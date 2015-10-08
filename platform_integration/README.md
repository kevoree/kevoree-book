# Creating a new Kevoree platform
## Introduction
As you know Kevoree is a multiplatform distributed model tool.

Two platforms a currently maintained :
 * [Java](https://github.com/dukeboard/kevoree)
 * [Javascript](https://github.com/kevoree/kevoree-js)

One is currently in development :
 * [C#](https://github.com/kevoree/kevoree-dotnet)

Each of those platforms are based on the same concepts and are split in the same way.

In the rest of this chapter we will detail how to split an implentation of the Kevoree runtime. It aim to be usefull if you want to write kevoree in another language (python, haskell, ruby, erlang, you name it) but will be based on our experience with Java, Javascript and C#.

## Global architecture dependencies
TODO : Drawing a schema of dependencies between components

## Components
 * [Remote code loader](remote_code_loader.md) : (How to load remote code in your runtime).
 * [Kevoree Model](model.md) : How to port Kevoree's data model to your platform ?
 * [Kevoree Model generation](model_generator.md) : Advices on how to quickly obtain a kevoree model code base
 * **Core :** TODO.
 * [Registry client](registry_client.md) A simple client for the registry.
 * **Logger** : TODO - Define a few specifications.
 * **Code generator :** TODO -> tool which takes a Type Definition and generate a project's base compatible with the definition.
 * **KevScript tool** : reading kevscript, generating valid kevscript...
 * [Bootstrap](bootstrap.md) A Bootstrap is a runtime tool dedicated to the startup of a node instance.
 * **Kevoree's components :**
  * Component : TODO
  * Node : TODO
  * Group : TODO
  * Channel : TODO
 * **Usefull development tools :**
  * **Local kevoree registry :**
    * Java project : https://github.com/kevoree/kevoree-registry
    * Docker container : https://github.com/kevoree/docker-image-registry-replica (clone the [official registry](http://registry.kevoree.org) by default)
  * **Local kevoree editor :**
    * Node project : https://github.com/kevoree/kevoree-web-editor
    * Docker container : https://github.com/kevoree/docker-image-editor
