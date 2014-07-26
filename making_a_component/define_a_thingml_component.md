# Define a ThingML Component
The core concept of ThingML is thing. A thing defines a component which can send and receive a set of messages asynchronously. Messages are sent and received via ports. The overall behaviour of a thing is defined using a state machine.
Here is the syntax for the definition of a thing:
```
// definition of an empty thing
thing myThing {
  /* Some properties */
  /* Some messages */
  /* Some ports */
  /* Some state machines */
}
```

Properties are declared, initialized and manipulated similarly as in C or Java. ThingML state machines communicate by exchanging messages in an asynchronous way. The declaration of a message in ThingML is quite similar, from a syntactical point of view, to the declaration of methods in a Java interface (without any return type):

```
//definition of a message with two parameters
message sendState(name : String, state : DigitalState );
```

Ports allow grouping messages into coherent units. Basically, a thing providing a service will declare something like:

```
thing MyThingProvidingServiceA {
  //request to get the status of the sensor called name
  message getState(name : String);
  //response
  message sendState(name : String, state : DigitalState );

  provided port ServiceA {
    receives getState
    sends sendState
  }
}
```

Even though ThingML is not an object-oriented programming (OOP) language, and thus does not provide plain inheritance, it provides some basic mechanisms to improve the modularity/reusability of fragments of ThingML provides. The notion of thing fragment allows designer to specify interfaces. A thing fragment can declare messages and ports, but does not contain any behaviour. Typically, the top thing fragment will only contain the set of messages that are relevant for a given service. Two other thing fragments will include this former fragment and organize the messages into ports, as follows:

- The thing fragment providing the service will specify which messages it could receive, and which messages it could send, and organize them into ports.
- The thing fragment requiring the service will basically organize the messages into a mirror structure, so that it is possible to connect both things.

Typically, thing fragments only declare some messages, but they could also define any feature (such as properties) we can find in plain things (except behaviour).
The previous code fragment would then be refactored into:

```
//Interface for the service A
thing fragment ServiceAMsgs {
  //request to get the status of the sensor called name
  message getState(name : String);
  //response
  message sendState(name : String, state : DigitalState );
}

//Concrete thing providing A
thing MyThingProvidingServiceA  includes ServiceAMsgs{
  provided port ServiceA {
    receives getState
    sends sendState
  }
}
```



