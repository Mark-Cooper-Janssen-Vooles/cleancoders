# Clean Coders Notes

Contents
- Intro
- Names
- Functions
- Function Structure
- Form
- Test driven Development


### Intro
- "Leave the code better than you found it" 
- "Random act of kindness to the code"
- "Clean code always looks like it was written by someone who cares"
- "You know that you're reading clean code, whenever every thing you read is pretty much what you expected"

### Names
(variable names)
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



## Form 


## Test Driven Development
upto: 
TDD 27 min in