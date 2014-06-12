# Getting started

### Kevoree and Models
Kevoree makes an intensive use of Models. Physically, models are structured files in JSON or XMI format, used to carry the description of a component, an entire library, the location where the binary files can be found and/or the description of a software system to deploy with all the component instances and their connections.

### The Kevoree Editor

The Kevoree Editor provides a model authoring tool specialized for Kevoree Models.
It offers a Graphical Editor in which modifications on models are made principally using drag&drop mechanisms.
It also embeds a Kevoree Scripting engine developed to simplify the modifications.

[Download Kevoree Editor](http://oss.sonatype.org/service/local/artifact/maven/redirect?r=public&g=org.kevoree.tools&a=org.kevoree.tools.ui.editor&v=RELEASE)

### Kevoree Runtimes
Kevoree offers several runtime environments. Among others, the Java runtime of Kevoree wraps a Java Virtual Machine with all the necessary features to handle the deployment of models received from editors or local components.

* Use Kevoree for test purpose, go for Runtime GUI version :

[Download Java Runtime w. GUI](http://oss.sonatype.org/service/local/artifact/maven/redirect?r=public&g=org.kevoree.platform&a=org.kevoree.platform.standalone.gui&v=RELEASE)

* Use Kevoree for command line usage, go for standalone JAR version :

[Download Java Standalone](http://oss.sonatype.org/service/local/artifact/maven/redirect?r=public&g=org.kevoree.platform&a=org.kevoree.platform.standalone.gui.prompt&v=RELEASE)

* Use Kevoree as a Service for production deployment, go for the DEB version (for Ubuntu like server, or Raspian OS) with watchdog :

[Download Java Watchdog](http://oss.sonatype.org/service/local/artifact/maven/redirect?r=public&g=org.kevoree.watchdog&a=org.kevoree.watchdog&v=RELEASE)
