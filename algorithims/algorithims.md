# Intro

## Basic

### Reverse a String

- You may need to turn the string into an array before you can reverse it.

```javascript
function reverseString(str) {
  let s = "";
  for (let i = str.length - 1; i >= 0; i--) {
    s += str[i];
  }
  return s;
}

reverseString("hello");
```

- Using recursion with `substr()` and `charat()`

```javascript
function reverseString(str) {
  if (!str) {
    return "";
  }

  return reverseString(str.substr(1)) + str.charAt(0);
}

reverseString("hello");
```

### Reverse a Number

- Using while loop

```javascript
function reverseString(number) {
  let s = "";

  while (number > 0) {
    s += number % 10;
    number = parseInt(number / 10);
  }
  return s;
}
console.log(reverseString(12345789));
```

- Using recursion

```javascript
var sum = 0;
function reverseString(str) {
  if (str <= 0) {
    return "";
  }
  sum = sum * 10 + (str % 10);
  reverseString(parseInt(str / 10));

  return sum;
}
console.log(reverseString(12345));
```

### Factorialize a Number

- Return the factorial of the provided integer.

- If the integer is represented with the letter n, a factorial is the product of all positive integers less than or equal to n.

- Factorials are often represented with the shorthand notation n!

```
For example: 5! = 1 * 2 * 3 * 4 * 5 = 120
```

```javascript
function factorialize(num) {
  if (num <= 0) {
    return 1;
  }

  return factorialize(num - 1) * num;
}

factorialize(5);
```

### Find the Longest Word in a String

- Use foorloop

```javascript
function findLongestWordLength(str) {
  let chars = str.split(" ");
  let maxItem = "";
  for (let i = 0; i < chars.length; i++) {
    if (maxItem.length < chars[i].length) {
      maxItem = chars[i];
    }
  }
  console.log(maxItem);
  return maxItem.length;
}
- Use sorting

findLongestWordLength("The quick brown fox jumped over the lazy dog");
```

### Return Largest Numbers in Arrays

- Return an array consisting of the largest number from each provided sub-array. For simplicity, the provided array will contain exactly 4 sub-arrays.
- Solution 1: By loop

  ```javascript
  function largestOfFour(arr) {
    const arrays = [];
    for (let i = 0; i < arr.length; i++) {
      let currentArr = arr[i];
      let largestNumber;
      let subIndex = 0;
      let currentArrLength = currentArr.length;
      while (subIndex <= currentArrLength) {
        if (!largestNumber) {
          largestNumber = currentArr[0];
          continue;
        }
        if (largestNumber < currentArr[subIndex]) {
          largestNumber = currentArr[subIndex];
        }
        subIndex += 1;
      }
      arrays.push(largestNumber);
    }
    console.log(arrays);
    return arrays;
  }

  largestOfFour([
    [17, 23, 25, 12],
    [25, 7, 34, 48],
    [4, -10, 18, 21],
    [-72, -3, -17, -10],
  ]);
  ```

- By Map-reduce

```javascript
function largestOfFour(arr) {
  return arr.map((res) => {
    return res.reduce((accumulator, currentValue) => {
      if (accumulator < currentValue) {
        return currentValue;
      } else {
        return accumulator;
      }
    });
  });
}
```

### Confirm the Ending

```javascript
function confirmEnding(str, target) {
  if (str.substr(-target.length).indexOf(target) > -1) {
    return true;
  }
  return false;
}

confirmEnding("Connor", "n");
```

## Boo whoPassed

Check if a value is classified as a boolean primitive. Return true or false.

```javascript
function booWho(bool) {
  return typeof bool == "boolean";
}

booWho(null);
```

## Title Case a Sentence

- Return the provided string with the first letter of each word capitalized. Make sure the rest of the word is in lower case.

```javascript
function titleCase(str) {
  var result = str
    .toLowerCase()
    .split(" ")
    .map((res) => {
      return res.replace(res[0], res[0].toUpperCase());
    });
  return result.join(" ");
}

titleCase("I'm a little tea pot");
```

## Slice and Splice

- You are given two arrays and an index.

- Copy each element of the first array into the second array, in order.

- Begin inserting elements at index n of the second array.

```javascript
function frankenSplice(arr1, arr2, n) {
  var newArr = [...arr2];
  newArr.splice(n, 0, ...arr1);
  return newArr;
}

frankenSplice(["claw", "tentacle"], ["head", "shoulders", "knees", "toes"], 2);
```

## Falsy bouncer

- Remove all falsy values from an array.

- Falsy values in JavaScript are false, null, 0, "", undefined, and NaN.

```javascript
function bouncer(arr) {
  return arr.filter((res) => {
    if (res) {
      return res;
    }
  });
}

bouncer([7, "ate", "", false, 9]);
```

## Where do I Belong

- Return the lowest index at which a value (second argument) should be inserted into an array (first argument) once it has been sorted. The returned value should be a number.

- For example, getIndexToIns([1,2,3,4], 1.5) should return 1 because it is greater than 1 (index 0), but less than 2 (index 1).

```javascript
function getIndexToIns(arr, num) {
  var sorted = arr.sort((a, b) => {
    return a - b;
  });

  for (let i = 0; i < sorted.length; i++) {
    if (num <= sorted[i]) {
      console.log(i);
      return i;
    }
  }

  return sorted.length;
}

getIndexToIns([40, 60, 20], 50);
```

## Mutations

- Return true if the string in the first element of the array contains all of the letters of the string in the second element of the array.

- For example, ["hello", "Hello"], should return true because all of the letters in the second string are present in the first, ignoring case.

- The arguments ["hello", "hey"] should return false because the string "hello" does not contain a "y".

```javascript
function mutation(arr) {
  var v1 = arr[0].toLowerCase();
  var v2 = arr[1].toLowerCase();
  for (let i = 0; i < v2.length; i++) {
    if (v1.indexOf(v2[i]) == -1) {
      return false;
    }
  }
  return true;
}

mutation(["hello", "Hello"]);
```

## Chunky Monkey

- Write a function that splits an array (first argument) into groups the length of size (second argument) and returns them as a two-dimensional array.

```javascript
function chunkArrayInGroups(arr, size) {
  var mularr = [];
  var leg = arr.length / size;
  for (let i = 0; i < leg; i++) {
    mularr.push(arr.splice(0, size));
  }
  return mularr;
}

chunkArrayInGroups(["a", "b", "c", "d"], 2);
```

## Sum All Numbers in a Range

- We'll pass you an array of two numbers. Return the sum of those two numbers plus the sum of all the numbers between them. The lowest number will not always come first.

- For example, sumAll([4,1]) should return 10 because sum of all the numbers between 1 and 4 (both inclusive) is 10.

- Solution 1: using max and min

```javascript
function sumAll(arr) {
  let min = arr[0];
  let max = arr[1];
  if (min - max > 0) {
    [min, max] = [arr[1], arr[0]];
  }
  let sum = 0;
  for (let i = min; i <= max; i++) {
    sum += i;
  }
  return sum;
}

sumAll([1, 4]);
```

- Solution 2: Recursion

```javascript
function sumAll(arr) {
  let first = arr[0];
  let last = arr[1];
  let step = first - last > 0 ? -1 : 1;

  if (first === last) {
    return first;
  }

  return sumAll([step + first, last]) + first;
}

sumAll([4, 1]);
```

- Solution 3: using math formular `Using Arithmetic Progression summing formula`
  sum of a continuous range is `(startNum + endNum) * numCount / 2`.

```javascript
function sumAll(arr) {
  let first = arr[0];
  let last = arr[1];

  let numCount = Math.abs(arr[0] - arr[1]) + 1;
  // Using Arithmetic Progression summing formula
  return ((first + last) * numCount) / 2;
}

sumAll([4, 1]);

console.log(sumAll([4, 1]));
```

## Diff Two Arrays

- Compare two arrays and return a new array with any items only found in one of the two given arrays, but not both. In other words, return the symmetric difference of the two arrays.
- Solution 1: Imperative

```javascript
function diffArray(arr1, arr2) {
  var newArr = [];

  let diff = function (first, last) {
    for (let i = 0; i < first.length; i++) {
      if (last.indexOf(first[i]) === -1) {
        newArr.push(first[i]);
      }
    }
  };
  diff(arr1, arr2);
  diff(arr2, arr1);
  return newArr;
}

diffArray([1, 2, 3, 5], [1, 2, 3, 4, 5]);
```

- Solution 2: merged, filter and include

```javascript
function diffArray(arr1, arr2) {
  var newArr = [];

  newArr = arr1.concat(arr2).filter((res) => {
    return !arr1.includes(res) || !arr2.includes(res);
  });
  console.log(newArr);
  return newArr;
}

diffArray([1, 2, 3, 5, 6], [1, 2, 3, 4, 5]);
```

- Solution 3: imperative with ES6

```javascript
function diffArray(arr1, arr2) {
  var newArr = [];

  var diff = function (arr1, arr2) {
    return arr1.filter((res) => {
      return arr2.indexOf(res) === -1;
    });
  };
  newArr = [...diff(arr1, arr2), ...diff(arr2, arr1)];
  console.log(newArr);
  return newArr;
}

diffArray([1, 2, 3, 5, 6], [1, 2, 3, 4, 5]);
```

## Seek and Destroy

- You will be provided with an initial array (the first argument in the destroyer function), followed by one or more arguments. Remove all elements from the initial array that are of the same value as these arguments.

- Note: You have to use the arguments object.

- Solution 1: Using spread, filter and include

```javascript
function destroyer(arr1, ...args) {
  var arr = arr1.filter((res) => {
    return !args.includes(res);
  });
  return arr;
}
-destroyer([1, 2, 3, 1, 2, 3], 2, 3);
```

- Solution 2: Using Array.protocol.slice with the `Boolean` object as a `filter` for any `null's` created by the delete operator.

```javascript
function destroyer(arr) {
  var args = Array.prototype.slice.call(arguments);

  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < args.length; j++) {
      if (arr[i] === args[j]) {
        delete arr[i];
      }
    }
  }
  return arr.filter(Boolean);
}

destroyer([1, 2, 3, 1, 2, 3], 2, 3);
```

## Wherefore art thou

- Make a function that looks through an array of objects (first argument) and returns an array of all objects that have matching name and value pairs (second argument). Each name and value pair of the source object has to be present in the object from the collection if it is to be included in the returned array.

- For example, if the first argument is `[{ first: "Romeo", last: "Montague" }, { first: "Mercutio", last: null }, { first: "Tybalt", last: "Capulet" }]`, and the second argument is `{ last: "Capulet" }`, then you must return the third object from the array (the first argument), because it contains the name and its value, that was passed on as the second argument.

```javascript
function whatIsInAName(collection, source) {
  var arr = [];
  // Only change code below this line
  for (let i = 0; i < collection.length; i++) {
    let item = collection[i];
    let valid = true;
    for (let key in source) {
      if (item[key] !== source[key]) {
        valid = false;
      }
    }
    if (valid) {
      arr.push(item);
    }
  }
  // Only change code above this line
  return arr;
}

whatIsInAName(
  [
    { first: "Romeo", last: "Montague" },
    { first: "Mercutio", last: null },
    { first: "Tybalt", last: "Capulet" },
  ],
  { last: "Capulet" }
);
```

- Refactor 1

```javascript
function whatIsInAName(collection, source) {
  var arr = [];

  // Only change code below this line
  arr = collection.filter((item) => {
    for (let key in source) {
      if (item[key] !== source[key]) {
        return false;
      }
    }
    return true;
  });
  // Only change code above this line
  return arr;
}

whatIsInAName(
  [
    { first: "Romeo", last: "Montague" },
    { first: "Mercutio", last: null },
    { first: "Tybalt", last: "Capulet" },
  ],
  { last: "Capulet" }
);
```

- Refactor 2:

```javascript
function whatIsInAName(collection, source) {
  var arr = [];
  var keys = Object.keys(source);
  // Only change code below this line
  arr = collection.filter((item) => {
    return keys.every((key) => {
      return item.hasOwnProperty(key) && source[key] === item[key];
    });
  });
  // Only change code above this line
  return arr;
}

whatIsInAName(
  [{ apple: 1, bat: 2 }, { apple: 1 }, { apple: 1, bat: 2, cookie: 2 }],
  { apple: 1, cookie: 2 }
);
```

## Spinal Tap Case

- Convert a string to spinal case. Spinal case is all-lowercase-words-joined-by-dashes.
- My solution

```javascript
function spinalCase(str) {
  return str
    .split(/(?=[A-Z])|\s|_|-/)
    .join("-")
    .toLowerCase();
}

spinalCase("The_Andy_Griffith_Show");
```

- Solution 1:

```javascript
function spinalCase(str) {
  // Create a variable for the white space and underscores.
  var regex = /\s+|_+/g;

  // Replace low-upper case to low-space-uppercase
  str = str.replace(/([a-z])([A-Z])/g, "$1 $2");
  // Replace space and underscore with -
  return str.replace(regex, "-").toLowerCase();
}

spinalCase("thisIsSpinalTap");
```

## Pig Latin

- Pig Latin is a way of altering English Words. The rules are as follows:

- If a word begins with a consonant, take the first consonant or consonant cluster, move it to the end of the word, and add "ay" to it.

- If a word begins with a vowel, just add "way" at the end.
- My solution

```javascript
function translatePigLatin(str) {
  var unVowel = str.match(/^[^aoeui]+/gi) || "";
  const suffix = unVowel ? "ay" : "way";
  return str.replace(unVowel, "").concat(unVowel + suffix);
}

translatePigLatin("algorithm");
```

- Solution 1: recursion

```javascript
function translatePigLatin(str, charAt = 0) {
  var vowel = ["a", "o", "e", "u", "i"];
  var suffix = "";

  if (vowel.includes(str[0])) {
    if (charAt == 0) {
      return str + "way";
    } else {
      return str + "ay";
    }
  } else {
    if (charAt == str.length) {
      return str + "ay";
    } else {
      return translatePigLatin(str.slice(1) + str[0], charAt + 1);
    }
  }
}
translatePigLatin("consonant");
```

## Search and Replace

- Perform a search and replace on the sentence using the arguments provided and return the new sentence.

- First argument is the sentence to perform the search and replace on.

- Second argument is the word that you will be replacing (before).

- Third argument is what you will be replacing the second argument with (after).

- Note

  - Preserve the case of the first character in the original word when you are replacing it. For example if you mean to replace the word "Book" with the word "dog", it should be replaced as "Dog"

- My solution:

```javascript
function myReplace(str, before, after) {
  let beforeChar = before.charAt(0);
  let afterChar = after.charAt(0);
  if (beforeChar == beforeChar.toUpperCase()) {
    after = after.replace(afterChar, afterChar.toUpperCase());
  } else {
    after = after.replace(afterChar, afterChar.toLowerCase());
  }
  return str.replace(before, after);
}

myReplace("He is Sleeping on the couch", "Sleeping", "sitting");
```

- Solution 1: using indexOf()

```javascript
function myReplace(str, before, after) {
  var index = str.indexOf(before);

  if (str[index] == str[index].toUpperCase()) {
    after = after.charAt(0).toUpperCase() + after.slice(1);
  } else {
    after = after.charAt(0).toLowerCase() + after.slice(1);
  }
  return str.replace(before, after);
}

myReplace("Let us go to the store", "store", "mall");
```

- Solution 2: using regex `/^[A-Z]/`

```javascript
function myReplace(str, before, after) {
  if (/^[A-Z]/.test(before)) {
    after = after.charAt(0).toUpperCase() + after.slice(1);
  } else {
    after = after.charAt(0).toLowerCase() + after.slice(1);
  }
  return str.replace(before, after);
}

myReplace("Let us go to the store", "store", "mall");
```

- Solution 3: using split and forloop

```javascript
function myReplace(str, before, after) {
  function applyCasing(source, target) {
    let sourceArr = source.split("");
    let targetArr = target.split("");

    for (let i = 0; i < Math.min(sourceArr.length, targetArr.length); i++) {
      if (/^[A-Z]/.test(sourceArr[i])) {
        targetArr[i] = targetArr[i].toUpperCase();
      } else {
        targetArr[i] = targetArr[i].toLowerCase();
      }
    }
    return targetArr.join("");
  }
  return str.replace(before, applyCasing(before, after));
}

myReplace("Let us go to the store", "store", "mall");
```

- Solution 3: create helper function

```javascript
String.prototype.capitalize = function () {
  return this[0].toUpperCase() + this.slice(1);
};

function myReplace(str, before, after) {
  function testCase(str, case1) {
    if (case1) {
      return setTest(str, case1);
    } else {
      return getTest(str);
    }

    function getTest(str) {
      if (str == str.toUpperCase()) {
        return "toUpperCase";
      } else if (str == str.toLowerCase()) {
        return "toLowerCase";
      } else if (str == str.capitalize()) {
        return "capitalize";
      } else {
        return "normal";
      }
    }
    function setTest(str, cas) {
      if (cas == "toUpperCase") {
        return str.toUpperCase();
      } else if (cas == "toLowerCase") {
        return str.toLowerCase();
      } else if (cas == "capitalize") {
        return str.capitalize();
      } else {
        return str;
      }
    }
  }
  return str.replace(before, testCase(after, testCase(before)));
}

myReplace("He is Sleeping on the couch", "Sleeping", "sitting");
```

## DNA Pairing

- The DNA strand is missing the pairing element. Take each character, get its pair, and return the results as a 2d array.

- Base pairs are a pair of AT and CG. Match the missing element to the provided character.

- Return the provided character as the first element in each array.

- For example, for the input GCG, return [["G", "C"], ["C","G"],["G", "C"]]

- The character and its pair are paired up in an array, and all the arrays are grouped into one encapsulating array.
- My solution

```javascript
function pairElement(str) {
  let arr = str.split("");
  let newArr = [];
  for (let i = 0; i < arr.length; i++) {
    switch (arr[i]) {
      case "A":
        newArr.push(["A", "T"]);
        break;
      case "T":
        newArr.push(["T", "A"]);
        break;
      case "C":
        newArr.push(["C", "G"]);
        break;
      case "G":
        newArr.push(["G", "C"]);
        break;
    }
  }
  return newArr;
}

pairElement("ATCGA");
```

- Using dictionary mapping:

```javascript
function pairElement(str) {
  const dir = {
    A: "T",
    T: "A",
    C: "G",
    G: "C",
  };
  const newArr = str.split("").map((res) => {
    return [res, dir[res]];
  });
  console.log(newArr);
  return newArr;
}

pairElement("ATCGA");
```

## Missing letters

- Find the missing letter in the passed letter range and return it.

- If all letters are present in the range, return undefined.

- My solution:

```javascript
function fearNotLetter(str) {
  let firstCode = str.charCodeAt(0);

  for (let i = 0; i < str.length; i++) {
    let itemCode = str.charCodeAt(i);
    if (itemCode != firstCode + i) {
      return String.fromCharCode(firstCode + i);
    }
  }
}

fearNotLetter("abce");
```

- Solution 1: using Map function

```javascript
function fearNotLetter(str) {
  let compare = str.charCodeAt(0),
    missing;

  str.split("").map((res, index) => {
    if (str.charCodeAt(index) === compare) {
      compare++;
    } else {
      missing = String.fromCharCode(compare);
    }
  });
  return missing;
}

fearNotLetter("abce");
```

- Solution 3: using selection loop

```javascript
function fearNotLetter(str) {
  for (let i = 1; str.length; i++) {
    if (str.charCodeAt(i) - str.charCodeAt(i - 1) > 1) {
      return String.fromCharCode(str.charCodeAt(i - 1) + 1);
    }
  }
}

fearNotLetter("abce");
```

## Sorted Union

- Write a function that takes two or more arrays and returns a new array of unique values in the order of the original provided arrays.

- In other words, all values present from all arrays should be included in their original order, but with no duplicates in the final array.

- The unique numbers should be sorted by their original order, but the final array should not be sorted in numerical order.
- Solution 1: using map and filter

```javascript
function uniteUnique(...arr) {
  var newArr = [];
  arr.map((res) => {
    var diffs = res.filter((item) => {
      return !newArr.includes(item);
    });
    newArr.push(...diffs);
  });
  return newArr;
}

uniteUnique([1, 3, 2], [5, 2, 1, 4], [2, 1]);
```

- Solution 1: using reduce and concat

```javascript
function uniteUnique(...arr) {
  var newArr = arr.reduce((arr1, arr2) => {
    console.log(arr1);
    return arr1.concat(
      arr2.filter((res) => {
        return !arr1.includes(res);
      })
    );
  });
  return newArr;
}

uniteUnique([1, 3, 2], [5, 2, 1, 4], [2, 1]);
```

- Solution 2: using Set

```javascript
function uniteUnique(...arrays) {
  //make an array out of the given arrays and flatten it (using the spread operator)
  const flatArray = [].concat(...arrays);

  // create a Set which clears any duplicates since it's a regular set and not a multiset
  return [...new Set(flatArray)];
}

// test here
uniteUnique([1, 3, 2], [5, 2, 1, 4], [2, 1]);
```

- Solution 3: using Flat and Set

```javascript
function uniteUnique(...arr) {
  return [...new Set(arr.flat())];
}

// Or as an arrow function
const uniteUnique = (...arr) => [...new Set(arr.flat())];
```

## Convert HTML Entities

- Convert the characters &, <, >, " (double quote), and ' (apostrophe), in a string to their corresponding HTML entities.

```javascript
function convertHTML(str) {
  let dic = {
    "&": "&amp;",
    "<": "&lt;",
    ">": "&gt;",
    '"': "&quot;",
    "'": "&apos;",
  };

  var str = str.replace(/[&<>"']/g, (match) => {
    return dic[match];
  });
  return str;
}

convertHTML("<>");
```

## Sum All Odd Fibonacci Numbers

- Given a positive integer num, return the sum of all odd Fibonacci numbers that are less than or equal to num.

- The first two numbers in the Fibonacci sequence are 1 and 1. Every additional number in the sequence is the sum of the two previous numbers. The first six numbers of the Fibonacci sequence are 1, 1, 2, 3, 5 and 8.

- For example, sumFibs(10) should return 10 because all odd Fibonacci numbers less than or equal to 10 are 1, 1, 3, and 5.
- Solution 1: using currentValue and previous Value

```javascript
function sumFibs(num) {
  var result = 0;

  let currentValue = 1;
  let previousValue = 0;
  while (currentValue <= num) {
    if (currentValue % 2 !== 0) {
      result += currentValue;
    }

    currentValue = currentValue + previousValue;
    previousValue = currentValue - previousValue;
  }
  return result;
}

sumFibs(1000);
```

- Solution 2: Using array unshift, filter and reduce

```javascript
function sumFibs(num) {
  if (num == 0) {
    return 0;
  }

  const arr = [1, 1];
  let nextEl = 0;

  while ((nextEl = arr[0] + arr[1]) <= num) {
    arr.unshift(nextEl);
  }

  var result = arr
    .filter((res) => res % 2 !== 0)
    .reduce((acc, res) => acc + res);
  return result;
}

sumFibs(1000);
```

## Sum All Primes

- A prime number is a whole number greater than 1 with exactly two divisors: 1 and itself. For example, 2 is a prime number because it is only divisible by 1 and 2. In contrast, 4 is not prime since it is divisible by 1, 2 and 4.

- Rewrite sumPrimes so it returns the sum of all prime numbers that are less than or equal to num.
- Solution 1: using 2 for-loops

```javascript
function sumPrimes(num) {
  if (num == 1) {
    return 0;
  }
  if (num == 2) {
    return 2;
  }

  let arr = [];

  for (let i = 2; i <= num; i++) {
    const isPrime = false;
    for (let j = 2; j < i; j++) {
      if (i % j == 0) {
        isPrime = true;
      }
    }
    if (!isPrime) {
      arr.push(i);
    }
  }
  let result = arr.reduce((a, b) => a + b);
  return result;
}

sumPrimes(10);
```

- Solution 2: using sieve of eratosthenes algorithim

```javascript
function sumPrimes(num) {
  if (num == 1) {
    return 0;
  }
  if (num == 2) {
    return 2;
  }

  let prime = [];
  let sieve = [];
  for (let i = 2; i <= num; i++) {
    if (!prime[i]) {
      sieve.push(i);
      // or let j = i*i
      for (let j = i << 1; j <= num; j = j + i) {
        prime[j] = true;
      }
    }
  }
  let result = sieve.reduce((a, b) => a + b);

  return result;
}

sumPrimes(10);
```

- Solution 3: Using helper function and while

```javascript
function sumPrimes(num) {
  let isPrime = function (number) {
    for (let i = 2; i < number; i++) {
      if (number % i == 0) {
        return false;
      }
    }
    return number !== 1 && number !== 0;
  };
  let sum = 0;
  let i = 0;
  while (i <= num) {
    if (isPrime(i)) {
      sum += i;
    }
    i++;
  }
  return sum;
}

sumPrimes(977);
```

- Solution 4: using recursion and helper function

```javascript
function sumPrimes(num) {
  let isPrime = function (number) {
    for (let i = 2; i < number; i++) {
      if (number % i == 0) {
        return false;
      }
    }
    return number !== 1 && number !== 0;
  };
  if (num == 1) {
    return 0;
  }
  if (isPrime(num)) {
    return sumPrimes(num - 1) + num;
  }
  return sumPrimes(num - 1);
}

sumPrimes(10);
```

- Solution 5: using filter and reduce then remove all non-primes

```javascript
function sumPrimes(num) {
  var arr = Array.from({ length: num + 1 })
    .map((_, index) => index)
    .slice(2);
  console.log(arr);
  let onlyPrimes = arr.filter((res) => {
    let m = res - 1;
    while (m > 1 && m >= Math.sqrt(res)) {
      if (res % m === 0) return false;
      m--;
    }
    return true;
  });

  return onlyPrimes.reduce((a, b) => a + b);
}
sumPrimes(10);
```

## Smallest Common Multiple

- Find the smallest common multiple of the provided parameters that can be evenly divided by both, as well as by all sequential numbers in the range between these parameters.

- The range will be an array of two numbers that will not necessarily be in numerical order.

- For example, if given 1 and 3, find the smallest common multiple of both 1 and 3 that is also evenly divisible by all numbers between 1 and 3. The answer here would be 6.
- Solution 1: Using the first two biggest numbers in array to compare the others with do while function

```javascript
function smallestCommons(arr) {
  arr.sort((a, b) => {
    return b - a;
  });
  var newArr = [];
  for (let i = arr[0]; i > 0; i--) {
    newArr.push(i);
  }

  let quot = 0;
  let loop = 1;
  let n;
  do {
    quot = newArr[0] * loop * newArr[1];

    for (n = 2; n < newArr.length; n++) {
      if (quot % newArr[n] !== 0) {
        break;
      }
    }
    loop++;
  } while (n !== newArr.length);

  return arr;
}
smallestCommons([1, 5]);
```

- Solution 3: Using Euclidean algorithm

```javascript
function smallestCommons(arr) {
  let findgcd = function (x, y) {
    if (y === 0) {
      return x;
    } else {
      return findgcd(y, x % y);
    }
  };
  arr.sort((a, b) => {
    return b - a;
  });
  var newArr = [];
  for (let i = arr[0]; i >= arr[1]; i--) {
    newArr.push(i);
  }
  var lcm = newArr[0];
  for (let i = 1; i < newArr.length; i++) {
    let gcd = findgcd(lcm, newArr[i]);
    lcm = (lcm * newArr[i]) / gcd;
  }
  return lcm;
}

smallestCommons([18, 23]);
```

- Solution 4: Using sum up max value if not evenly divided the other numbers

```javascript
const smallestCommons = (arr) => {
  let max = Math.max(...arr);
  let min = Math.min(...arr);
  // Initially the solution is assigned to the highest value of the array
  let sol = max;

  for (let i = max - 1; i >= min; i--) {
    if (sol % i !== 0) {
      sol += max;
      i = max;
    }
  }
  console.log(sol);
  return sol;
};

smallestCommons([1, 6]);
```

## Drop it

- Given the array arr, iterate through and remove each element starting from the first element (the 0 index) until the function func returns true when the iterated element is passed through it.

- Then return the rest of the array once the condition is satisfied, otherwise, arr should be returned as an empty array.
- Solution 1: using for-loop

```javascript
function dropElements(arr, func) {
  for (let i = 0; arr.length; i++) {
    if (func(arr[0])) {
      break;
    } else {
      arr.shift();
    }
  }
  return arr;
}

dropElements([1, 2, 3], function (n) {
  return n > 2;
});
```

- Solution 2: using while

```javascript
function dropElements(arr, func) {
  while (arr.length > 0 && !func(arr[0])) {
    arr.shift();
  }
  return arr;
}

dropElements([1, 2, 3], function (n) {
  return n > 2;
});
```

- Solution 3: using slice

```javascript
function dropElements(arr, func) {
  arr = arr.slice(arr.findIndex(func) >= 0 ? arr.findIndex(func) : arr.length);
  return arr;
}

dropElements([1, 2, 3], function (n) {
  return n > 2;
});
```

## Steamroller

- Flatten a nested array. You must account for varying levels of nesting.
- Solution 1: using recursion and for-loop

```javascript
function steamrollArray(arr) {
  var newArr = [];
  var flatten = function (args) {
    if (!Array.isArray(args)) {
      newArr.push(args);
    } else {
      for (var item in args) {
        flatten(args[item]);
      }
    }
  };
  flatten(arr);
  return newArr;
}

steamrollArray([1, [2], [3, [[4]]]]);
```

- Solution 2: Using some and recursion

```javascript
function steamrollArray(arr) {
  let flat = [].concat(...arr);
  console.log(flat);
  return flat.some(Array.isArray) ? steamrollArray(flat) : flat;
}

steamrollArray([1, [2], [3, [[4]]]]);
```

## Binary Agents

- Return an English translated sentence of the passed binary string.

- The binary string will be space separated.
- Solution 1: using parseInt(number,2) to convert from binary to decimal

```javascript
function binaryAgent(str) {
  var arr = str.split(" ");
  var str = arr.reduce((acc, res) => {
    const decimal = parseInt(res, 2);
    return acc + String.fromCharCode(decimal);
  }, "");
  return str;
}

binaryAgent(
  "01000001 01110010 01100101 01101110 00100111 01110100 00100000 01100010 01101111 01101110 01100110 01101001 01110010 01100101 01110011 00100000 01100110 01110101 01101110 00100001 00111111"
);
```

- Solution 2: Using Math.pow(number,exponent)

```javascript
function binaryAgent(str) {
  var str = str.split(" ");
  var arr = [];
  for (let i = 0; i < str.length; i++) {
    let decimalVal = 0;
    for (let j = 0; j < str[i].length; j++) {
      if (str[i][j] == 1) {
        let pow = Math.pow(2, str[i].length - j - 1);

        decimalVal += pow;
      }
    }
    arr.push(String.fromCharCode(decimalVal));
  }
  return arr.join("");
}

binaryAgent("01000001 01110010");
```

## Everything Be True

- Check if the predicate (second argument) is truthy on all elements of a collection (first argument).

- In other words, you are given an array collection of objects. The predicate pre will be an object property and you need to return true if its value is truthy. Otherwise, return false.

- In JavaScript, truthy values are values that translate to true when evaluated in a Boolean context.

- Remember, you can access object properties through either dot notation or [] notation.

```javascript
function truthCheck(collection, pre) {
  var result = true;

  for (let i = 0; i < collection.length; i++) {
    console.log(collection[i][pre]);
    if (!collection[i][pre]) {
      result = false;
    }
  }
  return result;
}

truthCheck(
  [
    { user: "Tinky-Winky", sex: "male" },
    { user: "Dipsy", sex: "male" },
    { user: "Laa-Laa", sex: "female" },
    { user: "Po", sex: "female" },
  ],
  "sex"
);
```

## Arguments Optional

- Create a function that sums two arguments together. If only one argument is provided, then return a function that expects one argument and returns the sum.

- For example, addTogether(2, 3) should return 5, and addTogether(2) should return a function.

- Calling this returned function with a single argument will then return the sum:

```javascript
var sumTwoAnd = addTogether(2);

sumTwoAnd(3) returns 5.
```

- If either argument isn't a valid number, return undefined.
- Solution: using some and reduce function

```javascript
function addTogether() {
  let arr = [...arguments];

  if (arr.some((res) => typeof res !== "number")) {
    return undefined;
  }
  if (arr.length > 1) {
    return arr.reduce((a, b) => a + b);
  } else {
    return (n) => {
      return typeof n !== "number" ? undefined : arr[0] + n;
    };
  }
}

addTogether(2, "3");
```

## Make a Person

- Fill in the object constructor with the following methods below:

```javascript
getFirstName();
getLastName();
getFullName();
setFirstName(first);
setLastName(last);
setFullName(firstAndLast);
```

- Run the tests to see the expected output for each method. The methods that take an argument must accept only one argument and it has to be a string. These methods must be the only available means of interacting with the object.

```javascript
var Person = function (firstAndLast) {
  // Only change code below this line
  // Complete the method below and implement the others similarly
  var fullName = firstAndLast;
  this.getFullName = function () {
    return fullName;
  };
  this.getFirstName = function () {
    console.log(fullName);
    return fullName.split(" ")[0];
  };
  this.getLastName = function () {
    return fullName.split(" ")[1];
  };
  this.setFirstName = function (first) {
    fullName = first + " " + fullName.split(" ")[1];
  };
  this.setLastName = function (last) {
    fullName = fullName.split(" ")[0] + " " + last;
  };
  this.setFullName = function (firstAndLast) {
    fullName = firstAndLast;
  };
};

var bob = new Person("Bob Ross");
console.log(bob.firstName);
```

## Roman Numeral Converter

- Convert the given number into a roman numeral.

- All roman numerals answers should be provided in upper-case.
- Solution 1: using dictionary and 2 loops

```javascript
function convertToRoman(num) {
  var lookup = {
      M: 1000,
      CM: 900,
      D: 500,
      CD: 400,
      C: 100,
      XC: 90,
      L: 50,
      XL: 40,
      X: 10,
      IX: 9,
      V: 5,
      IV: 4,
      I: 1,
    },
    roman = "",
    i;
  for (let i in lookup) {
    while (num >= lookup[i]) {
      num -= lookup[i];
      roman += i;
    }
  }
  return roman;
}

convertToRoman(2);
```

- Solution 2:

```javascript
function convertToRoman(num) {
  var romans = ["I", "V", "X", "L", "C", "D", "M"],
    ints = [],
    romanNumber = [],
    numeral = "",
    i;
  while (num) {
    ints.push(num % 10);
    num = Math.floor(num / 10);
  }
  console.log(ints);
  for (i = 0; i < ints.length; i++) {
    units(ints[i]);
  }
  function units() {
    numeral = romans[i * 2];
    switch (ints[i]) {
      case 1:
        romanNumber.push(numeral);
        break;
      case 2:
        romanNumber.push(numeral.concat(numeral));
        break;
      case 3:
        romanNumber.push(numeral.concat(numeral).concat(numeral));
        break;
      case 4:
        romanNumber.push(numeral.concat(romans[i * 2 + 1]));
        break;
      case 5:
        romanNumber.push(romans[i * 2 + 1]);
        break;
      case 6:
        romanNumber.push(romans[i * 2 + 1].concat(numeral));
        break;
      case 7:
        romanNumber.push(romans[i * 2 + 1].concat(numeral).concat(numeral));
        break;
      case 8:
        romanNumber.push(
          romans[i * 2 + 1].concat(numeral).concat(numeral).concat(numeral)
        );
        break;
      case 9:
        romanNumber.push(romans[i * 2].concat(romans[i * 2 + 2]));
    }
  }
  return romanNumber.reverse().join("").toString();
}
convertToRoman(36);
```

## Caesars Cipher

- One of the simplest and most widely known ciphers is a Caesar cipher, also known as a shift cipher. In a shift cipher the meanings of the letters are shifted by some set amount.

- A common modern use is the ROT13 cipher, where the values of the letters are shifted by 13 places. Thus 'A' ↔ 'N', 'B' ↔ 'O' and so on.

- Write a function which takes a ROT13 encoded string as input and returns a decoded string.

- All letters will be uppercase. Do not transform any non-alphabetic character (i.e. spaces, punctuation), but do pass them on.
- Solution 1: my generated code

```javascript
function rot13(str) {
  var str = str.split("");
  var regex = /[^\w]/;
  var newStr = "";
  for (let i = 0; i < str.length; i++) {
    for (let j = 0; j < str[i].length; j++) {
      if (str[i][j].match(regex)) {
        newStr += str[i][j];
        continue;
      }
      if (str[i][j].charCodeAt(0) + 13 > 90) {
        newStr += String.fromCharCode(
          str[i][j].charCodeAt(0) + 13 - 90 + 65 - 1
        );
      } else {
        newStr += String.fromCharCode(str[i][j].charCodeAt(0) + 13);
      }
    }
  }
  return newStr;
}

rot13("SERR CVMMN!");
```

- Solution 2: using Map

```javascript
function rot13(str) {
  var str = str
    .split("")
    .map((res) => {
      var format = res.charCodeAt(res);

      if (format < 65 || format > 90) {
        return res;
      }
      if (format < 78) {
        return String.fromCharCode(format + 13);
      } else {
        return String.fromCharCode(format - 13);
      }
    })
    .join("");
  return str;
}

rot13("SERR CVMMN!");
```

- Solution 3: using modular arithmetic and cyclic nature of rot13 transform

```javascript
function rot13(str) {
  var regex = /\w/;
  var str = str
    .split("")
    .map((res) => {
      if (res.match(regex)) {
        return String.fromCharCode(((res.charCodeAt(0) - 65 + 13) % 26) + 65);
      } else {
        return res;
      }
    })
    .join("");
  console.log(str);
  return str;
}

rot13("SERR CVMMN!");
```

- Solution 4: using modular arithmetic and indexOf

```javascript
function rot13(str) {
  const alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
  return str
    .split("")
    .map((char) => {
      const pos = alphabet.indexOf(char);
      return pos >= 0 ? alphabet[(pos + 13) % 26] : char;
    })
    .join("");
}
```

- References:

  - https://forum.freecodecamp.org/t/freecodecamp-challenge-guide-caesars-cipher/16003

## Telephone Number Validator

- Return true if the passed string looks like a valid US phone number.

- The user may fill out the form field any way they choose as long as it has the format of a valid US number. The following are examples of valid formats for US numbers (refer to the tests below for other variants):

```javascript
555-555-5555
(555)555-5555
(555) 555-5555
555 555 5555
5555555555
1 555 555 5555
```

- For this challenge you will be presented with a string such as 800-692-7753 or 8oo-six427676;laskdjf. Your job is to validate or reject the US phone number based on any combination of the formats provided above. The area code is required. If the country code is provided, you must confirm that the country code is 1. Return true if the string is a valid US phone number; otherwise return false.

Solution 1:

```javascript
function telephoneCheck(str) {
  var regex = /^(1\s?)?(\d{3}|\(\d{3}\))[\s\-]?(\d{3})[\s|-]?(\d{4})$/g;
  var match = regex.test(str);
  return match;
}

telephoneCheck("1(757) 622-7382");
```

SOlution 2: using libphonenumber of google github

```javascript
function telephoneCheck(str) {
  var re = /^([+]?1[\s]?)?((?:[(](?:[2-9]1[02-9]|[2-9][02-8][0-9])[)][\s]?)|(?:(?:[2-9]1[02-9]|[2-9][02-8][0-9])[\s.-]?)){1}([2-9]1[02-9]|[2-9][02-9]1|[2-9][02-9]{2}[\s.-]?){1}([0-9]{4}){1}$/;
  return re.test(str);
}
telephoneCheck("555-555-5555");
```

## Cash Register

- Design a cash register drawer function checkCashRegister() that accepts purchase price as the first argument (price), payment as the second argument (cash), and cash-in-drawer (cid) as the third argument.

- cid is a 2D array listing available currency.

- The checkCashRegister() function should always return an object with a status key and a change key.

- Return {status: "INSUFFICIENT_FUNDS", change: []} if cash-in-drawer is less than the change due, or if you cannot return the exact change.

- Return {status: "CLOSED", change: [...]} with cash-in-drawer as the value for the key change if it is equal to the change due.

- Otherwise, return {status: "OPEN", change: [...]}, with the change due in coins and bills, sorted in highest to lowest order, as the value of the change key.

```javascript
Currency Unit	Amount
Penny	$0.01 (PENNY)
Nickel	$0.05 (NICKEL)
Dime	$0.1 (DIME)
Quarter	$0.25 (QUARTER)
Dollar	$1 (ONE)
Five Dollars	$5 (FIVE)
Ten Dollars	$10 (TEN)
Twenty Dollars	$20 (TWENTY)
One-hundred Dollars	$100 (ONE HUNDRED)
```

- Solution 1:

```javascript
function checkCashRegister(price, cash, cid) {
  var change = [];
  var cashback = cash - price;
  var prototype = [
    { name: "PENNY", val: 0.01 },
    { name: "NICKEL", val: 0.05 },
    { name: "DIME", val: 0.1 },
    { name: "QUARTER", val: 0.25 },
    { name: "ONE", val: 1 },
    { name: "FIVE", val: 5 },
    { name: "TEN", val: 10 },
    { name: "TWENTY", val: 20 },
    { name: "ONE HUNDRED", val: 100 },
  ];
  cid = cid.reverse();
  var register = cid.reduce(
    function (acc, curr) {
      acc.total += curr[1];
      acc[curr[0]] = curr[1];
      return acc;
    },
    { total: 0 }
  );
  if (register.total == cashback) {
    change = { status: "CLOSED", change: cid };
    return change;
  }

  if (register.total < cashback) {
    change = { status: "INSUFFICIENT_FUNDS", change: [] };
    return change;
  }
  for (let i of cid) {
    if (cashback <= 0) {
      break;
    }
    let item = prototype.find((res) => res.name == i[0]);
    if (item) {
      let result = false;
      let total = 0;
      while (register[item.name] > 0 && cashback >= item.val) {
        register[item.name] -= item.val;
        cashback = cashback - item.val;
        total += item.val;
        cashback = Math.round(cashback * 100) / 100;
        result = true;
      }

      if (result) {
        change.push([item.name, total]);
      }
    }
  }

  if (cashback > 0) {
    change = { status: "INSUFFICIENT_FUNDS", change: [] };
    return change;
  }

  if (change.length != prototype.length) {
    change = { status: "OPEN", change: change };
  }
  return change;
}

checkCashRegister(19.5, 20, [
  ["PENNY", 0.5],
  ["NICKEL", 0],
  ["DIME", 0],
  ["QUARTER", 0],
  ["ONE", 0],
  ["FIVE", 0],
  ["TEN", 0],
  ["TWENTY", 0],
  ["ONE HUNDRED", 0],
]);
```

- Solution 2:

```javascript
// Create an array of objects which hold the denominations and their values
var denom = [
  { name: "ONE HUNDRED", val: 100.0 },
  { name: "TWENTY", val: 20.0 },
  { name: "TEN", val: 10.0 },
  { name: "FIVE", val: 5.0 },
  { name: "ONE", val: 1.0 },
  { name: "QUARTER", val: 0.25 },
  { name: "DIME", val: 0.1 },
  { name: "NICKEL", val: 0.05 },
  { name: "PENNY", val: 0.01 },
];

function checkCashRegister(price, cash, cid) {
  var output = { status: null, change: [] };
  var change = cash - price;

  // Transform CID array into drawer object
  var register = cid.reduce(
    function (acc, curr) {
      acc.total += curr[1];
      acc[curr[0]] = curr[1];
      return acc;
    },
    { total: 0 }
  );

  // Handle exact change
  if (register.total === change) {
    output.status = "CLOSED";
    output.change = cid;
    return output;
  }

  // Handle obvious insufficient funds
  if (register.total < change) {
    output.status = "INSUFFICIENT_FUNDS";
    return output;
  }

  // Loop through the denomination array
  var change_arr = denom.reduce(function (acc, curr) {
    var value = 0;
    // While there is still money of this type in the drawer
    // And while the denomination is larger than the change remaining
    while (register[curr.name] > 0 && change >= curr.val) {
      change -= curr.val;
      register[curr.name] -= curr.val;
      value += curr.val;

      // Round change to the nearest hundreth deals with precision errors
      change = Math.round(change * 100) / 100;
    }
    // Add this denomination to the output only if any was used.
    if (value > 0) {
      acc.push([curr.name, value]);
    }
    return acc; // Return the current change_arr
  }, []); // Initial value of empty array for reduce

  // If there are no elements in change_arr or we have leftover change, return
  // the string "Insufficient Funds"
  if (change_arr.length < 1 || change > 0) {
    output.status = "INSUFFICIENT_FUNDS";
    return output;
  }

  // Here is your change, ma'am.
  output.status = "OPEN";
  output.change = change_arr;
  return output;
}

// test here
checkCashRegister(19.5, 20.0, [
  ["PENNY", 1.01],
  ["NICKEL", 2.05],
  ["DIME", 3.1],
  ["QUARTER", 4.25],
  ["ONE", 90.0],
  ["FIVE", 55.0],
  ["TEN", 20.0],
  ["TWENTY", 60.0],
  ["ONE HUNDRED", 100.0],
]);
```

See below for an example of a cash-in-drawer array:

- References:
  - https://forum.freecodecamp.org/t/freecodecamp-challenge-guide-smallest-common-multiple/16075

## Advance Algorithms

### 1. Divide and Conquer (DAC)

- An important category of algorithms that needs to be understood before diving into other topics
- It is used to solve problems that can be divided into subproblems that are similar to the original problem, but smaller in size
- DAC then recursively solves them and finally merges the results to find the solution of the problem
- Complexity: T(n)=D(n)+C(n)+M(n)
  - Meaning that every stage has a different complexity depending on the problem.
- It has three stages:
  - Divide — the problems into subproblems;
  - Conquer — the subproblems by using recursion;
  - Merge — the subproblems’ results into the final solution.
- What are they used for?
  - **Parallel programming** using multiple processors, so the subproblems are executed on different machines
  - DAC is the base of many algorithms such as Quick Sort, Merge Sort, Binary Search or fast multiplication algorithms.
  - **Binary Search**
    - is a searching algorithm.
    - In each step, the algorithm compares the input element x with the value of the middle element in array
    - If the values match, return the index of the middle
    - Otherwise, if x is less than the middle element, then the algorithm recurs for left side of middle element, else recurs for the right side of the middle element
    - Time Complexity: O(log2n)
  - **Quick Sort**
    - The algorithm picks a pivot element
    - Rearranges the array elements in such a way that all elements smaller than the picked pivot element move to left side of pivot
    - And all greater elements move to right side
    - Finally, the algorithm recursively sorts the subarrays on left and right of pivot element.
    - Time Complexity: O(n^2)
  - **Merge Sort** is also a sorting algorithm
    - The algorithm divides the array in two halves
    - Recursively sorts them and finally merges the two sorted halves.
    - Time Complexity: O(n log(n))
  - **Closest Pair of Points**
    - The problem is to find the closest pair of points in a set of points in x-y plane.
    - The problem can be solved in **O(n^2)** time by calculating distances of every pair of points and comparing the distances to find the minimum. - The Divide and Conquer algorithm solves the problem in **O(nLogn)** time.
    - Time Complexity: O(nLogn)
  - **Strassen’s Algorithm**
    - is an efficient algorithm to multiply two matrices
    - A simple method to multiply two matrices need 3 nested loops and is O(n^3)
    - Strassen’s algorithm multiplies two matrices in O(n^2.8974) time.
    - Time Complexity: O(n^2.8974)
  - **Cooley–Tukey Fast Fourier Transform (FFT)** algorithm
    - is the most common algorithm for FFT. It is a divide and conquer algorithm which works in O(nlogn) time.
    - Time Complexity: O(nlogn)
  - **Karatsuba algorithm for fast multiplication**
    - it does multiplication of two n-digit numbers in at most 3 n^{\log_23}\approx 3 n^{1.585}single-digit multiplications in general (and exactly n^{\log_23} when n is a power of 2).
    - It is therefore faster than the classical algorithm, which requires n2 single-digit products. If n = 210 = 1024, in particular, the exact counts are 310 = 59, 049 and (210)2 = 1, 048, 576, respectively.
    - A Naive Approach : O(n^2)
    - Time Complexity: O(N^(log 3) that is O(N^1.585)
  - **Fibonacci numbers**
  - **Matrix Multiplication**
- SUM OF N ELEMENTS USING DAC - C++
  ```C++
  int DAC(int arr[], int start, int finish)
  {
      if(start==finish)
          return arr[start];
      else
      {
          int mid = (start+finish)/2;
          int sum1 = DAC(arr, start, mid);
          int sum2 = DAC(arr, mid+1, finish);
          return sum1+sum2;
      }
  }
  ```

### 2. Sorting Algorithms

#### 2.1 Bubble Sort

- Is one of the simplest sorting algorithms
  - It is based on a repeated swap between adjacent elements if they are in wrong order. It is stable
- This algorithm is almost `never` used because of its O(N²) time complexitiy. But in computer graphics, it is popular to detect a very small error (like swap of two elements) in almost sorted array.

- Worst: O(n²)
- Average: O(n²)
- Best: O(n)
- Memory: O(1).
- Stable: yes

```javascript
 sort(originalArray) {
    // Flag that holds info about whether the swap has occur or not.
    let swapped = false;
    // Clone original array to prevent its modification.
    const array = [...originalArray];

    for (let i = 1; i < array.length; i += 1) {
      swapped = false;

      // Call visiting callback.
      this.callbacks.visitingCallback(array[i]);

      for (let j = 0; j < array.length - i; j += 1) {
        // Call visiting callback.
        this.callbacks.visitingCallback(array[j]);

        // Swap elements if they are in wrong order.
        if (this.comparator.lessThan(array[j + 1], array[j])) {
          [array[j], array[j + 1]] = [array[j + 1], array[j]];

          // Register the swap.
          swapped = true;
        }
      }

      // If there were no swaps then array is already sorted and there is
      // no need to proceed.
      if (!swapped) {
        return array;
      }
    }

    return array;
  }
```

#### 2.2 Selection Sort

- This algorithm is used when the input array's length is around `10 - 20`. Usually, insertion sort is preferred over selection sort. But selection sort takes less write than insertion sort. That's why sometimes, selection sort is preferred over insertion sort.
- Worst: O(n²)
- Average: O(n²)
- Best: O(n)
- Memory: O(1).
- Stable: yes

#### 2.3 Insertion sort

- This algorithm is used when the input array's length is around `10 - 20`. This algorithm is `mostly preferred` because its an adaptive algorithm i.e it improves its time complexitiy from O(N²) to even O(N\*logN) by taking advantage of a sorted subarray if its present in the input array.

```javascript
sort(originalArray) {
    const array = [...originalArray];

    // Go through all array elements...
    for (let i = 0; i < array.length; i += 1) {
      let currentIndex = i;

      // Call visiting callback.
      this.callbacks.visitingCallback(array[i]);

      // Go and check if previous elements and greater then current one.
      // If this is the case then swap that elements.
      while (
        array[currentIndex - 1] !== undefined &&
        this.comparator.lessThan(array[currentIndex], array[currentIndex - 1])
      ) {
        // Call visiting callback.
        this.callbacks.visitingCallback(array[currentIndex - 1]);

        // Swap the elements.
        [array[currentIndex - 1], array[currentIndex]] = [
          array[currentIndex],
          array[currentIndex - 1],
        ];

        // Shift current index left.
        currentIndex -= 1;
      }
    }

    return array;
  }
```

#### 2.1 Counting Sort

- The time complexity is O(N + k) where k is the largest integer present in the input array. This algorithm is only used when the input array's length is very very high and the largest element (k) present in the array is smaller than the length of array (N). For example, sort an array of length around a billion containing age of people
- It is basically using the frequency of each element (a kind of hashing)
- Determining the minimum and maximum value and then iterating between them to place each element based on its frequency.
- It is efficient if the range of input is not significantly greater than the number of elements.
- Time complexity: O(n+k) where n is the number of elements in input array and k is the range of input.
- Space complexity:O(n+k)

#### 2.2 Quick Sort

- This algorithm is used when the input array's length is `very very high`. This is usually preferred over mergesort. But we should select the pivot element properly. If we take the wrong pivot element, its time complexitiy can reach O(N²).
- An application of Divide and Conquer
- It is based on choosing an element as a pivot (first, last or median) and then swapping elements in order to place the pivot between all the elements smaller than it and all the elements bigger than it
- Time complexity: O(n\*log n)
- Space complexity: no additional space

#### 2.3 Merge Sort

- This algorithm is used when the input array's length is very very high and it is usually used to sort linked list.
- is also a Divide & Conquer application
- It divides the array in two halves, sorts each half and then merges them.
- It is also super fast like Quick Sort
- Time complexity: O(n\*log n)
- Space complexity: O(n) to store two subarrays at the same time and, finally, merge them.

#### 2.4 Radix Sort

- Uses Counting Sort as a subroutine, so it is not a comparison based algorithm
- What if the elements are in range from 1 to n2?
  - We can’t use counting sort because counting sort will take O(n2) which is worse than comparison based sorting algorithms. Can we sort such an array in linear time?
  - Radix Sort is the answer. The idea of Radix Sort is to do digit by digit sort starting from least significant digit to most significant digit. Radix sort uses counting sort as a subroutine to sort.
- Time complexity: O(n+k) where elements are in range [1, k]. It sorts the elements digit by digit starting with the least significant one (units), to the most (tens, hundreds etc.)
- Space complexity: O(n)

#### References

- https://www.geeksforgeeks.org/comparison-among-bubble-sort-selection-sort-and-insertion-sort/

### 3. Searching Algorithms

#### 3.1 Linear Search

- This algorithm’s approach is very simple: you start searching for your value from the first index of the data structure
- You compare them one by one until your value and your current element are equal.
- If that specific value is not in the DS, return -1.
- Time Complexity: O(n)

#### 3.2 Binary Search

- BS is one efficient search algorithm based on Divide and Conquer
- **Unfortunately, it only works only on sorted data structures**
- Being a DAC method, you continuously divide the DS in two halves and compare your in-search value with the middle element’s value.
  - If they are equal, the search is finished.
  - Either way, if your value is bigger/smaller than it, the search should continue on the right/left half.
    Time Complexity: O(log n)

### 4. Sieve of Eratosthenes

- The method uses a frequency list/map that marks the primality of every number in the range
  - [0, n]: ok[x]=0 if x is prime
  - ok[x]=1 otherwise
- We begin choosing every prime number from our list and marking its multiples from the list with 1 — that way, we choose the unmarked (0) numbers. - Finally, we can easily answer in O(1) to as many queries as we want.
- What are they used for?
  - Given an integer number n, print all the prime numbers smaller or equal to n.
  - Sieve of Eratosthenes is one of the most efficient algorithms that solves this problem and it perfectly works for n smaller than **10.000.000**
- Time complexity: O(n\*log(log n)) for the classical algorithm, O(n) for the optimized one.
- Space complexity: O(n)

### 5. Knuth-Morris-Pratt Algorithm

- Given a text of length n and a pattern of length m, find all the occurrences of the pattern in the text.
- Its working the best when the pattern has many repeating subpatterns.
- Knuth-Morris-Pratt Algorithm (KMP) is an efficient way to solve the pattern matching problem.
- For instance: find a pattern pat[] ( abxab) in a string txt[] (abxababxab)
- The naive solution is based on using a “sliding window”, where we compare character to character every time we set a new beginning index, starting from index 0 of the text to index n-m. That way, time complexity is O(m*(n-m+1))~O(n*m).
- Its using a **sliding window**, but instead of comparing all the characters to the substring’s, it is constantly looking for the longest suffix of the current subpattern which is also its prefix.
- In other words, anytime we detect a mismatch after some matches, we already know some of the characters in the text of the next window.
- Therefore, it is useless to match them again, so we restart the matching with the same character in the text with a character after that prefix. - - How do we know how many characters we should skip? Well, we should build a pre-process array that tells us how many characters should be skipped.
- What are they used for?
  - Given a text of length n and a pattern of length m, find all the occurrences of the pattern in the text.
  - Its working the best when the pattern has many repeating subpatterns.
- Time complexity: O(n)

### 6. Greedy

- At every step, we can make a choice that looks best at the moment, and we get the optimal solution of the complete problem.
- The Greedy method is mostly used for problems that require optimization and the local optimal solution leads to the global optimal solution
- when using Greedy, the optimal solution at each step leads to the overall optimal solution
- However, in most cases, the decision we make at one step affects the list of decisions for the next step
  - In this case, the algorithm must be mathematically demonstrated
- Greedy also produces great solutions on some mathematical problems, but not on all (it is possible that the most optimal solution is not guaranteed)!
- A Greedy algorithm generally has five components:
  - a candidate set — from which a solution is created;
  - a selection function — chooses the best candidate;
  - a feasibility function — can determine if a candidate is able to contribute to the solution;
  - an objective function — assigns the candidate to the (partial) solution;
  - a solution function — builts the solution from the partial solutions
- What are they used for?
  - **Activity Selection Problem**
    - You are given n activities with their start and finish times. Select the maximum number of activities that can be performed by a single person, assuming that a person can only work on a single activity at a time.
    - 1. Sort the activities according to their finishing time
    - 2. Select the first activity from the sorted array and print it.
    - 3. Do following for remaining activities in the sorted array.
      - If the start time of this activity is greater than or equal to the finish time of previously selected activity then select this activity and print it.
    - Time Complexity: O(nlogn)
  - **Job Sequencing Problem**
    - Given an array of jobs where every job has a deadline and associated profit if the job is finished before the deadline. It is also given that every job takes single unit of time, so the minimum possible deadline for any job is 1. How to maximize total profit if only one job can be scheduled at a time.
    - Sort all jobs in descending order of profit
    - Init the result sequence as the first job in sorted order
    - Do the following n-1 jobs
      - If the current job can fit the result sequence without missing deadline, add current job to result, else ignore the current job
    - Time Complexity: O(n^2)
  - **Huffman Coding**
    - It assigns variable-length bit codes to different characters.
    - The Greedy Choice is to assign least bit length code to the most frequent character.
    - The variable-length codes assigned to input characters as Prefix Codes
    - Use Heap Tree
    - What are they used for?
      - Lossless data compression algorithm
    - Time Complexity: O(nlogn)
  - **Kruskal’s Minimum Spanning Tree (MST)**
    - In Kruskal’s algorithm, we create a MST by picking edges one by one. The Greedy Choice is to pick the smallest weight edge that doesn’t cause a cycle in the MST constructed so far.
    - Kruskal’s algorithm runs faster in **sparse** graphs.
    - It traverses one node only once.
    - What are they used for?
      - To find the **minimum cost spanning tree** uses the greedy approach for a connected weighted graphs
    - Time Complexity: O(logV), V being the number of vertices.
  - **Prim’s Minimum Spanning Tree**
    - In Prim’s algorithm also, we create a MST by picking edges one by one.
    - We maintain two sets: a set of the vertices already included in MST and the set of the vertices not yet included.
    - The Greedy Choice is to pick the smallest weight edge that connects the two sets.
    - It traverses one node more than one time to get the minimum distance.
    - Prim’s algorithm runs faster in **dense** graphs.
    - What are they used for?
      - To find the **minimum cost spanning tree** uses the greedy approach for a connected weighted graph
    - Time complexity: O(V^2), V being the number of vertices.
  - **Dijkstra’s Shortest Path**
    - The Dijkstra’s algorithm is very similar to Prim’s algorithm.
    - The shortest path tree is built up, edge by edge
    - We maintain two sets:
      - a set of the vertices already included in the tree
      - the set of the vertices not yet included
    - The Greedy Choice is to pick the edge that connects the two sets and is on the smallest weight path from source to the set that contains not yet included vertices.
    - What are they used for?
      - Find the Shortest Path
      - It just talks about the shortest route and cost between 2 nodes. So in your case, if there's a need to include all nodes in between then the suggestion for TSP (Travelling sale person) is valid.
      - If you want to have the shortest routes and cost between all pairs of nodes, then you should go for Floyd's algorithm which is basically an extension of Dijkstra.
    - Time complexity: O(V^2) but with min-priority queue it drops down to O ( V + E l o g V )
    - Time complexity: O(LogV) for operations like extract-min and decrease-key value of Min Heap
      - Min Heap is used as a priority queue to get the minimum distance vertex from set of not yet included vertices
  - **Fractional Knapsack Problem**
    - Given weights and values of n items, we need to put these items in a knapsack of capacity W to get the maximum total value in the knapsack.
    - In the 0-1 Knapsack problem, we are not allowed to break items. We either take the whole item or don’t take it.
    - An efficient solution is to use **Greedy** approach.
      - The basic idea of the greedy approach is to calculate the ratio value/weight for each item and sort the item on basis of this ratio.
      - Then take the item with the highest ratio and add them until we can’t add the next item as a whole and at the end add the next item as much as we can. Which will always be the optimal solution to this problem.
    - Time complexity: O(NlogN) where N is the number of items in S.

### 7. Dynamic Programming

- Dynamic Programming (DP) is a similar approach to Divide & Conquer. It also breaks the problem into similar subproblems, but they are actually overlapping and codependent — they’re not solved independently.
- Each subproblem’s result can be used anytime later and it is built using memoization (precalculation). DP is mostly used for (time & space) optimization and it is based on finding a recurrence.
- DP applications include Fibonacci number series, Tower of Hanoi, Roy-Floyd-Warshall, Dijkstra etc. Below we are going to discuss about a DP solution of the 0–1 Knapsack Problem.

#### 7.1 0–1 Knapsack Problem

- Given weights and values of n items,we need to put these items in a knapsack of capacity W to get the maximum total value in the knapsack
- Fractioning items just as in the Greedy solution is **not allowed**
- The 0–1 property is given by the fact that we should either pick the whole item or not choose it at all.
- We build a DP structure as a matrix dp[i][cw] storing the maximum profit that we can obtain by choosing i objects whose total weight is cw. It is easy to notice that we should firstly initialize dp[1]w[i]] with v[i], where w[i] is the weight of the ith object and v[i] its value.
- The recurrence is the following: dp[i][cw] = max(dp[i-1][cw], dp[i-1]cw-w[i]]+v[i])
- Time complexity: O(nW) where, n is the number of items and W is the capacity of knapsack.

### 8. Longest Common Subsequence

- Given two sequences, find the length of the longest subsequence present in both of them. A subsequence is a sequence that appears in the same relative order, but not necessarily contiguous.
- For example, “bcd”, “abdg”, “c” are subsequences of “abcdefg”.

### 9. Longest Increasing Subsequence

### 10. Convex Hull

### 11. Graph Traversals

### 12. Floyd-Warshall Algorithm

### 13. Dijkstra’s Algorithm & Bellman-Ford Algorithm

### 14. Kruskal’s Algorithm

### 15. Topological Sorting

### 12. Shannon-Fano Algorithm for Data Compression

### 13. LZW (Lempel–Ziv–Welch) for Data Compression

### 14. Map Reduce

- https://en.wikipedia.org/wiki/MapReduce

### 15. Memorization and Recursion

- https://dev.to/ionabrabender/memoization-and-recursion-228f

### 16. Euclidean algorithms (Basic and Extended)

- GCD of two numbers is the largest number that divides both of them. A simple way to find GCD is to factorize both numbers and multiply common factors.

```javascript
36 =  2 * 2 * 3 * 3
60 = 2 * 2 * 3 *5
GCD = Multiplication of common factor
    = 2 * 2 * 3
    = 12
```

- Basic Euclidean Algorithm for GCD, The algorithm is based on below facts.
  - If we subtract smaller number from larger (we reduce larger number), GCD doesn’t change. So if we keep subtracting repeatedly the larger of two, we end up with GCD.
  - Now instead of subtraction, if we divide smaller number, the algorithm stops when we find remainder 0.

### 16. Find currenrcy rates path

- https://stackoverflow.com/questions/3372375/algorithm-to-determine-exchange-rate

## Modulo operator (%)

- Basically, operated on a number, it divides the number by the given divisor and gives the remainder of the division.
  For Example,

```javascript
0 % 5 = 0 because 0 / 5 = 0 and the remainder is 0.

2 % 5 = 2 because 2 / 5 = 0 and the remainder is 2

4 % 5 = 4 because 4 / 5 = 0 and the remainder is 4

5 % 5 = 0 because 5 / 5 = 1 and the remainder is 0

7 % 5 = 2 because 7 / 5 = 1 and the remainder is 2

9 % 5 = 4 because 9 / 5 = 1 and the remainder is 4

10 % 5 = 0 because 10 / 5 = 2 and the remainder is 0
```

- But you must have noticed a pattern here.
  As you might have noticed, the amazing modulo operator wraps over the LHS value when it just reaches multiples of the RHS value.
  e.g. in our case, when LHS = 5, it wrapped over to 0
  OR
  when LHS = 10, it wrapped over to 0 again.

Hence, we see the following pattern emerging

```javascript
     0 ⇔ 0
     1 ⇔ 1
     2 ⇔ 2
     3 ⇔ 3
     4 ⇔ 4
     5 ⇔ 0
     6 ⇔ 1
     7 ⇔ 2
     8 ⇔ 3
     9 ⇔ 4
    10 ⇔ 0
```

Hence, we conclude that using modulo operator, one can map a range of values to a range between [0 to DIVISOR - 1]. In our case, we mapped [5 - 9] between [0 - 4] or mapped [6 - 10] between [0 - 4].

## Recursion

- When a function calls itself, its called Recursion. It will be easier for those who have seen the movie Inception. Leonardo had a dream, in that dream he had another dream, in that dream he had yet another dream, and that goes on. So it's like there is a function called , and we are just calling it in itself.

```javascript
function dream()
    print "Dreaming"
    dream()
```

- Recursion is useful in solving problems which can be broken down into smaller problems of the same kind. But when it comes to solving problems using Recursion there are several things to be taken care of. Let's take a simple example and try to understand those. Following is the pseudo code of finding factorial of a given number using recursion.

```javascript
function factorial(x)
    if x is 0                    // base case
        return 1
    return x*factorial(x-1)       // break into smaller problem(s)
```

- Base Case: Any recursive method must have a terminating condition. Terminating condition is one for which the answer is already known and we just need to return that. For example for the factorial problem, we know that , so when is 0 we simply return 1, otherwise we break into smaller problem i.e. find factorial of . If we don't include a Base Case, the function will keep calling itself, and ultimately will result in stack overflow. For example, the function given above has no base case. If you write a code for it in any language, it will give a runtime error.

- Number of Recursive calls: There is an upper limit to the number of recursive calls that can be made. To prevent this make sure that your base case is reached before stack size limit exceeds.

- So, if we want to solve a problem using recursion, then we need to make sure that:

  - The problem can broken down into smaller problems of same type.
  - Problem has some base case(s).
  - Base case is reached before the stack size limit exceeds.

## Backtracking

## Machine learning algorithims

- Linear regression
- Logistic regression
- https://towardsdatascience.com/all-machine-learning-algorithms-you-should-know-in-2021-2e357dd494c7

## References:

1. https://dev.to/iuliagroza/complete-introduction-to-the-30-most-essential-data-structures-algorithms-43kd?fbclid=IwAR1WYHQ7loHbuEWo4KefnVHV2AvGurQftrTFdtJx5MobXhSECv-8Ws3bt08
2. GeeksforGeeks Youtube: https://www.youtube.com/channel/UC0RhatS1pyxInC00YKjjBqQ, thanks so much for much comprehensive videos :)
