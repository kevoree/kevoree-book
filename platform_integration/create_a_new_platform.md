# Creating a new Kevoree platform
## Introduction
As you know Kevoree is a multiplatform distributed model tool.

Two platforms a currently maintained:
 * [Java](https://github.com/dukeboard/kevoree)
 * [Javascript](https://github.com/kevoree/kevoree-js)

One is currently in development:
 * [C#](https://github.com/kevoree/kevoree-dotnet)

Each of those platforms are based on the same concepts and are split in the same way.

In the rest of this chapter we will detail how to split an implentation of the Kevoree runtime. It aims to be useful if you want to implement Kevoree in another language (python, haskell, ruby, erlang, you name it) but will be based on our experience with Java, JavaScript and C#.

## Global architecture dependencies
TODO : Schema of dependencies between components

## Components
 * [Remote code loader](remote_code_loader.md) (How to load remote code in your runtime).
 * **Kevoree Model generation :** : Advices on how to quickly obtain a kevoree model code base
 * **Core :** TODO.
 * **Bootstrap :** TODO.
 * **Registry client :** TODO.
 * **Logger** : TODO - Define a few specifications.
 * **Model generator :** : TODO (model generation + registry publication ? // should be based on language's platform automation and industrialisation tools).
 * **Code generator :** TODO -> tool which takes a Type Definition and generate a project's base compatible with the definition.
 * **Kevoree's components :**
  * Component : TODO
  * Node : TODO
  * Group : TODO
  * Channel : TODO
