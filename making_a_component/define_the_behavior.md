# Define the Behavior
The smallest state machine (called 'statechart' in ThingML as a reference to the UML statecharts):

```
statechart MyStateMachine init MyState {
  state MyState {}
}
```

Each state machine is given a name and must have an initial state.
ThingML supports simple states, composite states and history states.

```
// simple state
state MyState {}

// composite state
composite state MyCompositeState1 init InnerState1 {
  state InnerState1 {}
  state InnerState2 {}
}

// history state
composite state MyCompositeState2 init InnerState3 keeps history {
  state InnerState3 {}
  state InnerState4 {}
}
```

Regular composite states enter their initial state whenever they are activated.
History states enter their initial state the first time they are activated, save their current state when exited and re-enter that state when activated again.
All states (composite or not) can have entry and exit actions, which are executed when entering and leaving the state.
Here is an example for a simple state (the entry and exit action must be defined before any transition):

```
state MyState {
  on entry do /* some actions */ end
  on exit do /* some actions */ end
}
```

In the same way, composite states and the state machine itself can have entry and exit actions. When entering composite states the order of execution of the entry actions is from the outer state to the inner state. When leaving a composite state the exit action of the inner state is executed before the exit action of the composite state.
Transitions can be defined both on simple states and composite states. Transitions can only be defined between sibling states: they can cross neither composite states boundaries nor region boundaries (regions are explained below).

Transitions must have at least a target state and a trigger event (the name is optional):

```
state MyState1 {
  transition t1 -> MyState2
  event port?message
}

state MyState2 {}
```

The current version of ThingML only supports events which correspond to the reception of at a message or the "empty event". In the future version, we are investigating the addition of "complex events" which could be constructed by a combination of a set of events in a given time frame. This is related to the complex-event processing work done in WP4.
Optionally transitions can have a guard condition and actions:

```
transition t2 -> MyState2
event myPort?myMessage
guard /* some condition */
action /* some action */
```

For such a transition the guard is evaluated every time the message "myMessage" is received on port "myPort". If the guard is true the transition is fired, i.e. the exit action of the current state is executed, the action of the transition is executed and the entry action of the target state is executed.
Several events can trigger a transition:

```
// Transition with multiple events
transition t3 -> MyState2
event myPort1?myMessage1
event myPort1?myMessage2
event myPort2?myMessage3
```

Internal transitions can be used to implement event handlers on states which do not exit and reenter the state.
The example below shows a state with an auto-transition (i.e. a transition to itself) which is triggered by the message "myMessage1" and an internal transition triggered by the message "myMessage2".

```
state MyState {
  on entry /* some entry action */
  on exit /* some exit action */

  transition -> MyState
  event myPort?myMessage1
  action /* some action */

  internal event myPort?myMessage2
  action /* some action */
}
```

When "myMessage1" is received, the transition is fired and the exit action is executed, followed by the transition action and the entry action.
When "myMessage2" is received the internal transition is fired and only the internal transition action is executed. The difference between a transition to self and an internal event is that in the case of the internal event the state is not left and re-entered which means that the exit and entry actions are not executed.
State machines and composite states can contain one or more parallel regions. Each region executes independently from each other: they have their own initial, history and current states.
By default a state machine and composite states define one region. Additional regions can be added using the "region" keyword:

```
statechart MyStateMachine init MyState1 {

  state MyState1 {}

  region MyRegion2 init MyState2 {
    state MyState2 {}
  }

  region MyRegion3 init MyState3 {
    state MyState3 {}
  }
}
```

In this example the state machine is made of 3 parallel regions. The first one is defined by the state machine "MyStateMachine" and the two other ("MyRegion2" and "MyRegion3") are explicitly added.

> There are no semantic differences between the three regions; the first one is defined by default just to make the syntax a bit more compact.

