# KevScript tool
## Description

The kevscript tool is a library which takes a kevscript in input and gives kevoree model in return.

It can be see as the combination of 2 components :
  * A transformer from KevScript to a json modelisation of the model.
  * A transformer from a json modelisation of the model to a datastructure in your platform.

By composition of those to components you get a kevscript to kevoree model transformer for your platform.

## Implementations
Following the example of the [model](model.md), you can write the tool for your platform or
transpiling it from another existing implentation.

We did the later for our C# implementation.
