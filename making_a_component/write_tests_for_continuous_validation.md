# Write tests for continuous validation

Kevoree framework offers a JUnit extention to integrate behavioral testing of components, channels, groups and nodeTypes before their deployment. In details, this framework allows you to launch a KevoreeRuntime, instanciate a model using the element to validate, perform some adaptations and write assertions on the console result. In order to use it, add the following dependency as test scope to your project. Several nodes can be started and monitored to evaluate the output stream and traces to early detect regressions.

```
        <dependency>
            <groupId>org.kevoree.tools</groupId>
            <artifactId>org.kevoree.tools.test</artifactId>
            <version>${kevoree.version}</version>
            <scope>test</scope>
        </dependency>
```

Then add in `src/test/java` a new class file ending with a name Test.
As any JUnit test, each method with a `@Test` annotation is a unit test.
In addition to traditionnal assert methods, Kevoree Framework offers the following:

Start a platform using a name and a bootfile, bootfile can be in resources folder or absolute path.

`bootstrap("node0", "boot.kevs");`

Waits until the output of the node0 displays a line "Bootstrap complete". This output is expect within 10000 milliseconds.

`waitLog("node0", "node0/Bootstrap completed", 10000);`

Waits the completion of the execution of the kevScript on the node0

`exec("node0", "set child1.started = \"false\"");`

Waits the completion of the deployement of the `model` in node0

`deploy("node0", model);`

Gets the currentModel of the platform node0

`getCurrentModel("node0");`

Destroys the platform node0

`shutdown("node0");`

Each method throw exception in case of errors, so no need to encapsulate them in a assert method, JUnit will grab the errors. Finally all platforms are automacally cleaned after test execution. So now you have everything to write a complete exemple to test the child management of JavaNode.

```java
public class SubChildrenTest extends KevoreeTestCase {
    @Test
    public void startupChildTest() throws Exception {
        bootstrap("node0", "oneChild.kevs");
        waitLog("node0", "node0/child1/* INFO: Bootstrap completed", 10000);
        exec("node0", "set child1.started = \"false\"");
        assert (getCurrentModel("node0").findNodesByID("child1").getStarted() == false);
        waitLog("node0", "node0/* INFO: Stopping nodes[child1]", 5000);
        exec("node0", "set child1.started = \"true\"");
        assert (getCurrentModel("node0").findNodesByID("child1").getStarted() == true);
        waitLog("node0", "node0/child1/* INFO: Bootstrap completed", 10000);
    }
}
```
