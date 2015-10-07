# Remote code loader
## Introduction
A Kevoree model represents an ensemble of Components, Nodes, Groups and Channels linked.

At some point the nodes have to load the Components, Groups fragments and Channels fragments from a shared code repository.

Once loaded in a node, a piece of code should note interact with the rest of the application.

For example if a Node **"A"** have a dependency to a library **Z** in version **1.0.0** and have to load Component **"B"** with a dependency to the same library **Z** but in version **2.0.0**, the action of loading "B" in the context of "A" should not override Z this the version 2.0.0.

Each component must be **isolated** from the rest of the node.

## Existing implementations
### Java
The java implementation is based on [maven](https://maven.apache.org/) repositories implementation for the remote code loader part.

The code isolation is base on a custom ClassLoader named [KCL](https://github.com/dukeboard/kevoree-classloading-framework).
### Javascript
The remote code loader is based on npm, the official project and dependencies manager on node. Code isolation is a structural feature of this platform.

### C&#35;
The remote code loader is [Nuget](https://github.com/kevoree/kevoree-dotnet-nuget-loader).

The code isolation is based on <a href="https://msdn.microsoft.com/en-us/library/2bh4z9hs(v=vs.110).aspx">AppDomain</a> and the <a href="https://msdn.microsoft.com/en-us/library/dd460648(v=vs.110).aspx">MEF Framework</a>.

The [Kevoree Dotnet Nuget Loader](https://github.com/kevoree/kevoree-dotnet-nuget-loader) is a component which combines Nuget, AppDomain and MEF. It take a Nuget name and version and return an isolated context containing the remote component code.

# Advices
This component can be pretty tricky to implement depending of the default features of the targeted language.

You should implement it as soon as possible because it will impact the following code parts :
 * Bootstrap
 * Node
 * Model generator
