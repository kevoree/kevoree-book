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
public class JavaNode implements org.kevoree.api.NodeType {...}
```
>Kotlin
*************

```
public ComponentType class HelloProducerComponent{...}

public ChannelType class AsyncBroadcast implements ChannelDispatch {...}

public GroupType class WebSocketGroup {...}

public NodeType class JavaNode implements org.kevoree.api.NodeType {...}
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
public class JavaNode implements org.kevoree.api.NodeType {...}
```
>Kotlin
*************

```kotlin
public ComponentType Library(name="Java") class HelloKotlin {...}
```



