# Algorithm Title Case a Sentence

:triangular_flag_on_post: Remember to use [**`Read-Search-Ask`**](FreeCodeCamp-Get-Help) if you get stuck. Try to pair program :busts_in_silhouette: and write your own code :pencil:

### :checkered_flag: Problem Explanation:

We have to return a sentence with title case. This means that the first letter will always be in uppercase and the rest will be in lowercase.

#### Relevant Links

- [Global String Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
- [JS String Prototype ToLowerCase](JS-String-Prototype-ToLowerCase)
- [JS String Prototype ToUpperCase](JS-String-Prototype-ToUpperCase)
- [JS String Prototype Replace](JS-String-Prototype-Replace)

## :speech_balloon: Hint: 1

- You should start by splitting the string into an array of words.
- Split the sentence.

> _try to solve the problem now_

## :speech_balloon: Hint: 2

- You should make the word lowercase before making the first letter uppercase.
- Use replace method on each word to capitalize the first letter of each word.

> _try to solve the problem now_

## :speech_balloon: Hint: 3

- You will need to create a new string with pieces of the previous one and at the end merge everything into a single string again.
- In replace method, give first argument as the position of the first letter using charAt. For second argument write a function to return the capitalized letter as the replacement.

> _try to solve the problem now_

## Spoiler Alert!

![687474703a2f2f7777772e796f75726472756d2e636f6d2f796f75726472756d2f696d616765732f323030372f31302f31302f7265645f7761726e696e675f7369676e5f322e676966.gif](https://files.gitter.im/FreeCodeCamp/Wiki/nlOm/thumb/687474703a2f2f7777772e796f75726472756d2e636f6d2f796f75726472756d2f696d616765732f323030372f31302f31302f7265645f7761726e696e675f7369676e5f322e676966.gif)

**Solution ahead!**

## :beginner: Basic Code Solution:

```javascript
String.prototype.replaceAt = function(index, character) {
    return this.substr(0, index) + character + this.substr(index+character.length);
};


function titleCase(str) {
    var newTitle = str.split(' ');
    var updatedTitle = [];
    for (var st in newTitle) {
        updatedTitle[st] = newTitle[st].toLowerCase().replaceAt(0, newTitle[st].charAt(0).toUpperCase());
    }
    return updatedTitle.join(' ');
}
```

:rocket: [Run Code](https://repl.it/CLjU/8)

### Code Explanation:

We are modifying the `replaceAt` function using prototype to facilitate the use of the program.

Split the string by white spaces, and create a variable to track the updated title. Then we use a loop to turn turn the first character of the word to uppercase and the rest to lowercase. by creating concatenated string composed of the whole word in lowercase with the first character replaced by it's uppercase.

#### Relevant Links

- [JS For Loops Explained](JS-For-Loops-Explained)
- [JS String Prototype Split](JS-String-Prototype-Split)
- [JS String Prototype Substr](JS-String-Prototype-Substr)
- [JS Array Prototype Join](JS-Array-Prototype-Join)

## :sunflower: Intermediate Code Solution:

```javascript
function titleCase(str) {
  var convertToArray = str.toLowerCase().split(" ");
  var result = convertToArray.map(function(val){
      return val.replace(val.charAt(0), val.charAt(0).toUpperCase());
  });
  return result.join(" ");
}

titleCase("I'm a little tea pot");
```

:rocket: [Run Code](https://repl.it/CLjU/9)

### Code Explanation:

We are making entire string lowercase and then converting it into array. Then we are using map function to replace the lowercase character with uppercase. Finally, we are returning the string using `join` method.

#### Relevant Links

- [JS Array Prototype Map](JS-Array-Prototype-Map)

## :rotating_light: Advanced Code Solution:

```javascript
function titleCase(str) {
  return str.toLowerCase().replace(/( |^)[a-z]/g, (L) => L.toUpperCase());
}
```

:rocket: [Run Code](https://repl.it/CLjU/14)

### Code Explanation:

The solution works by first lowercasing all the characters in the string and then only uppercasing the first character of each word.
- Lowercase the whole string using `str.toLowerCase()`.
- Replace every word' first character to uppercase using `.replace`.
- Search for words and a lowercase character at the beginning of each word i.e. matching any lowercase character following a `space` or matching the first character of the whole string, by using the following pattern.
- Regex explanation:

  - `( |^)` matches a `space` character or beginning of the whole string (`^`).
  - `[a-z]` matches a single character in the range between a to z (case sensitive i.e. lowercase).

- The `g` modifier searches for other such word pattern in the whole string and replaces them.

#### Relevant Links

- [JS Regex Resources](JS-Regex-Resources)

### :trophy: Credits:

If you found this page useful, you can give thanks by copying and pasting this on the main chat:

**`Thanks @Rafase282 @PoojaKumar @Hallaathrad @abhisekp @ksharifbd for your help with Algorithm: Title Case a Sentence`**

## :clipboard: NOTES FOR CONTRIBUTIONS:

- :warning: **DO NOT** add solutions that are similar to any existing solutions. If you think it is **_similar but better_**, then try to merge (or replace) the existing similar solution.
- Add an explanation of your solution.
- Categorize the solution in one of the following categories &mdash; **Basic**, **Intermediate** and **Advanced**. :traffic_light:
- Please add your username only if you have added any **relevant main contents**. (:warning: **_DO NOT_** _remove any existing usernames_)

> See :point_right: [**`Wiki Challenge Solution Template`**](Wiki-Template-Challenge-Solution) for reference.
