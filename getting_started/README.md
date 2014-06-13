# Getting started

### Kevoree and Models
Kevoree makes an intensive use of Models. Physically, models are structured files in JSON or XMI format, used to carry the description of a component, an entire library, the location where the binary files can be found and/or the description of a software system to deploy with all the component instances and their connections.

### The Kevoree Editor

The Kevoree Editor provides a model authoring tool specialized for Kevoree Models.
It offers a Graphical Editor in which modifications on models are made principally using drag&drop mechanisms.
It also embeds a Kevoree Scripting engine developed to simplify the modifications.

1. Standalone Editor

> [Download Kevoree Editor](http://oss.sonatype.org/service/local/artifact/maven/redirect?r=public&g=org.kevoree.tools&a=org.kevoree.tools.ui.editor&v=RELEASE)

2. Web Editor

> http://editor.kevoree.org

it also embedded in Boot2Kevoree version

> boot2kevoree editor

and in Kevoree GUI distribution (just right clic on top right, and it will magically deploy the editor and open it on your browser :-) )

![KevoreeGuiEditor](gui_editor.png)

### Kevoree Distributions
Kevoree offers several runtime environments. Among others, the Java runtime of Kevoree wraps a Java Virtual Machine with all the necessary features to handle the deployment of models received from editors or local components.

* Use Kevoree for Cloud developement or without installing anything on your machine :

> [Donwload Boot2Kevoree client](https://github.com/kevoree/boot2kevoree-cli/releases) (requirement : virtualbox) and simply start a Kevoree mini cloud using boot2kevoree-cli start

> [Donwload Boot2Kevoree iso](https://github.com/kevoree/boot2kevoree/releases) and use it in virtual box for instance.

* Use Kevoree for test purpose, go for Runtime GUI version :

> [Download Java Runtime w. GUI](http://oss.sonatype.org/service/local/artifact/maven/redirect?r=public&g=org.kevoree.platform&a=org.kevoree.platform.standalone.gui&v=RELEASE)

* Use Kevoree for command line usage, go for standalone JAR version :

> [Download Java Standalone](http://oss.sonatype.org/service/local/artifact/maven/redirect?r=public&g=org.kevoree.platform&a=org.kevoree.platform.standalone.gui.prompt&v=RELEASE)

* Use Kevoree as a Service for production deployment, go for the DEB version (for Ubuntu like server, or Raspian OS) with watchdog :

> [Download Java Watchdog](http://oss.sonatype.org/service/local/artifact/maven/redirect?r=public&g=org.kevoree.watchdog&a=org.kevoree.watchdog&v=RELEASE)


### Usage

For all Kevoree Java application you can start them by using

> java -jar kevoreeRuntime.jar (replace kevoreeRuntime by the right name of the file)

or more simply by double clic.

To run boot2kevoree (virtualbox need to be installed http://www.virtualbox.org/), simply copy the file in your path then:

> boot2kevoree init

This will download the .iso file and init the virtualmachine

> boot2kevoree up

This will start the boot2kevoree virtual machine

> boot2kevoree editor

will run the editor

> boot2kevoree ssh

will log into the virtual machine (user:kevoree, password:tcuser)

> boot2kevoree gui

will run the default Kevoree Cloud GUI, this will allow you to add/remove virtual machine

![KevoreeCloudGUI](cloud_gui.png)
