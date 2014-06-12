# The Annotation API

The Annotation API is made to provide a simple and flexible way to decorate your existing code to declare it as a `component`, `channel`, `node` or `group`.

#### Types
1.**Components**
New kind of Component are declared by placing a `@ComponentType` annotation on their implementation class.
2.**Channels**
The channels are in charge of the transport of messages and objects, from output to input ports. Each channel type has a different behavior (sync, async, parallel, sequential, first-answer, etc.) and is declared by putting a `@ChannelType` on its implementation class.
3.**Groups**
The groups are responsible for the dispatch and synchronization of the models between several nodes. Just as the channels, they can have different dispatch and synchronization policies for each type. They are declared by putting a `@GroupType` annotation on their implementation class.
4.**Nodes**
The nodes support the deployment of components or sub-nodes, so that the runtime always conforms to the last consistent model a node received. They are declared by putting a `@NodeType` annotation on their implementation class.

>Java
*************

```
@ComponentType
public class HelloProducerComponent{...}

@ChannelType
public class AsyncBroadcast implements ChannelDispatch {...}

@GroupType
public class WebSocketGroup {...}

@NodeType
@Library(name = "Java")
public class JavaNode implements ModelListener, org.kevoree.api.NodeType {...}
```
>Kotlin
*************

```
public ComponentType class HelloProducerComponent{...}

public ChannelType class AsyncBroadcast implements ChannelDispatch {...}

public GroupType class WebSocketGroup {...}

public NodeType class JavaNode implements ModelListener, org.kevoree.api.NodeType {...}
```

#### Input Ports - Provided Methods

If you are used to Message-Oriented approaches, you just have to put a `@Input` annotation on the method you want to expose as an input port. If you are more familiar with Service-Oriented approaches, you will have to put a `@Provided` annotation on  each method you want to expose/offer.
The port gets its name from the method name. The mapped methods have to declare a unique `Object`-typed parameter. In case this parameter is missing, the method will be called and any parameter from the caller will be dropped. In case the method has more than one parameter, an error will be triggered.
In Kevoree, we have mixed the Message and Service oriented approaches. To this end, each call on a port can declare an optional `Callback` method. Any value returned from an `Input` or a `Provided` method will be forwarded to the caller and passed as parameter to the callback method it declared.

>Java
*************

```Java
@Input
public void sayHelloTo(Object msg) {...}

@Provides
public Boolean getTemp() {...}
```

>Kotlin
*************

``` Kotlin
public Input void sayHelloTo(Object msg) {...}

public Provides Boolean getTemp() {...}	```

#### Output Ports - Required Methods

If you are used to Message-Oriented approaches, you just have to put a `@Output` annotation on a field of the class that will host the port. This field has to be typed as `Port` from the Kevoree API. If you are more familiar with Service-Oriented approaches, you will have to put a `@Required` annotation on  each method you want to use.
The port gets its name from the field name.
In Kevoree, we have mixed the Message and Service oriented approaches. To this end, each call on a port can declare an optional `Callback` method. This method is called as soon as the execution of the call is completed. The parameter of the callback is the value of the return of the `Input / Provided` port connected.

>Java
*************

> **Without callback**

```Java
@Output
private org.kevoree.api.Port helloProduced;

public void onHelloProduced(String greetingMessage) {
	helloProduced.send(greetingMessage);
}
```
> **With callback**

```Java
@Required
private org.kevoree.api.Port userDecision;

public boolean askUser(String questionMessage) {
	userDecision.call(greetingMessage, new Callback() {
		public void run(Object result) {
        	return (Boolean)result;
        }
    });
}
```

#### Parameters

Parameters are sometimes useful to adapt the behavior of a piece of code. These parameters can be used to set the delay of a timeout, a display name of a frame, the color of a frame, etc.
To declare a parameter, just declare a field in your class, and add to it the `@Param` annotation. The default value of a parameter has to be specified in the annotation as shown on the right.
<span class="warning-bloc"><span class="fa fa-exclamation-triangle fa-lg orange"></span> Kevoree only supports the `Param` annottaion on *Primitive* types and their boxing equivalent.</span>



>Java
*************

```Java
@Param
String name;

@Param (defaultValue = "2000")
int delay = 2000;
```

>Kotlin
*************

``` Kotlin
Param(defaultValue = "default") var name : String = "default" ;
```

#### Library

The Library annotation makes it possible for you to organize the components you create into virtual Libraries. It has nothing to do with the deployment, the location of the binaries or the behavior of your component. It can be whatever you want.
<span class="warning-bloc"><span class="fa fa-exclamation-triangle fa-lg orange"></span> The Library annotation must always be placed after the type declaration annotation (i.e.: ComponentType, ChannelType, etc.).</span>

>Java
*************

``` Java
@NodeType
@Library(name = "Java")
public class JavaNode implements ModelListener, org.kevoree.api.NodeType {...}
```
>Kotlin
*************

```kotlin
public ComponentType Library(name="Java") class HelloKotlin {...}
```



#### Kevoree services injection
Several services from the Kevoree runtime can be injected into a component, channel, group or node, on demand. To do so, just place a `KevoreeInject` annottaion on a variable typed by the servcie you need. The services available are:
**ModelService**
**BootstrapService**
**KevScriptService**
**Context**
**ChannelContext**

>Java
*************

``` Java
@KevoreeInject
ChannelContext channelContext;
```

>Kotlin
*************

```kotlin
KevoreeInject ChannelContext channelContext;
```


#### Life Cycle
In Kevoree, Components, Channels, Groups and Nodes have a Life Cycle.
Thus, the runtime must be able to  start, stop and update these elements when needed.
Depending on these elements' implementation, it may sometimes be required to perform some actions when stopping, starting or updating them.
Life Cycle annotations are here to allow you to specify the methods to call on start, stop or update.
There is no constraint on the method you select for these operations.
<span class="warning-bloc"><span class="fa fa-exclamation-triangle fa-lg orange"></span> Be cautious about what you do in these methods, because you can freeze the entire runtime if you create a deadlock !</span>
>Java
*************

``` Java
@Start
public void startComponent() {...}

@Stop
public void stopComponent() {...}

@Update
public void updateComponent() {...}
```
>Kotlin
*************

```kotlin
Start fun startComponent(){...}

Stop fun stopComponent(){...}

Update fun updateComponent(){...}
```
