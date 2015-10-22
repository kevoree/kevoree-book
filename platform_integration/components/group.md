# Group
## Description
A group is a piece of code which synchronize a model between the nodes connected to it.
It is also the interface to load a living model into an external tool (e.g an editor).

### Examples
 * RemoteWSGroup : The nodes are connected to a shared WebSocket broker which broadcast every received messages.
 * WSGroup : A WSGroup have the same behaviour as a RemoveWSGroup but one of the group fragment is running the WebSocket broker.

## Interface
A group interact with the rest of a kevoree system through its interface.
It is composed of different elements, usually described by annotated field and method (at least in our existing implementations in java, javascript/typescript and C#).

### Start
The method annotated with Start will be called when an instance of the group need to be started.

### Stop
The method annotated with Stop will be called when an instance of the group need to be stopped.

### Update
The method annotated with Update will be called when an instance of the group need to be updated.

### Param
A field annotated with Param will be instantiated with a value provided by the model.

### KevoreeInject
A few interfaces to the external system are provided to the groups by injection of interfaces instances.
The core will match every KevoreeInject annotated field and will look for a instance of its interface.

The provided interfaces are :
 * Logger : Offers a way to log messages. For more detail read the [Logger](../logger.md) page
 * Context : Provider accessors to the node node, the instance path and the instance name.
 * ModelService : Offers operators on the node's model. For example you can use it to publish a new model, which will be adapted by the core.


## Naming rules reminder
As defined in the [generalities](../generalities.md) part, every group must follow this name rule : kevoree-${platform}-group-${groupName} (e.g kevoree-js-group-ws, kevoree-dotnet-group-remotews).
