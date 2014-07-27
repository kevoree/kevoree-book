# Injected Services

#### Kevoree services injection
Several services from the Kevoree runtime can be injected into a component, channel, group or node, on demand. To do so, just place a `KevoreeInject` annotation on a variable typed by the servcie you need. The services available are:
- `ModelService`
- `BootstrapService`
- `KevScriptService`
- `Context`
- `ChannelContext`

#####*Java*
*************

``` Java
@KevoreeInject
ChannelContext channelContext;
```

#####*Kotlin*
*************

```kotlin
KevoreeInject ChannelContext channelContext;
```

The ModelService interface offers several methods to trigger model modification and by the way give an access to trigger adaptations.

#### Life Cycle
In Kevoree, Components, Channels, Groups and Nodes have a Life Cycle.
Thus, the runtime must be able to start, stop and update these elements when needed.
Depending on these elements' implementation, it may sometimes be required to perform some actions when stopping, starting or updating them.
Life Cycle annotations are here to allow you to specify the methods to call on start, stop or update.
There is no constraint on the method you select for these operations.
<span class="warning-bloc"><span class="fa fa-exclamation-triangle fa-lg orange"></span> Be cautious about what you do in these methods, because you can freeze the entire runtime if you create a deadlock !</span>
#####*Java*
*************

``` Java
@Start
public void startComponent() {...}

@Stop
public void stopComponent() {...}

@Update
public void updateComponent() {...}
```
#####*Kotlin*
*************

```kotlin
Start fun startComponent(){...}

Stop fun stopComponent(){...}

Update fun updateComponent(){...}
```

#### Model Listeners

Through injected services, Kevoree entities can register listener on model modification and so on all system update.
User has to implement the interface `ModelListener` and perform adaptatoin analysis directly into the callback method `modelUpdate`.

```java
@ComponentType
public UpdateListener implement ModelListener {
    @KevoreeInject
    ModelService modelService;

   modelService.registerModelListener(this);

   public void modelUpdate(event....){...}

}
```
