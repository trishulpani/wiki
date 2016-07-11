# Algorithm Caesars Cipher

:triangular_flag_on_post: Remember to use [**`Read-Search-Ask`**](FreeCodeCamp-Get-Help) if you get stuck. Try to pair program :busts_in_silhouette: and write your own code :pencil:

### :checkered_flag: Problem Explanation:

- You need to write a function, which will take a string encoded with _Caesar cipher_ as a parameter and decode it.
- The one used here is ROT13 where the value of the letter is shifted by 13 places. e.g. 'A' ↔ 'N', 'T' ↔ 'G'.
- You have to shift it back 13 positions, such that 'N' ↔ 'A'.

#### Relevant Links

- [String.prototype.charCodeAt](JS-String-Prototype-CharCodeAt)
- [String.fromCharCode](String.fromCharCode)

## :speech_balloon: Hint: 1

Use _String.charCodeAt()_ to convert the English character to ASCII.

> _try to solve the problem now_

## :speech_balloon: Hint: 2

Use _String.fromCharCode()_ to convert ASCII to English character.

> _try to solve the problem now_

## :speech_balloon: Hint: 3

Leave anything that doesn't come between A-Z as it is.

> _try to solve the problem now_

## Spoiler Alert!

![687474703a2f2f7777772e796f75726472756d2e636f6d2f796f75726472756d2f696d616765732f323030372f31302f31302f7265645f7761726e696e675f7369676e5f322e676966.gif](https://files.gitter.im/FreeCodeCamp/Wiki/nlOm/thumb/687474703a2f2f7777772e796f75726472756d2e636f6d2f796f75726472756d2f696d616765732f323030372f31302f31302f7265645f7761726e696e675f7369676e5f322e676966.gif)

**Solution ahead!**

## :beginner: Basic Code Solution:

```javascript
function rot13(str) {
  // Split str into a character array
  return str.split('')
  // Iterate over each character in the array
    .map.call(str, function(char) {
      // Convert char to a character code
      x = char.charCodeAt(0);
      // Checks if character lies between A-Z
      if (x < 65 || x > 90) {
        return String.fromCharCode(x);  // Return un-converted character
      }
      //N = ASCII 78, if the character code is less than 78, shift forward 13 places
      else if (x < 78) {
        return String.fromCharCode(x + 13);
      }
      // Otherwise shift the character 13 places backward
      return String.fromCharCode(x - 13);
    }).join('');  // Rejoin the array into a string
}
```

:rocket: [Run Code](https://repl.it/CLjU/38)

### Code Explanation:

- A string variable `nstr` is declared and initialized to store the decoded string.
- The for loop is used to loop through each character of the input string.
- If the character is not uppercase English alphabets(i.e. its ascii doesn't lie between 65 and 91 ), we'll leave it as it is and [continue](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/continue) with next iteration.
- If it's the uppercase English alphabet, we'll subtract 13 from it's ascii code.
- If the ascii code is less than 78, it'll get out of range when subtracted by 13 so we'll add 26 (number of letters in English alphabets) to it so that after A it'll go back to Z. e.g. M(77) ↔ 77-13 = 64(Not an English alphabet) +26 = 90 ↔ Z(90).

#### Relevant Links

- [Array.prototype.map](JS-Array-Prototype-Map)
- [String.prototype.split](JS-String-Prototype-Split)
- [Array.prototype.join](JS-Array-Prototype-Join)

## :sunflower: Intermediate Code Solution:

```javascript
// Solution with Regular expression and Array of ASCII character codes
function rot13(str) {
  var rotCharArray = [];
  var regEx = /[A-Z]/ ;
  str = str.split("");
  for (var x in str) {
    if (regEx.test(str[x])) {
      // A more general approach
      // possible because of modular arithmetic
      // and cyclic nature of rot13 transform
      rotCharArray.push((str[x].charCodeAt() - 65 + 13) % 26 + 65);
    } else {
      rotCharArray.push(str[x].charCodeAt());
    }
  }
  str = String.fromCharCode.apply(String, rotCharArray);
  return str;
}

// Change the inputs below to test
rot13("LBH QVQ VG!");
```

### Code Explanation:

- An empty array is created in a variable called `rotCharArray` to store the character codes.
- The `regEx` variable stores a regular expression for all uppercase letters from A to Z.
- We split `str` into a character array and then use a for loop to loop through each character in the array.
- Using an if statement, we test to see if the string only contains uppercase letters from A to Z.
- If it returns true, we use the `charCodeAt()` function and rot13 transformation to return the correct value, otherwise we return the initial value.
- We then return the string with the character codes from the `rotCharArray` variable.

#### Relevant Links

- [Function.apply](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)
- [Regex](JS-Regex-Resources)
- [Regex.test](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test)

:rocket: [Run Code](https://repl.it/CLjU/39)

## :rotating_light: Advanced Code Solution:

```javascript
function rot13(str) { // LBH QVQ VG!
  return str.replace(/[A-Z]/g, (L) => String.fromCharCode(65 + (L.charCodeAt(0) - 65 + 13) % 26));
}
```

### Code Explanation:

- `String.prototype.replace` [function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace) lets you transform a `String` based on some pattern match (defined by a regular expression), and the [transformation function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace#Specifying_a_function_as_a_parameter) (which is applied to each of the pattern matches).
- [Arrow function](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/Arrow_functions) syntax is used to write the function parameter to `replace()`.
- `L` represents a single unit, from every pattern match with `/[A-Z]/g` - which is every uppercase letter in the alphabet, from `A` to `Z`, present in the string.
- The arrow function applies the `rot13` transform on every uppercase letter from English alphabet present in the given string.

#### Relevant Links

- [String.prototype.replace](JS-String-Prototype-Replace)

### :trophy: Credits:

If you found this page useful, you may say thanks to the contributors by copying and pasting the following line in the main chat:

**`Thanks @anuragaryan @SaintPeter @vaskezu @abhisekp for your help with Algorithm: Caesar's Cipher`**

## :clipboard: NOTE TO CONTRIBUTORS:

- :warning: **DO NOT** add solutions that are similar to any existing solutions. If you think it is **_similar but better_**, then try to merge (or replace) the existing similar solution.
- Add an explanation of your solution.
- Categorize the solution in one of the following categories -- **Basic**, **Intermediate** and **Advanced**. :traffic_light:
- Please add your username only if you have added any **relevant main contents**. (:warning: **_DO NOT_** _remove any existing usernames_)

> See :point_right: [**`Wiki Challenge Solution Template`**](Wiki-Template-Challenge-Solution) for reference.
