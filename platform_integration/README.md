# Creating a new Kevoree platform
## Introduction
As you know Kevoree is a multiplatform distributed model tool.

Two platforms are currently maintained :
 * [Java](https://github.com/dukeboard/kevoree)
 * [Javascript](https://github.com/kevoree/kevoree-js)

One is currently in development :
 * [C#](https://github.com/kevoree/kevoree-dotnet)

Each of those platforms are based on the same concepts and are split in the same way.

In the rest of this chapter we will detail the architecture of an implentation of the Kevoree runtime. It aims to be useful if you want to write Kevoree in another language (python, haskell, ruby, erlang, you name it) but will be based on our experience with Java, JavaScript and C#.

## Global architecture dependencies
TODO : Drawing a schema of dependencies between components

## Components
 * **[Generalities](generalities.md)**: A few cross platform advices
 * **[Kevoree Model](model.md)**: How to port Kevoree's data model to your platform
 * **[Remote code loader](remote_code_loader.md)**: How to load remote code in your runtime
 * **[Kevoree Model generation](model_generator.md)**: How to quickly obtain a kevoree model code base
 * **[Logger](logger.md)**: Specifications of the logging system.
 * **[Core](core.md)**: The Model@Runtime conductor
 * **[Generate instances of the Kevoree Metamodel](model_generator.md)**: How to quickly obtain a kevoree model code base
 * **[Registry client](registry_client.md)**: A simple REST client for the registry
 * **[Code generator](code_generator.md)**: How to generate a Component project from a Type Definition.
 * **[KevScript tool](kevscript.md)**: Reading kevscript, generating valid kevscript...
 * **[Runtime](runtime.md)**: A Bootstrap is a runtime tool dedicated to the startup of a node instance
 * **Kevoree's components**:
 <!---
Should we define a strict way to implement this (using annotation...) or just explaining that it is necessary to implement and document something powerful enought to express everything allowed by the model ?
 -->
    * **[Component](components/component.md)** : Component development guide
    * **[Node](components/node.md)** : Node development guide
    * **[Group](components/group.md)** : Group development guide
    * **[Channel](components/channel.md)** : Channel development guide
 * **Useful development tools**:
  * **Local kevoree registry**:
    * Java project : https://github.com/kevoree/kevoree-registry
    * Docker container : https://github.com/kevoree/docker-image-registry-replica (clone the [official registry](http://registry.kevoree.org) by default)
  * **Local kevoree editor**:
    * Node project : https://github.com/kevoree/kevoree-web-editor
    * Docker container : https://github.com/kevoree/docker-image-editor
