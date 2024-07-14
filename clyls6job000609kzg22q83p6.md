---
title: "Leetcode 151: Reverse Words in a String"
datePublished: Sun Jul 14 2024 16:39:29 GMT+0000 (Coordinated Universal Time)
cuid: clyls6job000609kzg22q83p6
slug: leetcode-151-reverse-words-in-a-string
tags: code, algorithms, javascript, leetcode, two-pointers

---

We need to reverse the order of words in a given string.

### Code

```javascript
const reverse_words = (string) => {
  const string_trim = string.trim();
  const string_array = string_trim.split(/\s+/);
  const string_reverse = string_array.reverse();
  const string_join = string_reverse.join(" ");

  return string_join;
};

// Example
console.log(reverse_words("  the sky is blue  ")); // blue is sky the
console.log(reverse_words("hello world!")); // world! hello
console.log(reverse_words("a good   example")); // example good a
```

### Explanation

* **Trim the input string** to remove leading and trailing whitespace.
    
* **Split the string** into words using spaces as the delimiter.
    
* **Filter out empty words** to handle multiple spaces between words.
    
* **Reverse the array** of words.
    
* **Join the array** back into a string with a single space between each word.
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><code>split(/\s+/)</code>: Splits the string into an array of words. The regular expression <code>\s+</code> matches one or more whitespace characters, effectively handling multiple spaces between words.</div>
</div>

### Code: Using Two Pointer

```javascript
const reverse_words = (string) => {
  const string_trim = string.trim();
  const string_array = string_trim.split(/\s+/);

  let left = 0;
  let right = string_array.length - 1;
  while (left < right) {
    [string_array[left], string_array[right]] = [
      string_array[right],
      string_array[left],
    ];
    left++;
    right--;
  }

  const string_join = string_array.join(" ");

  return string_join;
};

// Example
console.log(reverse_words("  the sky is blue  ")); // blue is sky the
console.log(reverse_words("hello world!")); // world! hello
console.log(reverse_words("a good   example")); // example good a
```

### Explanation

* Initialize two pointers, `left` starting at the beginning of the array and `right` starting at the end.
    
* Swap the elements at `left` and `right` until the two pointers meet in the middle.
    
* Increment `left` and decrement `right` after each swap.
    

###