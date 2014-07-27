# Making a component

The Kevoree platform exists in several versions, namely Java, JS, C++.
However in this documentation we only cover the Java version.
Indeed Kevoree extracts component model information from annotations.
In other words, we can write plain Java code using regular tools like Maven.
Kevoree will take care of the deployement for you.

1. **Create the business code of the component**. Make sure it works by simply adding a main, that creates, starts and stops your component.
2. **Decorate your code with the Kevoree Annotations** to specify that your class is a Kevoree Component, which are the Input ports, Required services, the Output ports, the Provided services, the parameters of your component and the services your require from the runtime.
3. **Compile your code using the Kevoree Annotation plugin**, then the code compiles depending on your implementation language.
4. Enjoy !
