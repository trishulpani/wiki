# Algorithm Drop It

![](https://i.imgur.com/goyTFy2.png)

:triangular_flag_on_post: Remember to use [**`Read-Search-Ask`**](FreeCodeCamp-Get-Help) if you get stuck. Try to pair program :busts_in_silhouette: and write your own code :pencil:

### :checkered_flag: Problem Explanation:

Basically while the second argument is not true, you will have to remove the first element from the left of the array that was passed as the first argument.

#### Relevant Links

- [Arguments object](JS-Arguments)
- [Array.shift()](JS-Array-Prototype-Shift)
- [Array.slice()](JS-Array-Prototype-Slice)

## :speech_balloon: Hint: 1

You can use `Array.prototype.shift()` or filter that you should be more familiar with to solve this problem in a few lines of code.

> _try to solve the problem now_

## :speech_balloon: Hint: 2

Shift returns the element that was removed which we don't really need, all we need is the modified array that is left.

> _try to solve the problem now_

## :speech_balloon: Hint: 3

If you still can't figure out how to solve it with shift, then try solving it with filter, and check how filter works, if you become familiar with it, then you can make the code with shift.

> _try to solve the problem now_

## Spoiler Alert!

![687474703a2f2f7777772e796f75726472756d2e636f6d2f796f75726472756d2f696d616765732f323030372f31302f31302f7265645f7761726e696e675f7369676e5f322e676966.gif](https://files.gitter.im/FreeCodeCamp/Wiki/nlOm/thumb/687474703a2f2f7777772e796f75726472756d2e636f6d2f796f75726472756d2f696d616765732f323030372f31302f31302f7265645f7761726e696e675f7369676e5f322e676966.gif)

**Solution ahead!**

## :beginner: Basic Code Solution:

```javascript
function dropElements(arr, func) {
  // drop them elements.
  var times = arr.length;
  for (var i = 0; i < times; i++) {
    if (func(arr[0])) {
      break;
    } else {
      arr.shift();
    }
  }
  return arr;
}

// test here
dropElements([1, 2, 3, 4], function(n) {return n >= 3;})
```

:rocket: [Run Code](https://repl.it/CLna/0)

### Code Explanation:

- Create a for loop to check each element.
- Then check for the function given if true then stop, otherwise remove that element.
- return the array.

#### Relevant Links

- [For Loops](JS-For-Loop)
- [More about for loops](JS-For-Loops-Explained)

## :sunflower: Intermediate Code Solution:

```javascript
function dropElements(arr, func) {
  return arr.slice(arr.findIndex(func) >= 0 ? arr.findIndex(func): arr.length, arr.length);
}

// test here
dropElements([1, 2, 3, 4], function(n) {return n >= 3;});
```

:rocket: [Run Code](https://repl.it/CLnc/0)

### Code Explanation:

- Use ES6 `findIndex()` function to find the index of the element that passes the condition
- Slice the array from the found index until the end
- There is one edge case! if the condition is not met against any of the elements 'findIndex' will return `-1` which messes up the input to `slice()`. In this case use a simple conditional operator to return `false` instead of `-1`. And the ternary operator (?:) returns the found index of required elements when the condition is `true`, and the length of the array otherwise so that the return value is an empty array as is instructed.

#### Relevant Links

- [findIndex()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)
- [Conditional Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)

## :rotating_light: Advanced Code Solution:

```javascript
function dropElements(arr, func) {
  while(arr.length > 0 && !func(arr[0])) {
    arr.shift();
  }
  return arr;
}

// test here
dropElements([1, 2, 3, 4], function(n) {return n >= 3;});
```

:rocket: [Run Code](https://repl.it/CLnf/0)

### Code Explanation

- Use a while loop with `Array.prototype.shift()` to continue checking and dropping the first element of the array until the function returns true. It also makes sure the array is not empty first to avoid infinite loops.
- Return the filtered array.

#### Relevant Links

- [While loops](JS-While-Loop)

### :trophy: Credits:

If you found this page useful, you may say thanks to the contributors by copying and pasting the following line in the main chat:

**`Thanks @Rafase282 @sabahang for your help with Algorithm: Drop it`**

## :clipboard: NOTES FOR CONTRIBUTIONS:

- :warning: **DO NOT** add solutions that are similar to any existing solutions. If you think it is **_similar but better_**, then try to merge (or replace) the existing similar solution.
- Add an explanation of your solution.
- Categorize the solution in one of the following categories &mdash; **Basic**, **Intermediate** and **Advanced**. :traffic_light:
- Please add your username only if you have added any **relevant main contents**. (:warning: **_DO NOT_** _remove any existing usernames_)

> See :point_right: [**`Wiki Challenge Solution Template`**](Wiki-Template-Challenge-Solution) for reference.
