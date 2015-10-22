# Channel
## Description
A channel is a piece of code which forward messages from components with an output port connect to it to components with an input port connected to it.

### Examples
 * RemoteWSChan : The components are connected to a shared WebSocket broker which broadcast every received messages.
 * WSChan : A WSChan have the same behaviour as a RemoteWSChan but one of the channel fragment is running the WebSocket broker.

## Interface
A channel interact with the rest of a kevoree system through its interface.
It is composed of different elements, usually described by annotated field and method (at least in our existing implementations in java, javascript/typescript and C#).

### Start
The method annotated with Start will be called when an instance of the channel need to be started.

### Stop
The method annotated with Stop will be called when an instance of the channel need to be stopped.

### Update
The method annotated with Update will be called when an instance of the channel need to be updated.

### Param
A field annotated with Param will be instantiated with a value provided by the model.

### KevoreeInject
A few interfaces to the external system are provided to the channels by injection of interfaces instances.
The core will match every KevoreeInject annotated field and will look for a instance of its interface.

The provided interfaces are :
 * Logger : Offers a way to log messages. For more detail read the [Logger](../logger.md) page
 * Context : Provider accessors to the node node, the instance path and the instance name.
 * ModelService : Offers operators on the node's model. For example you can use it to publish a new model, which will be adapted by the core.
 * ChannelContext : offer an access to the input and output of connected components.


## Naming rules reminder
As defined in the [generalities](../generalities.md) part, every channel must follow this name rule : kevoree-${platform}-chan-${channelName} (e.g kevoree-js-chan-ws, kevoree-dotnet-chan-remotews).
