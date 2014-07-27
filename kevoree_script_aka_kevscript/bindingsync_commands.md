# Binding/Sync Commands

After creation, Kevoree entities has to be binded to each others in order to exchange message or models.
`Bind` and `Unbind` commands allow to connect *components* to *channels* and `Attach` and `Detach` allow to create a subscription of a *node* to a *group*.

####Bind
Binds the port, or several ports, of a component instance to several channel instances.
```
bind node0.base.output chan0
bind node0.base.input chan0
```

####Unbind
Disconnects the port of a component from a channel.
```
unbind node0.base.input chan0
```

####Attach
The last parameter of this command can be an instance of `group`or a `namespace`.
If the last parameter is a namespace, the list of parameters can be whatever you want. If the last parameter is a group, the elements should be nodes or namespaces.
```
attach node0 sync
attach node1, node2 sync
attach * sync
attach * space42
```

####Detach
Disconnects one or several node instances from a synchronization group. The group is always at the last position in the command.
```
detach node0 sync2
```

