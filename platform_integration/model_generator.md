# Model generator
## Introduction

In order to declare publicly a component you have to publish its TypeDefinition and
its DeployUnit to a registry. To do so you have to generate a model for your component.

 * Publication is done by calling a POST method, documented here : https://github.com/kevoree/kevoree-registry#push-model (using the [registry client](registry_client.md))
 * The registry's REST API expects to receive the published model formated in JSON. This is usually done by building an object structure using the [model](model.md) and then marshaling it in JSON.
 * Implementing a model generator can be done by static code analysis or reflection.


## Existing implementations
### Java
A maven plugin ([kevoree-maven-plugin](https://github.com/dukeboard/kevoree/tree/master/kevoree-tools/org.kevoree.tools.mavenplugin)) is in charge of publishing collectively a component to a maven repository and to a Kevoree registry.  
The code analysis is done by reflection (mostly by annotations scanning).

### Javascript
For the JavaScript platform, the model generation is made by a [Grunt task](https://www.npmjs.com/package/grunt-kevoree-genmodel) that will reflect on the Node.js module code. The reflection is mostly done by reading the provided properties of the class. The properties that have a meaning in Kevoree are prefixed using **naming conventions**:
 - **dic_XXX**: for Dictionary Attribute
 - **in_XXX**: for input port
 - **out_XXX**: for output port

By reading this, the JavaScript model generator is able to generate the appropriate TypeDefinition and then publish it on the Kevoree registry, on demand, using another [Grunt task](https://www.npmjs.com/package/grunt-kevoree-registry).

### C&#35;
Their is no integrated tool to do all in once in c# yet.

The process is split in two steps:
 1. publish the package to a nuget registry
 2. use the C# [Kevoree Model Generator](https://github.com/kevoree/kevoree-dotnet-model-generator) to publish the package to a Kevoree registry
