# Compile to Java and Wrap into Kevoree
Let's consider a simple ThingML program made of two things, basically involving message to deal with a timer:

```
thing fragment TimerMsgs {
	// Start the Timer
	message timer_start(delay : Integer);
	// Cancel the Timer
	message timer_cancel();
	// Notification that the timer has expired
	message timer_timeout();
}
```

First, a timer:
```
thing fragment Timer includes TimerMsgs
{
	provided port timer
    {
		sends timer_timeout
		receives timer_start, timer_cancel
	}
}

//Java implementation of the timer
datatype JavaTimer
@java_type "java.util.Timer";

datatype JavaTimerTask
@java_type "java.util.TimerTask";

// Manage a set of software timers.
thing TimerJava includes Timer
@java_interface "org.thingml.timer.TimerObserver"
@thingml_maven_dep "org.thingml.utils"
{

    readonly property javaTimer : JavaTimer = 'new java.util.Timer()'
    property javaTimerTask : JavaTimerTask

    function onTimeout()@override "true"
    do
        timer!timer_timeout()
    end

    function cancel()
    do
      if(not (javaTimerTask == 'null'))
      do
        '' & javaTimerTask & '.cancel();'
        '' & javaTimerTask & ' = null;'
      end
      '' & javaTimer & '.purge();'
    end

    function start(delay : Integer)
    do
        cancel()
        javaTimerTask = 'new org.thingml.timer.ThingMLTimerTask(this)'
        '' & javaTimer & '.schedule(' & javaTimerTask & ', (long)' & delay & ');'
    end

    statechart SoftTimer init default {
        state default {
          internal start
            event m : timer?timer_start
            guard m.delay > 0
            action do
                start(m.delay)
            end

          internal cancel
            event m : timer?timer_cancel
            action cancel()
        }
    }
}
```

Second, a simple client:
```
thing fragment TimerClient includes TimerMsgs
{
	required port timer
    {
		receives timer_timeout
		sends timer_start, timer_cancel
	}

}

thing TimerClientJava includes TimerClient
{
    statechart Default init Tick {

        property counter : Integer = 0

        state Tick {
            on entry
            do
                timer!timer_start(1000)
            end


            transition tock -> Tick
            event timer?timer_timeout
            guard counter%2 == 0
            action do
                print("tick")
                print(counter)
                counter = counter + 1
            end

            internal event tick : timer?timer_timeout
            guard counter%2 == 1
            action do
                print("tock")
                print(counter)
                counter = counter + 1
                timer!timer_start(5000)
            end
        }

    }

}
```

We then need to define a configuration, specifying how to connect the timer and the client:
```
configuration TestTimerJava {
    instance timer : TimerJava
    instance client : TimerClientJava
    connector client.timer => timer.timer
}
```

This ThingML program can then be compiled (using the standalone editor) to Java. In the compiler Menu, select Java/JASM. This will generate the Java code, wrap it into a Maven project, compile it and run it. In the terminal/console, you should see:

```
tick
0
tock
1
tick
2
tock
3
```

Now, to wrap this program into Kevoree, just select, in the compiler menu, Java/Kevoree. This will generate a set of wrappers that exposes the ThingML components (things) as Kevoree components, and will update the pom.xml file to include the necessary Kevoree plugins. In addition, it will also generate a Kevscript file corresponding to the initial configuration of the system, as described in the ThingML configuration:
```
repo "http://repo1.maven.org/maven2"
repo "http://maven.thingml.org"

//include standard Kevoree libraries
include mvn:org.kevoree.library.java:org.kevoree.library.java.javaNode:release
include mvn:org.kevoree.library.java:org.kevoree.library.java.channels:release
include mvn:org.kevoree.library.java:org.kevoree.library.java.ws:release

//include external libraries that may be needed by ThingML components
include mvn:org.thingml:org.thingml.utils:snapshot

//include Kevoree wrappers of ThingML components
include mvn:org.thingml.generated:TestTimerJava:1.0-SNAPSHOT

//create a default Java node
add node0 : JavaNode
set node0.log = "false"
//create a default group to manage the node(s)
add sync : WSGroup
set sync.port/node0 = "9000"
attach node0 sync

//instantiate Kevoree/ThingML components
add node0.TimerClientJava_TestTimerJava_client : KTimerClientJava
add node0.TimerJava_TestTimerJava_timer : KTimerJava

//instantiate Kevoree channels and bind component
add channel_1324969411 : SyncBroadcast
bind node0.TimerClientJava_TestTimerJava_client.timerPort_out channel_1324969411
bind node0.TimerJava_TestTimerJava_timer.timerPort channel_1324969411
add channel_1324969411_re : SyncBroadcast
bind node0.TimerClientJava_TestTimerJava_client.timerPort channel_1324969411_re
bind node0.TimerJava_TestTimerJava_timer.timerPort_out channel_1324969411_re
start sync
start node0
```

After you recompile the project (using `mvn clean install`), you can open this KevScripts into the Kevoree editor and deploy it using Kevoree as a normal Java node.
