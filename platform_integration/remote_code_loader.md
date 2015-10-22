# Remote code loader
## Introduction
A Kevoree model represents a set of Components, Nodes, Groups and Channels that can be connected together.

At some point the nodes have to load the Components, Groups fragments and Channels fragments from a shared code repository.

Once loaded in a node, a piece of code must be isolated from the rest of the application.

For example if a Node **"A"** have a dependency to a library **Z** in version **1.0.0** and have to load Component **"B"** with a dependency to the same library **Z** but in version **2.0.0**, the action of loading **"B"** in the context of **"A"** should not override **Z** in its version 2.0.0

## Existing implementations
### Java

**Repo**: [maven](https://maven.apache.org/)  
**Loader**: ClassLoader named [KCL](https://github.com/dukeboard/kevoree-classloading-framework)

### Javascript

**Repo**: [npm](https://www.npmjs.com/)  
**Loader**: Node.js module (CommonJS standard)

Code isolation is a structural feature of this platform because modules are loaded based on their full path location and versioning is handled by **npm**

### C&#35;

**Repo**: [Nuget](https://github.com/kevoree/kevoree-dotnet-nuget-loader)  
**Loader**:
The code isolation is based on <a href="https://msdn.microsoft.com/en-us/library/2bh4z9hs(v=vs.110).aspx">AppDomain</a> and the <a href="https://msdn.microsoft.com/en-us/library/dd460648(v=vs.110).aspx">MEF Framework</a>.  

The [Kevoree Dotnet Nuget Loader](https://github.com/kevoree/kevoree-dotnet-nuget-loader) is a component which combines Nuget, AppDomain and MEF. It take a Nuget name and version and return an isolated context containing the remote component code.

# Advices
This component can be pretty tricky to implement according to the default features of the targeted language.

You should implement it as soon as possible because it will impact the following code parts :
 * [Bootstrap](bootstrap.md)
 * Node
 * [Model generator](model_generator.md)
