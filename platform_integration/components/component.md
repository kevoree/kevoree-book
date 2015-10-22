# Component
## Description
A component is a piece of code which can tack data in input and produces data in ouput.

### Examples
 * Ticker : Emit a random value every N seconds.
 * ConsolePrinter : Print everything it receive.
 * ArduinoController : Can be used as a proxy to an [arduino device](https://www.arduino.cc/).

## Interface
A component interact with the rest of a kevoree system through its interface.
It is composed of different elements, usually described by annotated field and method (at least in our existing implementations in java, javascript/typescript and C#).

### Input
A field annotated with input will receive data from any channel connected to it.

### Output
A field annotated with output offer the ability to send data through channels connected to it.

### Start
The method annotated with Start will be called when an instance of the component need to be started.

### Stop
The method annotated with Stop will be called when an instance of the component need to be stopped.

### Update
The method annotated with Update will be called when an instance of the component need to be updated.

### Param
A field annotated with Param will be instantiated with a value provided by the model.

### KevoreeInject
A few interfaces to the external system are provided to the components by injection of interfaces instances.
The core will match every KevoreeInject annotated field and will look for a instance of its interface.

The provided interfaces are :
 * Logger : Offers a way to log messages. For more detail read the [Logger](../logger.md) page
 * Context : Provider accessors to the node node, the instance path and the instance name.
 * ModelService : Offers operators on the node's model. For example you can use it to publish a new model, which will be adapted by the core.


## Naming rules reminder
As defined in the [generalities](../generalities.md) part, every component must follow this name rule : kevoree-${platform}-comp-${componentName} (e.g kevoree-js-comp-ticker, kevoree-dotnet-comp-consoleprinter, kevoree-java-comp-arduino-controller).
