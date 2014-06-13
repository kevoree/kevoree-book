# KevScript Commands

**Comments**
If you want to comment a line in your KevScript, here you go.
```
// this is a comment
// comments allow any character ! \ù%*é=^``~&°.:!§,?/#çà][-|
```

**Namespace**
A namespace allows to group several elements under a unique name, in order to simplify the manipulation on these elements. For instance, you can declare a namespace to which you add several nodes, to be able to write their connection to the same synchronization group as presented on the right.
Elements are added in namespaces using the `attach` command, they can be removed from the namespace using `detach`. A namespace can be completely removed using the `remove` command.

```
namespace space42
attach node0, node1 space42
attach space42 sync
detach node1 space42
remove space42
```


**Repository**
Adds a repository location for the resolution of binaries.
```
repo org.sonatype.org/foo/bar?a=b&c=d
repo http://oss.sonatype.org/content/repositories/releases
```

**Include**
Imports a library of types in the model, makes the Types available.
A fixed version number enforce the use of a specific version of library that will never change.
A `SNAPSHOT` version will always get the last version of the library, in snapshot mode.
A `RELEASE` version tag indicates that the version has to be updated to the latests release of the library.
A `LATEST` version tag (the default) looks for the latest version of the library, regarless of its type (release or snapshot) based on the build timestamp.
```
include mvn:org.kevoree.library.java:org.kevoree.library.java.javaNode:3.0.0
include mvn:org.kevoree.library.java:org.kevoree.library.java.javaNode:3.0.0-SNAPSHOT
include mvn:org.kevoree.library.java:org.kevoree.library.java.javaNode:RELEASE
include mvn:org.kevoree.library.java:org.kevoree.library.java.javaNode:LATEST
```

**Add**
Adds a new instance of `Component`, `Node`, `Channel` or `Group`.
You can add several elements of the same type, at the same time, by separating the instances' names with a `,`.
When the element you add is a component instance, you `MUST` specify the node that will host this instance, using a dotted notation (i.e.: node0.instance0 : MyComponentType).
```
add node0, node1 : JavaNode
add sync : WebSocketGroup/0.0.2-SNAPSHOT
add node0.comp0 : ToyConsole
add node0.comp1, node0.comp2 : ToyDisplay
add chan0 : DelayBufferedChannel
```

**Remove**
Removes elements from the model.
```
remove node0
remove sync
remove chan0
```

**Move**
Moves one or several instances to another node. Instances can be of type `NodeType` or `ComponentType`. The last parameter of the command is always the destination node.
```
move node0.comp0 node1
move *.* node0 //moves all components of all nodes, to node0
move node0.comp0, node0.comp1 node1
```

**Set**
Used to set parameters of instances.
Some parameters are `fragment dependent`. In this case, a property can have a different value on each node howting a fragment (it can be the case for Groups and Channels). In this case, the property is set using a `<element>.<property>/<node> = "<value>"` notation.
```
set node0.comp0.foo = "bar"
set node0.*.baz = 'potato' //sets the property baz of all components on node0
set sync.forcePush = "false"
set sync.port/node0 = '8000'
```

**Bind**
Binds the port, or several ports, of a component instance to several channel instances.
```
bind node0.base.output chan0
bind node0.base.input chan0
```

**Unbind**
Disconnects the port of a component from a channel.
```
unbind node0.base.input chan0
```

**Attach**
The last parameter of this command can be an instance of `group`or a `namespace`.
If the last parameter is a namespace, the list of parameters can be whatever you want. If the last parameter is a group, the elements should be nodes or namespaces.
```
attach node0 sync
attach node1, node2 sync
attach * sync
attach * space42
```

**Detach**
Disconnects one or several node instances from a synchronization group. The group is always at the last position in the command.
```
detach node0 sync2
```

**Network**
Specifies the IP address on which a node is reachable. In addition give as last parameter an interface face, this must be unique.
```
network node0.ip.eth0 192.168.0.1
```
