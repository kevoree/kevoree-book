# Node
## Description
A node is a component which receive a set of traces (i.e. a list of differencies between the current model and the targeted model) and will adapt its state to match it with the targeted model.

For now a single implementation of Node is done by language. Mostly because is it one of the most complex part of a Kevoree implementation.

## Interface
A node interact with the rest of a kevoree system through its interface.
It is composed of different elements, usually described by annotated field and method (at least in our existing implementations in java, javascript/typescript and C#).

### Start
The method annotated with Start will be called when an instance of the node need to be started.

### Stop
The method annotated with Stop will be called when an instance of the node need to be stopped.

### Update
The method annotated with Update will be called when an instance of the node need to be updated.

### Param
A field annotated with Param will be instantiated with a value provided by the model.

### KevoreeInject
A few interfaces to the external system are provided to the components by injection of interfaces instances.
The core will match every KevoreeInject annotated field and will look for a instance of its interface.

The provided interfaces are :
 * Logger : Offers a way to log messages. For more detail read the [Logger](../logger.md) page
 * Context : Provider accessors to the node node, the instance path and the instance name.
 * ModelService : Offers operators on the node's model. For example you can use it to publish a new model, which will be adapted by the core.
