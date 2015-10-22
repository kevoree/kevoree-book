# Kevoree model
## Introduction
The meta-model of Kevoree is defined  [here](https://github.com/dukeboard/kevoree/blob/master/kevoree-core/org.kevoree.model/metamodel/org.kevoree.mm)
using [KMF](http://kevoree.org/kmf/)'s modeling language.  


## Strategies
### Adding a generator for the targeted platform
You have two choices here:
 - create a KMF generator that targets your language
 - create a model from scratch in the target language

### Kevoree Model's JSON Schema
What matters in the end is that the target platform is able to (de)serialize Kevoree models from (and to) JSON strings.  
The JSON format must comply with [this JSON Schema]().

### Transpiling from an existing model
A real life scenario is the development of the C# platform.
No generator exists for this platform, but C# paradigms are very close from Java's one so we had been able to use [IKVM](http://www.ikvm.net/), a tool which is able to convert a jar to a dll (among other things).

The whole process is detailed in this page : https://github.com/kevoree/kevoree-dotnet-ikvm/wiki

From our experience, the generated dll is working really well but we had a hard time figuring out how to integrated it with the isolated contexts needed to load components into a node.
