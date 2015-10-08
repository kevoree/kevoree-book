# Kevoree model
## Introduction
The metal model of kevoree is defined at https://github.com/dukeboard/kevoree/blob/master/kevoree-core/org.kevoree.model/metamodel/org.kevoree.mm
using [KMF](http://kevoree.org/kmf/) we are able to generate the corresponding model in Java and Javascript.

## Strategies
### Adding a generator for the targeted platform
TODO

### Transpiling from an existing model
A real life scenario is the development of the C# platform.
No generator exists for this platform, but C# paradigms are very close from Java's one so we had been able to use [IKVM](http://www.ikvm.net/), a tool which is able to convert a jar to a dll (among other things).

The whole process is details in this page : https://github.com/kevoree/kevoree-dotnet-ikvm/wiki

From our experience, the generated dll is working really well be we had some hard time figuring out how to integrated it with the isolated context needed to load the component into a node.
