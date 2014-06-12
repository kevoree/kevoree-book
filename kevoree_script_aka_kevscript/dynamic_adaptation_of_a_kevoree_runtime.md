# Dynamic adaptation of a Kevoree Runtime

The dynamic adaptation of a Kevoree Runtime is not the business of KevScript.
If you want to use a KevScript to realize an adaptation of your system, you have to:

1. Create a KevScript and ask for its execution on a model. This execution will give you a new model.
2. Ask the runtime for a deployment of this new model.
3. Back to the step #1
