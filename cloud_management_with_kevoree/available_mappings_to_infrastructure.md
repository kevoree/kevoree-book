# Available mappings to infrastructures

Each Kevoree node types can refine the creation of child nodes. Each of them, offers several virtualization capabilities.

####JavaNode
This is the default implementation. Basically it creates a second process for each child node which runs in a separated virtual machine. This light virtualization layer protects for process interaction but offers no protection in term of network or disk.

####LXCNode
This Node type creates each child in a Linux container. This offers a light virtualization but isolates network and disk from each machine. This prevents network port collisition and allows to define CPU share time between child nodes.

####DockerIO
Similar to LXC node, but using docker project as a backend. It is the default implementation included in Boot2Kevoree

####KVMNode
soon...

####EC2Node
soon...


