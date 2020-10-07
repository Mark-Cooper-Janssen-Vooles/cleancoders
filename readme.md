# Clean Coders Notes

Contents
- Intro
- Names
- Functions
- Function Structure
- Form
- Test driven Development
- Architecture, Use Cases and High Level Design


## Intro
- "Leave the code better than you found it" 
- "Random act of kindness to the code"
- "Clean code always looks like it was written by someone who cares"
- "You know that you're reading clean code, whenever every thing you read is pretty much what you expected"

## Names
- Choose your names well and thoughtfully
- When choosing names, communicate intent. No comments - the name should do it!
- Always avoid disinformation - don't let the names meaning rot or drift. It needs to say what it means and means what it says
- Pronouncable names
- Avoid encodings like hungarian notation (except maybe for interfaces.. IPerson)
- Clean code should always read like well-written prose 
    - give classes noun names
    - give variables nouns
    - give methods verbs 
    - if theyre booleans make them predicates (isCar)
- The scope rule:
    - variable names should be short, even one letter, if in a tiny scope
    - variable names should be long and describtive if in a big long scope
    - global variables should be very long
    - function names in a big scope should be short
    - function naems should be long and descriptive if a short scope 
    - short names for public classes
    - longer names for private classes with smaller scope


## Functions
- Keep your functions small, ideally 4 lines max! 
- Lots of little well named functions will save everybody lots of time in the long run
- Classes hide in long functions
- Make sure functions only do one thing - extract till you drop. If you can extract some logic out into another function, you should.
- if you can extract, it means by definition your function was doing more than one thing.


## Function Structure
- Function signatures should be small: 3 or fewer arguments
- You should not pass booleans or nulls into functions
- No output arguments
- Organise methods according to step down principle:
    - public methods at the top
    - methods below them are the ones called by them, so on down the chain
- switch statements violate the OOP paradigm - interferes with independent deployability and developability. we should replace with with polymorphism 
- command & query seperation: tell don't ask
- its better to throw exceptions than return error codes: exceptions should be scoped to our classes
- if a "try" appears in a function, that function is simply an error handling function. that is its one thing. 


## Form 
- Every time you write a comment, you've failed
- Commented out code is an an abomination that must be destroyed before it spreads
- Formatting   
    - white space discipline is important
    - horizontal scroll bars not good, keep line widths ~40 chars, not exceed 120.
    - avg file size should be less than 100 lines, not exceed 500.
- Classes are bags of functions that hide the implementation of the data they manipulate
    - use "tell don't ask" to avoid writing getters and setters.
    - when getters are absolutely necessary, make sure you hide implementation of data by abstracting it. 
    - use classes to protect yourself from new types, but not new functions
- Data structures are bags of data with no cohesive methods
    - don't put business rules into data stuctures 
    - manipulate with switch statements if you must 
    - use them to protect yourself from new functions, but not new types
- boundaries criss-cross our application seperating thigns that are concrete and things that are abstract 
    - all source code dependencies cross those boundaries pointing away from concrete stuff, towards the abstract
- domain objects and database tables aren't the same thing
    - seperate domain objects from your database by putting a layer inbetween them 
    - this layer should depend upward on the application, and downward on the database 
    - the application should not know about the layer, and defs not know about the database 


## Test Driven Development
- "I know of no better way to know that your code works, than to practice the three laws of TDD"
- Code rots because we're afraid to clean it. To keep it clean, we need to eliminate the fear of change. Only a trustworthy suite of tests can do this!
- The three laws of TDD:
    - 1. No production code until you've written a failing unit test
    - 2. WWrite only enough of a unit test to demonstrate a failure
    - 3. Write only enough production code to pass it 


## Architecture, Use Cases and High Level Design
- Architectures are not based on tools and frameworks, good architectures allow you to defer the decisions about tools and frameworks for a long time. 
    - "A good architecture maximises the time for decisions about tools and frameworks not made"
- A good architecture does not depend on the delivery mechanism, it hides it rather than exposing it. You should not be able to tell that its a web system
- Good architecture Allows the business to seperate the cost of the use cases, the UI and other system components
- The use cases of the system should be the primary abstractions and the central organising principles of the system architecture. When you look at that architecture, you should see the intent of the system  (not the user interface)
- Use Jacobsons interactor, entity and boundary partition to create use-case oriented architectures. We learned that interactors encapsulate use-cases, entities encapsulate business objects, and boundaries isolate us from the user interface
- To achieve the details of this isolation we can create a boundary of interfaces that separate the application from the delivery side. Model View Controller makes a good structure for the delivery side. A set of simple data structures can be used to communicate across the boundary.
- Databases should be seperated from entity and interactor objects, using the layering technique
- The interactor objects are responsible for orchestrating database acess
- The true foundation of an application lays in its use-cases. You ask yourself "what must this system do?", but you ask it in a delivery agnostic way - then you add the abstractions that support those delivery agnostic uses-cases.

### Foundations of the SOLID Principles
- What is software design?
    - What do engineers produce? Documents that specify how to build products
    - the source code is the document the software engineer produces
- An architect is expensive and designs the whole house at once, where as the software equivilent is to things one at a time and build them out as needed. 
    - In building houses, the design is expensive 
    - In building software, the design is cheap but the designers cost the most 
- A system is fragile when a small change to one module causes other unrelated modules to misbehave


Summary:
- Software is expensive to design, but cheap to build
    - This implies software should be designed and built iteratively, without huge up-front planning
- Definition of OOP: An objected oriented design is one in which key dependencies have been inverted, we're able to isolate high-level policy from low level detail
- The SOLID principles play a role in dependency management


## Single Responsibility Principle
- About functions and modules, it says the best modules are those that have just one responsibility
    - What is a responsibility?
        - some kind of action, i.e. a database call... SaveEmployee() and GetEmpoyeeById() would be considered the same responsibility, whereas DescribeEmployee() would be a different responsibility
- Single responsibility principle is about the users, the responsibilities are the responsibilities classes and methods have to those users - specifically users who will request changes to the software
    - a responsibility can be viewed as a "source of change"
- If the software is easy to change, its good for the business. If its hard to change, its bad for the business.
    - Secondary job of a developer: get the software to work
    - Primary job of a developer: give the software shape and structure that makes it easy to change
- Conclusion:
    - Classes have responsibilities to users, those users can be classified as actors by the roles they play
    - A responsibility is a family of functions that serves one particular actor 
    - The two values of software: primary is keep it flexible
    - Carefully allocating responsibility to classes and modules is one of the ways we keep the primary value of software high
    - When modules contain more than one responsibility, the system becomes fragile


### Open-Closed Principle
- Open to extension, closed to modification
- Should be easy to change the behaviour of a module, without having to change the source code of that module 
- If you design your code to open-closed principle, then when you modify them you'll do so by adding new code instead of changing old code ... the old code should theoretically never need modification again!
    - Except perhaps ``Main()``
    - The crystal ball problem... we cannot completely conform to it, but should aim for it. Functions, classes, small components should conform to it. 
- Issues with this is that you don't have a crystal ball, so you dont know the new features or changes the customers will request. 
    - Solutions:
        - BDUF (big design up front) - you think really hard about everything the customer may want
            - but creates large top-heavy designs littered with designs 
            - abstractions are expensive, make it hard to follow from cause to effect 
            - when we need abstractions, the cost is bearable. but when theyre anticipatory, the cost is overwhelming
        - Agile design
            - do the simplest thing you possibly can, get it out in front of the customer as soon as possible - then the customer starts shooting at it with change requests, and then you know what change requests are likely
            - wait for the customer to request a change, then make an abstraction that will prevent any further change to that feature in the future, as the best predictor of change is past-change 


### Liskov Substitution Principle