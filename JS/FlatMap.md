>[!info] https://www.geeksforgeeks.org/javascript-array-flatmap-method/

The ***flatMap() method** transforms each element of an array using a mapping function and flattens the result into a new array. It applies the function to every element, avoiding empty ones, and preserves the original array.

### ****Parameters:****

- ****current_value:**** It is the input array element.
- ****index:****
    - It is optional.
    - It is the index of the input element.
- ****Array:****   
    - It is optional.
    - It is used when an array map is called.

### ****Return Values:****

It returns a new array whose elements are the return value of the callback function.

```JS
let A = array.flatMap(function callback(current_value, index, Array)) {  
// It returns the new array's elements.  
}
```

example
```JS
const sentences = ["Hello world", "How are you?", "JavaScript is fun"]; 
const words = sentences.flatMap(sentence => sentence.split(' ')); console.log(words);
```

**Output**

`[ 'Hello', 'world', 'How', 'are', 'you?', 'JavaScript', 'is', 'fun' ]`