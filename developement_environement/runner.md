# Runner

#### Edit Kevoree script

We provide also two KevScript editor. One is a textual editor with completion. The second one is a graphical editor. To work with the graphical editor, the component definition must exist in your maven repository (do not forget to do a mvn install to push the definition in the repository. Do not also forget to include your maven component artefact (include mvn:org.kevoree.project:HelloWorlKevoree:latest) to be able to use it (add node0.hello : HelloWorldComponent)

![KevoreeProjectCreated](https://raw.github.com/kevoree/kevoree-eclipse-plugin/master/KevoreeEclipseUpdateSite/web/KevoreeKevscriptEditors.png)

#### Run the Kevoree Script

Now you can easily build a launcher for your kevscript.

1. Select the project (do not forget the * to get all the available project).
2. Select the kevscript to run
3. Select the node name to start

![KevoreeProjectCreated](https://raw.github.com/kevoree/kevoree-eclipse-plugin/master/KevoreeEclipseUpdateSite/web/KevoreeCreateRunner.png)

You will get the log in the console

![KevoreeProjectCreated](https://raw.github.com/kevoree/kevoree-eclipse-plugin/master/KevoreeEclipseUpdateSite/web/KevoreeCRunner.png)
