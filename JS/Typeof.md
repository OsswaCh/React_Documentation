## The typeof Operator
### Primitive Data Types

In JavaScript, a primitive value is a single value with no properties or methods.

JavaScript has 7 primitive data types:

- string
- number
- boolean
- bigint
- symbol
- null
- undefined

The `typeof` operator returns the type of a variable or an expression.

### Examples

typeof "John"         // Returns string  
typeof ("John"+"Doe") // Returns string  
typeof 3.14           // Returns number  
typeof 33             // Returns number  
typeof (33 + 66)      // Returns number  
typeof true           // Returns boolean  
typeof false          // Returns boolean  
typeof 1234n          // Returns bigint  
typeof Symbol()       // Returns symbol  
typeof x              // Returns undefined