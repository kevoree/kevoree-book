# Cloud Management with Kevoree

Kevoree can be used as a Cloud management layer, simply by following this idea. If a node is a container, it can as well contains other nodes, which can then host components. In others words, simply by composing Nodes with can manage Cloud virtual infrastructures by mapping Kevoree nodes to virtual machines.

Again, everything is about manipulating model, KevScript is then the simplest way to dynamically manipulate infrastructures.

**Add nodes**
This allows to create a new virtual machine in another container. Here `infra0` is the container, in other words, one of the IaaS (infrastructure) nodes set. `vm0` is then a PaaS (platform) node, ready himself to host components.
```
add infra0.vm0 : JavaNode
```

**Remove nodes**
In the same manner, one can delete a node from his container.
```
remove infra0.vm0
```

**Move nodes**
The move instruction is a migration command. It allows to migrate a virtual machine to another container.
```
move infra0.vm0 infra1
```
