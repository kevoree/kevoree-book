# Core
## What is it?
The **Core** is the *director* of a Kevoree runtime:
 - **it is in charge of a node** (Kevoree NodeType)
 - **it has to execute adaptations on deployments** (model@runtime)
 - **keeps track of model changes**

Using pseudo-code, the core algorithm looks like this:

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
