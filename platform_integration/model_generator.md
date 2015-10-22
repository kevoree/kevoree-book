# Model generator
## Introduction

In order to declare publicly a components you have to publish its Type Definition and
its DeployUnit to a registry, to do so you have to generate a model from your component.

 * Publication is done by calling a POST method, documented here : https://github.com/kevoree/kevoree-registry#push-model (using the [registry client](registry_client.md))
 * The registry's REST API expects to receive the published model formated in json. This is usually done by build fist a object structure using the [model](model.md) and then marshalling it in json.
 * Implementing a code generator can be done by static code analysis or reflection.


## Existing implementations
### Java
A maven plugin ([kevoree-maven-plugin](https://github.com/dukeboard/kevoree/tree/master/kevoree-tools/org.kevoree.tools.mavenplugin)) is charge of publishing collectively a component to a maven repository and to a kevoree registry.
The code analysis is done by reflection (mostly by annotations scanning).
### Javascript
TODO : npm & co.
### C&#35;
Their is no integrated tool to do all in once in c# yet.

The process is split in two steps. First you have to publish the package to a nuget registry.

Once it's done, a cli tool, [Kevoree Model Generator](https://github.com/kevoree/kevoree-dotnet-model-generator), is available to publish the package to a kevoree registry.

TODO
