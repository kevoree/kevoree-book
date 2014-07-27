# Model Edition

#### Add TypeDefinition to your model
To add TypeDefinition to your model you have multiple choices:

 - Load/Merge a model from a JSON file or a remote platform
 - Merge some Kevoree Std Libraries
 - Merge libraries from your own repositories
 - Add `include` statements to the KevScript editor and run it

Upon TypeDefinition addition, you will see the left panel being populated with items:

![KWE Tdefs list](http://hosta.braindead.fr/raw/5399967d1a9879c239a1a224)

This list has been created using the KevScript method with the following script:
```kevs
include npm:kevoree-node-javascript:latest
include npm:kevoree-group-websocket:latest
include mvn:org.kevoree.library.java:org.kevoree.library.java.javaNode:latest
include mvn:org.kevoree.library.java:org.kevoree.library.java.ws:latest
```

#### Add instances to your model
To add instances to your model, you have multiple choices:

 - drag'n'drop an item from the TypeDefinition list (left panel) to the model editor canvas (center)
 - add `add` statements to the KevScript editor and run it

By doing so, KWE will create an instance of the selected TypeDefinition (graphical method: using its latest available version, kevscript method: using the version you have specified).

Using the previous KevScript example (for TypeDefinition), we could do:
```kevs
include npm:kevoree-node-javascript:latest
include npm:kevoree-group-websocket:latest
include mvn:org.kevoree.library.java:org.kevoree.library.java.javaNode:latest
include mvn:org.kevoree.library.java:org.kevoree.library.java.ws:latest

add node0 : JavascriptNode
add node1 : JavaNode
```
We have added two `add` statements, one for `node0 : Javascript` and one for `node1 : JavaNode`. This will result in the addition of two nodes in the model editor canvas:

![KWE add instances](http://hosta.braindead.fr/raw/539998931a9879c239a1a225)
