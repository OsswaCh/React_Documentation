# Number toString()


### Examples
https://www.w3schools.com/jsref/jsref_tostring_number.asp

Convert a number to a string:

let num = 15;  
let text = num.toString();

Convert a number to a string, using base 2 (binary):

let num = 15;  
let text = num.toString(2);  
## Note

Every JavaScript object has a `toString()` method.

The `toString()` method is used internally by JavaScript when an object needs to be displayed as a text (like in HTML), or when an object needs to be used as a string.

Normally, you will not use it in your own code.

---

## Syntax

_number_.toString(_radix_)

## Parameters

|Parameter|Description|
|_radix_|Optional.  <br>The base to use.  <br>Must be an integer between 2 and 36.  <br>Base 2 is binary  <br>Base 8 is octal  <br>Base 16 is hexadecimal.|

## Return Value

|Type|Description|
|A string|The number as a string.|