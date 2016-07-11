# Challenge Word Blanks

:triangular_flag_on_post: Remember to use [**`Read-Search-Ask`**](FreeCodeCamp-Get-Help) if you get stuck. Try to pair program :busts_in_silhouette: and write your own code :pencil:

### :checkered_flag: Problem Explanation:

We will now use our knowledge of strings to build a **Mad Libs** style word game we're calling "Word Blanks". You will create an (optionally humorous) "Fill in the Blanks" style sentence.

You will need to use string operators to build a new string, **result**, using the provided variables: **myNoun**, **myAdjective**, **myVerb**, and **myAdverb**.

You will also need to use additional strings, which will not change, and must be in between all of the provided words. The output should be a complete sentence.

We have provided a framework for testing your results with different words. The tests will run your function with several different inputs to make sure all of the provided words appear in the output, as well as your extra strings.

- Change the code below `//Your Code here` and up to `//Change this line`.
- Take note that you are editing the inside of the `wordBlanks()` function.
- You will have basically created a sentence with the provided string variables.

#### Relevant Links

- [Mad Libs](https://en.wikipedia.org/wiki/Mad_Libs)
- [Challenge: Constructing Strings with Variables](http://www.freecodecamp.com/challenges/constructing-strings-with-variables)
- [Challenge: Concatenating Strings with Plus Operator](http://www.freecodecamp.com/challenges/concatenating-strings-with-plus-operator)
- [Challenge: Concatenating Strings with the Plus Equals Operator](http://www.freecodecamp.com/challenges/concatenating-strings-with-the-plus-equals-operator)

## :speech_balloon: Hint: 1

`+` can be used for _concatenating_ strings.

> _try to solve the problem now_

## :speech_balloon: Hint: 2

Just as you can chain strings by concatenating, you can assign them to an existing variable instead of a new one.

> _try to solve the problem now_

## :speech_balloon: Hint: 3

`+=` will allow you to use an existing variable, a string type in this case. Remember to add your own **non-letters** in between each variable.

> _try to solve the problem now_

## Spoiler Alert!

![687474703a2f2f7777772e796f75726472756d2e636f6d2f796f75726472756d2f696d616765732f323030372f31302f31302f7265645f7761726e696e675f7369676e5f322e676966.gif](https://files.gitter.im/FreeCodeCamp/Wiki/nlOm/thumb/687474703a2f2f7777772e796f75726472756d2e636f6d2f796f75726472756d2f696d616765732f323030372f31302f31302f7265645f7761726e696e675f7369676e5f322e676966.gif)

**Solution ahead!**

## :beginner: Basic Code Solution:

```javascript
function wordBlanks(myNoun, myAdjective, myVerb, myAdverb) {
    var result = "";
    // Your code below this line
    result+= "My "+myAdjective+" "+myNoun+" "+myVerb+" very "+myAdverb+".";

    // Your code above this line
  return result;
}

// Change the words here to test your function
wordBlanks("dog", "big", "ran", "quickly");
```

**Example Run**

- Test `wordBlanks("dog", "big", "ran", "quickly");` runs.
- Variable **result** is declared with an empty string `""`.
- **result** will be changed with a new string composed of the concatenated strings "dog", "big", "ran", "quickly" through the variables **myNoun**, **myAdjective**, **myVerb**, **myAdverb** respectively; the order is changed and whitespace added.
- **result** is returned.

### Code Explanation:

- Use **result** to concatenate the given variables.
- Separate words with whitespace and appropriate words to form the full sentence.

### :trophy: Credits:

If you found this page useful, you may say thanks to the contributors by copying and pasting the following line in the main chat:

**`Thanks @Rafase282 for your help with Checkpoint: Word Blanks`**

## :clipboard: NOTES FOR CONTRIBUTIONS:

- :warning: **DO NOT** add solutions that are similar to any existing solutions. If you think it is **_similar but better_**, then try to merge (or replace) the existing similar solution.
- Add an explanation of your solution.
- Categorize the solution in one of the following categories &mdash; **Basic**, **Intermediate** and **Advanced**. :traffic_light:
- Please add your username only if you have added any **relevant main contents**. (:warning: **_DO NOT_** _remove any existing usernames_)

> See :point_right: [**`Wiki Challenge Solution Template`**](Wiki-Template-Challenge-Solution) for reference.
