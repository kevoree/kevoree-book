# Kevoree model
## Introduction
The meta model of kevoree is defined at https://github.com/dukeboard/kevoree/blob/master/kevoree-core/org.kevoree.model/metamodel/org.kevoree.mm
using [KMF](http://kevoree.org/kmf/) we are able to generate the corresponding model in Java and Javascript.

## Requirements
 * A model must be serializable and unserializable to/from a json structure. It is useful for the communication of models by the Channels or the publication of models by the [model generator](model_generator.md).
 * The model is shared by many components usually isolated from eachother. Its objects should have a technical solution to allow them to be shared easilly (serialization, proxification...)

## Strategies
### Adding a generator for the targeted platform
TODO

### Transpiling from an existing model
A real life scenario is the development of the C# platform.
No generator exists for this platform, but C# paradigms are very close from Java's one so we had been able to use [IKVM](http://www.ikvm.net/), a tool which is allows us to convert a jar to a dll.

The whole process is detailed in this page : https://github.com/kevoree/kevoree-dotnet-ikvm/wiki

From our experience, the generated dll is working really well be we had some hard time figuring out how to integrated it with the isolated context needed to load the component into a node.
