# Core
## What is it?
The **Core** is the *director* of a Kevoree runtime:
 - **it is in charge of a node** (Kevoree NodeType)
 - **it has to execute adaptations on deployments** (model@run.time)
 - **keeps track of model changes**

### Bootstrap
The first step of the core is to **bootstrap** the runtime. To do so, the core is in charge
of creating the node instance defined with a **unique** name at the start of the Core.  
In order to know which NodeType to instantiate and with what properties, the core must have a model containing those data.  
This model is known as the **bootstrap model**. Using this model the core will be able to
create a new ContainerNode instance and keep a reference to it in order to ask that particular node *how* to do runtime adaptations on deployment phases.

### Deployment phase
Using pseudo-code, the deployment algorithm (model@run.time) looks like this:

```go
fun deployNewModel(newModel: KevModel) {
    // check the validity of the new model
    if (isValid(newModel)) {
        // compare new model with current model
        val compareResult: AdaptationModel = node.compare(currentModel, newModel);
        // execute a list of command to adapt the current system
        // according to the new model
        if (compareResult.execute()) {
            // keep track of current model (history)
            saveModel(currentModel);
            // use new model as current model
            setCurrentModel(newModel);
        } else {
            // if an adaptation fails, rollback to previous state
            // which means, execute the successfully applied command
            // backwards to go back to the previous state
            compareResult.rollback();
            // notify error
            throw error;
        }
    } else {
        // if the new model is not a valid model, discard it and notify
        throw error;
    }
}
```

### Error handling
If an error occurs while processing the adaptations the Core is in charge of putting the runtime state back to the previous one. This is known as the **rollback** phase.  
A rollback is an execution of all the already processed adaptations but backwards (cf. **Deployment phase** algorithm)

### Using the Core within the running components and fragments
From a component or fragment perspective, one might want to apply reconfigurations on the running system on its own. To do so, each **Component**, **Channel**, **Group** and **Node** must be able to get a reference to the runtime **core**.  

In **Java**, accessing the runtime core can be done like that:
```java
@Component
public class MyComponent {

    @KevoreeInject
    private ModelService modelService;

    public void doSomethingWithCore() {
        modelService.update(aModel, new UpdateCallback() {
            @Override
            public void run(Boolean success) {
                if (success) {
                    // adaptations made
                } else {
                    // problem with adaptation: not done
                }
            }
        });
    }
}
```

In **JavaScript**, each instance can access the core locally:
```js
var AbstractComponent = require('kevoree-entities').AbstractComponent;

module.export = AbstractComponent.extend({
    toString: 'MyComponent',

    doSomethingWithCore: function () {
        this.core.deploy(aModel, function (err) {
            if (err) {
                // problem with adaptation: not done
            } else {
                // adaptations made
            }
        });
    }
});
```
