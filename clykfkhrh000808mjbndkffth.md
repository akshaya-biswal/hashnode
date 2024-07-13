---
title: "Leetcode - 345. Reverse Vowels of a String"
datePublished: Sat Jul 13 2024 17:58:39 GMT+0000 (Coordinated Universal Time)
cuid: clykfkhrh000808mjbndkffth
slug: leetcode-345-reverse-vowels-of-a-string
tags: javascript, string, leetcode, two-pointers

---

* In this article, we will talk about a JavaScript function called `reverseVowels`. This function takes a string and reverses the vowels in it.
    
* We will use the `Two Pointers` here.
    

### Code

```javascript
const vowels = "aeiouAEIOU";

const reverseVowels = (string) => {
  const stringArray = string.split("");
  let left = 0;
  let right = string.length - 1;

  while (left < right) {
    if (!vowels.includes(stringArray[left])) {
      left++;
    } else if (!vowels.includes(stringArray[right])) {
      right--;
    } else {
      [stringArray[left], stringArray[right]] = [
        stringArray[right],
        stringArray[left],
      ];
      left++;
      right--;
    }
  }
  return stringArray.join("");
};

console.log(reverseVowels("hello")); // holle
console.log(reverseVowels("leetcode")); // leotcede
```

### Step-by-Step Explanation

* we convert the input string into an array of characters. This makes it easier to swap characters.
    
* We initialize two pointers, `left` at the beginning of the array and `right` at the end.
    
* We use a `while` loop to iterate as long as `left` is less than `right`.
    
* Inside the loop, we first check if the character at the `left` pointer is not a vowel. If it's not, we move the `left` pointer to the right.
    
* Similarly, we check if the character at the `right` pointer is not a vowel. If it's not, we move the `right` pointer to the left.
    
* If both characters at `left` and `right` pointers are vowels, we swap them. Then, we move both pointers towards the center.
    
* After the loop finishes, we convert the array back to a string and return it.
    

### Here’s a simple diagram to visualize the process:

```javascript
Input String:  "hello"
Initial Array: ['h', 'e', 'l', 'l', 'o']
Pointers:      L->'h'       R->'o'

1st Check: 'h' is not a vowel, move L
Pointers:  L->'e'           R->'o'

2nd Check: 'e' and 'o' are vowels, swap
Array:     ['h', 'o', 'l', 'l', 'e']
Move both pointers
Pointers:  L->'l'           R->'l'

3rd Check: L meets R, stop
Output String: "holle"
```