# Kevoree model
## Introduction
The meta-model of Kevoree is defined  [here](https://github.com/dukeboard/kevoree/blob/master/kevoree-core/org.kevoree.model/metamodel/org.kevoree.mm)
using [KMF](http://kevoree.org/kmf/)'s modeling language.  


## Requirements
 * A model must be serializable and unserializable to/from a JSON structure. It is useful for the communication of models by the Groups or the publication of models to a Kevoree registry.

## Strategies
### Adding a generator for the targeted platform
You have two choices here:
 - create a KMF generator that targets your language
 - create a model from scratch in the target language

### Kevoree Model's JSON Schema
What matters in the end is that the target platform is able to (de)serialize Kevoree models from (and to) JSON strings.  
The JSON format must comply with [this JSON Schema](/kevoree-schema.html).

### Transpiling from an existing model
A real life scenario is the development of the C# platform.
No generator exists for this platform, but C# paradigms are very close from Java's one so we had been able to use [IKVM](http://www.ikvm.net/), a tool to convert JARs to DLL.

The whole process is detailed [here](https://github.com/kevoree/kevoree-dotnet-ikvm/wiki).

From our experience, the generated DLL is working really well but we had a hard time figuring out how to integrate it with the isolated contexts needed to load components into a node.
