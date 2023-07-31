# Definition of Dependency injection

Dependency injection is set of software design principles and paterns that enables you to develop loosely coupled code.

## How to explain Dependency injection to five year old

When you go and get things out of the refrigerator for yourself, you can cause problems. You might leave door open, you might get
something Mommy and Daddy does't want you to have. You might even be looking for something we don't even have or which has expired.

What you should be doing is stating a need, "I need something to drink at lunch" and then we  will make sure you have something when
you sit down to eat.

What this means in terms of object oriented software development is this: collaborating classes (the five year old) should rely on
infrastructure(the parrents) to provide necessary services

## Purpose of DI
Purpose of DI isn't a goal itsels, its a means to an end. Meaning, creating maintainable code. as quoted in gang of four:
"Program to interface not implementation"

DI is nothing more than tehnique that enables loose coupling

## Common myths about DI

- DI is only relevant for late binding
- DI is only relevant for unit testing
- DI is a sort of Abstract factory on steroids
- DI requires DI container

Although none of these myts are true they are prevalent nonetheless.

### DI is only relevant for late binding
late binding referes to the ability to replace parts of application without recompiling the code, meaning if application supports both
oracle and sql databases, we can change database targeting via configuration.

### DI is only relevant for unit testing
DI helps a lot regarding unit testing, meaning we can easyly substitute services with mock data, but that is not only function of DI
and should not be in mindset that is used "ONLY" for that.

### DI is a sort of Abstract factory on steroids
The most dangerous fallacy is that DI involves some sort of general purpose Abstract Factory that you can use to create instances of
dependancies needed for application.

DI is "NOT" a service locator. it is exact opostive of it. it is a way to structure code so that you never have to imperativly ask for
dependencies, Rather you requre consumers to supply them.


### Testability
Unit Tests provide rapid feedback on the state of an application, but it is only possible to write unit tests when the unit in question
can be properly isolated from its Dependencies.

It's only when application is susceptible to unit testing that it's considered Testable, the safest way to ensure Testability is to develop
using TDD.

Unit tests alone don't ensure a working application.


### Seams
Everywhere you decide to program agains an Abstraction instead of concrete type, you introduce a Seam into application.

A Seam is a place where an application is assembled from its constituent parts, similar to the way a piece of clothing is sewn
together at its seams. It's also the place where you can dissasemble the application and work with modules in isolation.

### Stable Dependancies
The Important criteria for stable dependencies include the following

- The Class or module already exists
- New version does not contain breaking changes
- The types in question contain deterministic algorithm
- You never expect to: replace, wrap, decorate or intercept the class or module with another

### Volatile Dependancies
The Dependency should be considered volatile if any of the following criteria are true

- The Dependency  introduces a requirement to set up and configure runtime environment for the application. (e.g Databases, message queues, web service, file system)
- The Dependancy isnt installed on all machines in the development organizatuin (e.g expensive third party libraries or dependacies)
- The Dependancy contains non-determistic behavior.

Voilatile Dependancies are the focal point of DI. its for the voilatile dependancies that we intruduce seams into our application.

## Conclusion
Dependency injection is a means to the end, not the goal itself. It's the best way to enable loose coupling, an important part of maintainable code, the benefits are
not always imediatly apparent, but they become visable over time as complexity of code increases.

A tightly coupled code base will eventualy deteriorate into spagheti code, whereas well designed, loosely coupled code base can stay maintainable.

DI is nothing more then a collection of design principles and patterns. It's more about a way of thinking and designing code than it's about tools and techniques, The
purpose of DI is to make code maintainable.
