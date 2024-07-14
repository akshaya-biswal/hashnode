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

### Explanation:

1. **Vowel Set**: Create a set containing all the vowels (both uppercase and lowercase).
    
2. **String to Array**: Convert the string to an array of characters for easier manipulation.
    
3. **Two Pointers**: Initialize two pointers, `left` at the start of the array and `right` at the end.
    
4. **Pointer Movement**:
    
    * If the character at the `left` pointer is not a vowel, move the `left` pointer to the right.
        
    * If the character at the `right` pointer is not a vowel, move the `right` pointer to the left.
        
    * If both pointers point to vowels, swap the characters and move both pointers towards the center.
        
5. **Join Array to String**: After processing, join the array back into a string and return it.
    

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