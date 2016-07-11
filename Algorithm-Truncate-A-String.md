# Algorithm Truncate a String

:triangular_flag_on_post: Remember to use [**`Read-Search-Ask`**](FreeCodeCamp-Get-Help) if you get stuck. Try to pair program :busts_in_silhouette: and write your own code :pencil:

### :checkered_flag: Problem Explanation:

We need to reduce the length of the string or **truncate** it if it is longer than the given maximum lengths specified and add `...` to the end. If it is not that long then we keep it as is.

#### Relevant Links

- [String.prototype.slice()](https://github.com/FreeCodeCamp/FreeCodeCamp/wiki/js-array-prototype-slice)

## :speech_balloon: Hint: 1

Strings are immutable in JavaScript so we will need a new variable to store the truncated string.

> _try to solve the problem now_

## :speech_balloon: Hint: 2

You will need to use the slice() method and specify where to start and where to stop.

> _try to solve the problem now_

## :speech_balloon: Hint: 3

Do not forget that when we truncate the word, we also must count the length added by `...`

> _try to solve the problem now_

## Spoiler Alert!

![687474703a2f2f7777772e796f75726472756d2e636f6d2f796f75726472756d2f696d616765732f323030372f31302f31302f7265645f7761726e696e675f7369676e5f322e676966.gif](https://files.gitter.im/FreeCodeCamp/Wiki/nlOm/thumb/687474703a2f2f7777772e796f75726472756d2e636f6d2f796f75726472756d2f696d616765732f323030372f31302f31302f7265645f7761726e696e675f7369676e5f322e676966.gif)

**Solution ahead!**

## :beginner: Basic Code Solution:

```javascript
function truncateString(str, num) {
  // Clear out that junk in your trunk
  if (str.length > num && num > 3) {
    return str.slice(0, (num - 3)) + '...';
  } else if (str.length > num && num <= 3) {
    return str.slice(0, num) + '...';
  } else {
    return str;
  }

}
```

:rocket: [Run Code](https://repl.it/CLjU/55)

### Code Explanation:

- First we start off with a simple ```if``` statement to determine one of three outcomes...
1. If our string length is greater than the ```num``` we want to truncate at, and our truncate point is at least three characters or more into the string, we return a slice of our string starting at character 0, and ending at ```num - 3```. We then append our ```'...'``` to the end of the string.
2. However, if our string length is greater than the ```num``` but ```num``` is within the first three characters, we don't have to count our dots as characters. Therefore, we return the same string as above, with one difference: The endpoint of our slice is now just ```num```.
3. Finally, if none of the above situations are true, it means our string length is less than our truncation ```num```. Therefore, we can just return the string. 

## :rotating_light: Advanced Code Solution:

```javascript
function truncateString(str, num) {
  if (str.length <= num) {
    return str;
  } else {
    return str.slice(0, num > 3 ? num - 3 : num) + '...';
  }
}
```

:rocket: [Run Code](https://repl.it/CLjU/54)

### Code Explanation:

- First we need an if-statement to test if the length of the full string passed in as the first argument already fits within the size limit passed in as the second argument. If so we can just return the string that was passed in.

```javascript
if (str.length <= num)
  return str;
```

- If our ```if``` statement above fails, we move to the ```else```, where we are going to return a "slice" of the string. The slice method extracts a section of a string and returns a new string. Here we pass 0 as the starting point for our slice. To determine the endpoint, we use a ternary operator: ```num > 3 ? num - 3 : num```. In our ternary, if ```num``` is larger than 3, we must factor in the three dots to our total length, and thus we end our slice at ```num-3```. If num is less than or equal to 3, our slice gets an end variable of just ```num```. Finally, the ```'...'``` is appended to the end of our new string and is returned.

```javascript
} else {
    return str.slice(0, num > 3 ? num - 3 : num) + '...';
  }
```

- **NOTE** In order to understand the above code, you need to understand how a Ternary Operator works. The Ternary Operator is frequently used as a shortcut for the ```if``` statement and follows this format: ```condition ? expr1 : expr2```. If the ```condition``` evaluates to true, the operator returns the value of ```expr1```. Otherwise, it returns the value of ```expr2```.

#### Relevant Links

- [Conditional (ternary) Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)
- [String.prototype.slice()](https://github.com/FreeCodeCamp/FreeCodeCamp/wiki/js-array-prototype-slice)

### :trophy: Credits:

If you found this page useful, you may say thanks to the contributors by copying and pasting the following line in the main chat:

**`Thanks @Rafase282 @bmorelli25 for your help with Algorithm: Truncate a String`**

## :clipboard: NOTES FOR CONTRIBUTIONS:

- :warning: **DO NOT** add solutions that are similar to any existing solutions. If you think it is **_similar but better_**, then try to merge (or replace) the existing similar solution.
- Add an explanation of your solution.
- Categorize the solution in one of the following categories &mdash; **Basic**, **Intermediate** and **Advanced**. :traffic_light:
- Please add your username only if you have added any **relevant main contents**. (:warning: **_DO NOT_** _remove any existing usernames_)

> See :point_right: [**`Wiki Challenge Solution Template`**](Wiki-Template-Challenge-Solution) for reference.
