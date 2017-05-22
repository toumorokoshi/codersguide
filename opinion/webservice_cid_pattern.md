# CID: Consumer-Internal-Datasource

The CID pattern introduces a general code organization scheme,
desgined to protect and encapsulate common changes to code:

1. change to an interface, to provide compatability. (Consumer)
2. changes to the datatstore, for performance or architecture. (Datasource)
2. change to behaviour, which is typically agnostic from interface or data storage (Internal)

These are the three layers: consumer, internal, and datasource. Thus, the pattern is named CID.

# CID is good for design

Each layer represents the mindset to have, when considering the design
of that layer. It is true that many changes affect the whole
stack. However, the abstraction is still very important for
refactoring.

## Design for the Consumer

Designing for the consumer is thinking about the user interaction. How
does the user best interact with your application? How can I ensure the user only
sees the complexity they need to say?

## Design for the Datasource

Designing the datasource is mainly about performance and
correctness. How can I ensure an operation is performed efficiently?
How can I ensure that data integrity is preserved?

## Design for the Internal

Designing interally is a lot about code organization and
architecture. There are no hard and fast rules about any of the
layers, but the internal definitons are very loose.

# CID is good for refactoring

## Changing datasources entirely

Since the interface and expectations are well abstracted, switching
datasources comes down to building functions that can directly replace
than functonality.

## Changing interfaces (e.g. http to grpc)

As the interfaces are abstracted from the internal representation,
supported a new interface type becomes:

1. write a converter to and from the internal represention to the new interface
2. add the interface to your code.

That's it! The interface function should also be trivial, since it's a
matter of converting to and from the interface you're targetting.

# CID and data structures

In an ideal CID pattern, there is only one datastructure or object per
concept. Concerns like multiple versions of the interface is delegated
to the interface layer, while anything specific to the datasource
(e.g.  denormalizing data to ensure faster queries) should be
encapsulated in the datasource.

By following this rule, the internal code becomes a clean description
of the behavior of the service itself.
