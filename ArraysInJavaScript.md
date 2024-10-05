# Arrays in JavaScript

Arrays in JavaScript can initially be confusing and challenging to grasp, especially when dealing with advanced concepts. I, too, struggled with understanding arrays in JavaScript at first. In this article, I aim to demystify arrays in JavaScript, breaking down everything you need to know so you can work with them confidently.

## Definition

### What Is an Array

An array is a data structure that stores a collection of elements, each accessible by an index. In many programming languages, arrays store elements in contiguous memory locations. In JavaScript, arrays are high-level, list-like objects used to store multiple values in a single variable. They are zero-indexed, meaning the first element is at index `0`.

### Arrays in JavaScript

Since JavaScript is a dynamically typed language, arrays can hold elements of different types. An array can contain numbers, strings, booleans, objects, and even other arrays. This differs from statically typed languages like `Java` or `C++`, where arrays are typically homogeneous and must contain elements of the same data type.

## Why use an array?

Arrays help manage data efficiently by allowing you to store, access and manipulate values. They are used for anything that involves lists or collections, like managing items in an e-commerce cart or keeping track of user inputs.

## How to create an array in JavaScript

There are multiple ways to create arrays in JavaScript, I will go over few of them:

### 1. Using array literals `[]`

In JavaScript, you can simply create an array by assigning `[]` to a variable or a constant

```javascript
const numbers = [1, 2, 3];
const fruits = ["Apple", "Banana", "Orange"];
```

Notice that elements of an array are separated by comma `,`

### 2. Using `Array` constructor

You can also create an array as an instance of a native JavaScript `Array` constructor using the following this syntax:
`const myArray = new Array()`
The `Array` constructor takes one or more arguments (they have to be numbers), and it behaves differently according to the numbers of arguments you pass in!
If you pass one argument: `const myArray = new Array(4)`, this will create a new array with 4 empty elements!

If you pass more that one arguments: `const myArray = new Array(1, 2, 3)`, this creates an array of 3 numbers `1`, `2` and `3` respectively and it is simiral to writing `const myArray = [1, 2, 3]`!

I know this looks confusing but trust me it is easy if you make some more exercises with them!

### 3. Using `Array.of` method

Arrays can also be created using this method `Array.of` and it will just create an array containing all elements you pass to it as arguments. The difference betwee using `Array.of` and `Array` constructor lies in how they behave when they receive one argument!

```javascript
const array1 = Array.of(1); // This returns [1]
const array2 = Array.of(2, true, "hello"); // This returns [2, true, 'hello']
```

Notice how `Array.of` behaves when it receives one parameter, unlike `Array` constructor which just creates an array of `n` empty elements, the `Array.of` just creates an array with single element which is the one you passed in!

### 4. Using `Array.from` method

You can also use `Array.from(iterable)` method, which receives one argument which also must be an iterable and creates an array out of it! For example, you can pass a set to this method and creates an array from the values of that set!

```javascript
const mySet = new Set([2, 3, 4, 5, 5]);
const arrayFromSet = Array.from(mySet);
```

## Arrays manipulation in JavaScript

We've seen what is an array and how you can create arrays in JavaScript, now the remaining problem you might be asking yourself is, how do I use and work with arrays?
Well, that's a good question!

### Traditional way of working with arrays in JavaScript

Traditionally, we use loops to iterate over the elements stored in an array and use them!
The following example shows how you can loop over an array of numbers and display the double of every number inside the array:

```javascript
const numbers = [1, 2, 3, 4];
for (let i = 0; i < numbers.length; i++) {
  console.log(numbers[i] * 2);
}
```

### Using modern JavaScript array method syntax

JavaScript comes with many array methods (higher-order functions) out of the box, they are accessible to all array instances through `Array.prototype` object, we use those methods provided by JavaScript to manipulate and work with data stored in arrays! We can even create our own array methods (we will look at this on next chapter)

They are higher-order methods, because they take other functions as arguments and use those functions to manipulate the data stored in arrays!

Those array methods are also categorized into two categories:

1. **Mutating:** These loop over the array and while applying the callback function, they also mutate the original array!
2. **Non-mutating:** These iterate over the array and apply the callback function, but instead of mutating the original array, they return new array

#### 1. `forEach()` method

`forEach()` is an array higher-order method used to loop over elements of an array and apply a callback function on every element without either modifying the original array or creating a new array!

The syntax of the callback functions which is usually anonymous function (usually the same in all other methods):

```javascript
function (currentElement[, index, targetArray]) {}
```

This means that on every iteration, the array method has access to the current element in iteration (`currentElement`), it's index in the array `index` which is optional, and the reference to the target array in which the method is being executed over `targetArray` which is also optional. But you can call those parameters however you want, you just need to pay attention on their positions.

```javascript
const numbers = [1, 2, 3, 4];
numbers.forEach((element) => {
  console.log(element * 2);
});
```

#### 2. `map()` method

Just like `forEach` map is also another way of iterating over the elements of the array and apply the callback function on every element, but unlike `forEach` map is non-mutating method and hence it creates and return the new array as a result of iteration and does not change the original array!

```javascript
const numbers = [1, 2, 3, 4];
const squaredNumbers = numbers.map((element) => element * 2);
console.log(squaredNumbers);
```

#### 3. `filter()` method

`filter()` method is used when you want to filter the array by removing the elements you don't want, this is non-mutating method and it returns a new array!
For every iteration, the callback inside the `filter()` must return a boolean value indicating whether or not the current element is to be included in the new filtered array

```javascript
const numbers = [1, 2, 3, 4];
const evenNumbers = numbers.filter((element) => element % 2 === 0);
console.log(evenNumber); // [2, 4]
```

#### 4. `reduce()` method

`reduce()` method is a bit different from those above, it is used to reduce the elements of an array into a single value, it is neither mutating because it does not change the original array nor non-mutating because it does not return a new array. Instead it returns a single value, you will use it when you want a single value from all elements of an array like sum, average, maximum or minimum just to name a few!

The syntax is a also different
`Array.reduce(function(accumulator, element[, index, targetArray]) [, initialValue])`

This method takes two arguments, the first one is the callback function just like other methods, and the second one will be the initial value of the `accumutator` variable. This second argument is optional, if it is not provided, the reduce will use the first element of an array as the initial value of `accumulator`

The `accumulator` holds the result returned by the callback function on each iteration and will be the final result returned from the `reduce` once the iteration is over!

Let's try to find a sum from an array of numbers:

```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((accumulator, element) => accumulator + element);
console.log(sum);
```

#### 4. `slice()` method

`slice()` is another useful array method in JavaScript, which is used to extract a small portion of an array! `slice()` creates a new array by copying a section of an existing array without modifying the original array.

The syntax for the `slice()` method is as the following:
`Array.slice(startIndex, endIndex)` `startIndex` represents a starting point of extraction and it is inclusive and the `endIndex` represents the ending element of extraction, it is optional and exclusive. When it is not provided, the `slice` methods copies an array from `startIndex` to the end of an array!

```javascript
const fruits = ["apple", "banana", "orange", "mango"];
const slicedFruits = fruits.slice(1, 3); // ['banana', 'orange']
```

#### 5. `splice()` method

`splice()` is an array method in JavaScript, which is used for adding, removing and replacing elements in array. `splice()` changes the content of an array by adding, removing or replacing elements in array.

The syntax for the `splice()` method is as the following:
`Array.splice(index, elementsToRemove, newElement1, newElement2, ..., newElementn)`
This might look confusing but, let me try to explain:
`index` means the starting index in the array in which the removing of element is supposed to begin and it is inclusive.
`elementsToRemove` represents the number of elements from `index` in which you want to remove from array, if you only want to add new elements, you can provide `0` in this position.
`newElement1`, `newElement2` etc. These can be any number of elements you want to add in your array and they will replace `elementsToRemove` elements you specified in your array!

Much of talking, let's see an example:

```javascript
const fruits = ["apple", "banana", "orange", "mango"];
// If we want to replace 'banana' with 'pineapple'
const splicedFruits = fruits.splice(1, 1, "pineapple"); // This will return ['apple', 'pineapple', 'orange', 'mango']
```

`fruits.splice(1, 1, "pineapple")` this means from index of `1`, remove `1` elements and add `'pineapple'`
If we only wanted to add `pineapple` in array not replacing other value with it, we could have written this as
`fruits.splice(1, 0, "pineapple")` this would add `pineapple` after element at index`1` and will not remove any other element from this array.

## Conclusion

Arrays are a fundamental and versatile feature in JavaScript, offering an essential structure to store and manipulate collections of data. From simple array creation using literals to more advanced methods like `Array.of()` and `Array.from()`, JavaScript arrays provide a range of ways to handle different types of data. By mastering array manipulation through loops or modern methods like `forEach()`, `map()`, `filter()`, `reduce()`, `slice()`, and `splice()`, you can efficiently perform complex operations. Understanding these array features is key to becoming proficient in JavaScript, allowing you to write cleaner, more concise, and powerful code.
