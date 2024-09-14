# TC39 Proposal: string-splice



## Status

**Stage:** 0

*For more information see the [TC39 proposal process](https://tc39.github.io/process-document/).*

## Authors

- [electroluxcode](https://github.com/Electroluxcode/)

## Summary

This proposal aims to introduce a new string manipulation method called `string-splice` in JavaScript. This method will provide a more intuitive and efficient way to insert, replace, or remove substrings within a string.

## Motivation

Currently, JavaScript developers often rely on a combination of string methods such as `substring`, `slice`, and concatenation to achieve substring manipulation. This can lead to complex and error-prone code. The `string-splice` method simplifies these operations, making string manipulation more straightforward and reducing the cognitive load on developers.

## Proposed Syntax

```js
string.splice(startIndex, deleteCount, insertString);
```



## Semantics

1. `startIndex` indicates the position within the string where the manipulation should start.
2. `deleteCount` determines the number of characters to be removed starting from `startIndex`. If `deleteCount` is 0, no characters are removed.
3. `insertString` is the string that will be inserted at the `startIndex` position.
4.  similar to the `splice` method of an array



## Examples

```javascript
// Example 1: Inserting a substring
let str1 = "Hello world";
let newStr1 = str1.splice(5, 0, "beautiful ");
console.log(newStr1); // Outputs: Hello beautiful world

// Example 2: Replacing a substring
let str2 = "The quick brown fox";
let newStr2 = str2.splice(4, 5, "slow");
console.log(newStr2); // Outputs: The slow brown fox

// Example 3: Removing a substring
let str3 = "JavaScript is great";
let newStr3 = str3.splice(10, 5);
console.log(newStr3); // Outputs: JavaScript is
```



## Detailed Behavior

1. If `startIndex` is negative, it is counted from the end of the string.
2. If `startIndex` is greater than the length of the string, the string remains unchanged.
3. If `deleteCount` is greater than the number of characters remaining in the string starting from `startIndex`, all characters from `startIndex` to the end of the string are removed.

## Benefits

1. **Readability**: The `string-splice` method makes the intention of string manipulation clear, enhancing code readability.
2. **Simplicity**: Reduces the complexity of string manipulation by providing a single method for common operations.
3. **Efficiency**: Potentially more efficient than a series of concatenation and slicing operations.



## Potential Issues and Considerations

1. **Overloading the String Prototype**: Adding a new method to the string prototype might conflict with existing code or libraries that have their own extensions to the string prototype.
2. **Compatibility**: Ensuring compatibility with older JavaScript engines that do not support this new method.
3. **Error Handling**: Deciding how to handle invalid input such as non-integer values for `startIndex` and `deleteCount`.



## More Examples

### 1. Advanced Insertion

```javascript
let str4 = "12345";
let newStr4 = str4.splice(-2, 0, "-6-7");
console.log(newStr4); // Outputs: 123-6-745
```

### 2. Multiple Replacements

```javascript
let str5 = "aaaaa";
let newStr5 = str5.splice(1, 3, "b", "c", "d");
console.log(newStr5); // Outputs: abcd a
```

### 3. Edge Cases

```javascript
// Start index out of bounds
let str6 = "abc";
let newStr6 = str6.splice(5, 1, "x");
console.log(newStr6); // Outputs: abc

```



## Backwards Compatibility

This proposal is designed to have minimal impact on existing code. In environments that do not support the `string-splice` method, developers can still use traditional string manipulation techniques. However, in environments where it is supported, it offers a more convenient alternative.