# Management Commands

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

**Network**
Specifies the IP address on which a node is reachable. In addition give as last parameter an interface face, this must be unique.
```
network node0.ip.eth0 192.168.0.1
```
