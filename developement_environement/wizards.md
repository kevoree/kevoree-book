# Wizards

#### Create Kevoree Project

When it is installed, you can create a new Kevoree Project. (`File -> New Project -> Kevoree -> New Kevoree Project`)

![KevoreeProjectCreated](https://raw.github.com/kevoree/kevoree-eclipse-plugin/master/KevoreeEclipseUpdateSite/web/KevoreeCreateProject.png)

Next you must set the Project Name

![KevoreeProjectCreated](https://raw.github.com/kevoree/kevoree-eclipse-plugin/master/KevoreeEclipseUpdateSite/web/KevoreeCreateProjectName.png)

Finally,  you get a project with three natures, (Java, Maven and Kevoree). The POM is automatically created

![KevoreeProjectCreated](https://raw.github.com/kevoree/kevoree-eclipse-plugin/master/KevoreeEclipseUpdateSite/web/KevoreeProjectCreated.png)

#### Add Kevoree Entity

Now you can create Kevoree entities (components, channels, groups, kevscripts, ...)  (`File -> New -> Kevoree -> ...`). we provide templates for Java and Xtend programming languages. (C++, C, Scala, Kotlin, should arrive soon).

![KevoreeProjectCreated](https://raw.github.com/kevoree/kevoree-eclipse-plugin/master/KevoreeEclipseUpdateSite/web/KevoreeCreateKevoreeEntity.png)

If you select a new Java Component, you must provide a Java package and a Name for your component.

![KevoreeProjectCreated](https://raw.github.com/kevoree/kevoree-eclipse-plugin/master/KevoreeEclipseUpdateSite/web/KevoreeCreateComponent.png)

 You will automatically get the following Java class.

![KevoreeProjectCreated](https://raw.github.com/kevoree/kevoree-eclipse-plugin/master/KevoreeEclipseUpdateSite/web/KevoreeComponentCreated.png)


#### Builder, preferences page

We also provide a specific builder that automatically generate the model when the project changed.

![KevoreeProjectCreated](https://raw.github.com/kevoree/kevoree-eclipse-plugin/master/KevoreeEclipseUpdateSite/web/KevoreeEclipseBuilder.png)

We also create a preference page for Kevoree to set the Kevoree version you want to use. It is only for the plugin (builder, runner, ...) . The Kevoree version you use for a specific project is set within the pom.xml)

![KevoreeProjectCreated](https://raw.github.com/kevoree/kevoree-eclipse-plugin/master/KevoreeEclipseUpdateSite/web/KevoreeEclipsePreference.png)

#### Import a Kevoree project

If you have to import an existing Kevoree project, you can just import it as an existing maven project and add the Kevoree Nature (right click on the project, `configure -> add Kevoree Nature`)
