# Clean Coders Notes

Contents
- Intro
- Names
- Functions
- Function Structure
- Form
- Test driven Development


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
upto: 
TDD 27 min in