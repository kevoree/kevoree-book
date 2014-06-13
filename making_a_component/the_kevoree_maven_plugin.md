# The Kevoree Maven Plugin

The Kevoree Maven plugin is used to extract the Component-Model from the annotations placed in your code, and store it into a Kevoree Model packed along with the compiled class files.
Also, for the ease of use, the Kevoree Maven plugin embeds a Kevoree runner. This runner launches a Kevoree runtime using a KevScript file. This file is supposed to be `src/main/resources/kevs/main.kevs` in the project. If otherwise, you can specify the location of the KevScript file you want to use in the configuration of the plugin.
You can also specify the name of the node you want to launch.

```
<plugin>
	<groupId>org.kevoree.tools</groupId>
	<artifactId>org.kevoree.tools.mavenplugin</artifactId>
	<version>${kevoree.version}</version>
	<executions>
		<execution>
			<goals>
				<goal>generate</goal>
			</goals>
		</execution>
	</executions>
	<configuration>
		<nodename>MyNode</nodename>
		<model>src/main/kevs/main.kevs</model>
	</configuration>
</plugin>
```

### Available actions

Mainly the Kevoree maven plugin is automatically execute @CompileTime in order to put additional informations in the JAR. *(Mainly model fragment of currently developed type definitions)*.

Additionally from this plugin user can execute directly the root kevScript file refered in the configuration using the following command:

> mvn kev:run

This will execute Kevoree directly in the maven environement.

