# Component
## Description
A component is a piece of code which can tack datas in input and produces datas in ouput.

### Examples
 * Ticker : Emit a random value every N seconds.
 * ConsolePrinter : Print everything it receive.
 * ArduinoController : Can be used as a proxy to an [arduino device](https://www.arduino.cc/).

## Interface
A component interfact with the rest of a kevoree system through its interface.
It is composed of different elements, usually described by annotated field and method (at least in our existings implementations in java, javascript/typescript and C#).

### Input
A field annotated with input will receive datas from any channel connected to it.

### Output
A field annotated with output offer the ability to send data through channels connected to it.

### Start
The method annotated with Start will be called when an instance of the component need to be started.

### Stop
The method annotated with Stop will be called when an instance of the component need to be stopped.

### Update
The method annotated with Update will be called when an instance of the component need to be updated.

### KevoreeInject



## Naming rules reminder
As defined in the [generalities](../generalities.md) part, every component must follow this name rule : kevoree-${platform}-comp-${componentName} (e.g kevoree-js-comp-ticker, kevoree-dotnet-comp-consoleprinter, kevoree-java-comp-arduino-controller).
