# Kevoree Runtime options

The Kevoree runtime platform is runnable as standard Java application. In other words, `java -jar KevoreeRuntime.jar` or just double click on the JAR file if your operating system is well configured. In addition two system options are available:

* `node.name`: associates a node name with the runtime
* `node.bootstrap`: gives an initial bootstrap model (.json,.kev.kevs accepted)
* `o` or `offline`: puts Kevoree in offline mode

> Remember, bootstrap options must be before the `-jar` option.
