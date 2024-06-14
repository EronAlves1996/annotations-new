* Functions have a limit on 255 parameters? OMG
* Primitive types implements Serializable and Comparable. Semantically, my own primitives is a same as the boxed primitive types, so, I should leverage comparable in order to able interoperation with generic code.
- Another aspect that is fact of investigation is how the boxed types are really implemented.
- Constructors should preview boxed types, but I'll leverage the two forms, I don't want to allow autoboxing to take it's place.
- Comparing two objects that are not the same impose some level of challenge on design of methods. See, what should I consider here? When they are no the same object or the same semantically object, I should return that are 'semantically' equal? It doesnt seems that it should be correct. Throwing an error might introduce some types of problems, but can be complemented with API docs. It imposes limitations in mixed collections
- Integer and Double extends from Number, which is an abstract class. However, Number don't implements Comparable. It's implemented on subclass.
- Interfaces cannot override a method from `java.lang.Object`

## Debugging

* Debugging version bugs is difficult and disgusting. Spend about 3 hours on a bug on soft delete for Hibernate Reactive on Quarkus (add it to the indirection of dependencies), to discover that it was solved about 2 weeks ago.
* When occurs a server error, it's really important to print the stack trace to console to help debugging

## IDE's

* If loose dependencies references in Eclipse, rebuild it with package manager (gradle, mvn) manually