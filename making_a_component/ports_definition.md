# Ports definition

#### Input Ports - Provided Methods

If you are used to Message-Oriented approaches, you just have to put a `@Input` annotation on the method you want to expose as an input port. If you are more familiar with Service-Oriented approaches, you will have to put a `@Provided` annotation on  each method you want to expose/offer.
The port gets its name from the method name. The mapped methods have to declare a unique `Object`-typed parameter. In case this parameter is missing, the method will be called and any parameter from the caller will be dropped. In case the method has more than one parameter, an error will be triggered.
In Kevoree, we have mixed the Message and Service oriented approaches. To this end, each call on a port can declare an optional `Callback` method. Any value returned from an `Input` or a `Provided` method will be forwarded to the caller and passed as parameter to the callback method it declared.

>Java
*************

```Java
@Input
public void sayHelloTo(Object msg) {...}

@Provides
public Boolean getTemp() {...}
```

>Kotlin
*************

```Kotlin
public Input void sayHelloTo(Object msg) {...}

public Provides Boolean getTemp() {...}
```

#### Output Ports - Required Methods

If you are used to Message-Oriented approaches, you just have to put a `@Output` annotation on a field of the class that will host the port. This field has to be typed as `Port` from the Kevoree API. If you are more familiar with Service-Oriented approaches, you will have to put a `@Required` annotation on  each method you want to use.
The port gets its name from the field name.
In Kevoree, we have mixed the Message and Service oriented approaches. To this end, each call on a port can declare an optional `Callback` method. This method is called as soon as the execution of the call is completed. The parameter of the callback is the value of the return of the `Input / Provided` port connected.

>Java
*************

> **Without callback**

```Java
@Output
private org.kevoree.api.Port helloProduced;

public void onHelloProduced(String greetingMessage) {
	helloProduced.send(greetingMessage);
}
```
> **With callback**

```Java
@Required
private org.kevoree.api.Port userDecision;

public boolean askUser(String questionMessage) {
	userDecision.call(greetingMessage, new Callback() {
		public void run(Object result) {
        	return (Boolean)result;
        }
    });
}
```
