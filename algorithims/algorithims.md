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

## Machine learning algorithims

- Linear regression
- Logistic regression
- https://towardsdatascience.com/all-machine-learning-algorithms-you-should-know-in-2021-2e357dd494c7

## References:

1. https://dev.to/iuliagroza/complete-introduction-to-the-30-most-essential-data-structures-algorithms-43kd?fbclid=IwAR1WYHQ7loHbuEWo4KefnVHV2AvGurQftrTFdtJx5MobXhSECv-8Ws3bt08
2. GeeksforGeeks Youtube: https://www.youtube.com/channel/UC0RhatS1pyxInC00YKjjBqQ, thanks so much for much comprehensive videos :)
