![Logo](/logo.png)

# 30 seconds of code [![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/30-seconds-of-code/Lobby)
> Curated collection of useful Javascript snippets that you can understand in 30 seconds or less.

- Use <kbd>Ctrl</kbd> + <kbd>F</kbd> or <kbd>command</kbd> + <kbd>F</kbd> to search for a snippet.
- Contributions welcome, please read the [contribution guide](CONTRIBUTING.md).
- Snippets are written in ES6, use the [Babel transpiler](https://babeljs.io/) to ensure backwards-compatibility.

## Table of Contents

### Array
* [Array concatenation](#array-concatenation)
* [Array difference](#array-difference)
* [Array intersection](#array-intersection)
* [Array union](#array-union)
* [Average of array of numbers](#average-of-array-of-numbers)
* [Chunk array](#chunk-array)
* [Compact](#compact)
* [Count occurrences of a value in array](#count-occurrences-of-a-value-in-array)
* [Deep flatten array](#deep-flatten-array)
* [Drop elements in array](#drop-elements-in-array)
* [Fill array](#fill-array)
* [Filter out non unique values in an array](#filter-out-non-unique-values-in-an-array)
* [Flatten array up to depth](#flatten-array-up-to-depth)
* [Flatten array](#flatten-array)
* [Get max value from array](#get-max-value-from-array)
* [Get min value from array](#get-min-value-from-array)
* [Group by](#group-by)
* [Head of list](#head-of-list)
* [Initial of list](#initial-of-list)
* [Initialize array with range](#initialize-array-with-range)
* [Initialize array with values](#initialize-array-with-values)
* [Last of list](#last-of-list)
* [Median of array of numbers](#median-of-array-of-numbers)
* [Nth element of array](#nth-element-of-array)
* [Pick](#pick)
* [Shuffle array](#shuffle-array)
* [Similarity between arrays](#similarity-between-arrays)
* [Sum of array of numbers](#sum-of-array-of-numbers)
* [Tail of list](#tail-of-list)
* [Take](#take)
* [Unique values of array](#unique-values-of-array)

### Browser
* [Bottom visible](#bottom-visible)
* [Current URL](#current-url)
* [Element is visible in viewport](#element-is-visible-in-viewport)
* [Get scroll position](#get-scroll-position)
* [Redirect to URL](#redirect-to-url)
* [Scroll to top](#scroll-to-top)

### Date
* [Get days difference between dates](#get-days-difference-between-dates)

### Function
* [Chain asynchronous functions](#chain-asynchronous-functions)
* [Curry](#curry)
* [Pipe](#pipe)
* [Promisify](#promisify)
* [Run promises in series](#run-promises-in-series)
* [Sleep](#sleep)

### Math
* [Collatz algorithm](#collatz-algorithm)
* [Distance between two points](#distance-between-two-points)
* [Divisible by number](#divisible-by-number)
* [Even or odd number](#even-or-odd-number)
* [Factorial](#factorial)
* [Fibonacci array generator](#fibonacci-array-generator)
* [Greatest common divisor (GCD)](#greatest-common-divisor-gcd)
* [Hamming distance](#hamming-distance)
* [Percentile](#percentile)
* [Powerset](#powerset)
* [Round number to n digits](#round-number-to-n-digits)
* [Standard deviation](#standard-deviation)

### Media
* [Speech synthesis (experimental)](#speech-synthesis-experimental)

### Object
* [Object from key value pairs](#object-from-key-value-pairs)
* [Object to key value pairs](#object-to-key-value-pairs)
* [Shallow clone object](#shallow-clone-object)

### String
* [Anagrams of string (with duplicates)](#anagrams-of-string-with-duplicates)
* [Capitalize first letter of every word](#capitalize-first-letter-of-every-word)
* [Capitalize first letter](#capitalize-first-letter)
* [Check for palindrome](#check-for-palindrome)
* [Reverse a string](#reverse-a-string)
* [Sort characters in string (alphabetical)](#sort-characters-in-string-alphabetical)
* [Truncate a string](#truncate-a-string)

### Utility
* [Escape regular expression](#escape-regular-expression)
* [Get native type of value](#get-native-type-of-value)
* [Is array](#is-array)
* [Is boolean](#is-boolean)
* [Is function](#is-function)
* [Is number](#is-number)
* [Is string](#is-string)
* [Is symbol](#is-symbol)
* [Measure time taken by function](#measure-time-taken-by-function)
* [Number to array of digits](#number-to-array-of-digits)
* [Ordinal suffix of number](#ordinal-suffix-of-number)
* [Random integer in range](#random-integer-in-range)
* [Random number in range](#random-number-in-range)
* [RGB to hexadecimal](#rgb-to-hexadecimal)
* [Swap values of two variables](#swap-values-of-two-variables)
* [URL parameters](#url-parameters)
* [UUID generator](#uuid-generator)
* [Validate email](#validate-email)
* [Validate number](#validate-number)
* [Value or default](#value-or-default)

## Array

### Array concatenation
#### 拼接
- Use `Array.concat()` to concatenate an array with any additional arrays and/or values, specified in `args`.
- ES6
```js
const arrayConcat = (arr, ...args) => arr.concat(...args);
// arrayConcat([1], 2, [3], [[4]]) -> [1,2,3,[4]]
```
- ES5
```js
var arrayConcat = function arrayConcat(arr) {
  for (var _len = arguments.length, args = Array(_len > 1 ? _len - 1 : 0), _key = 1; _key < _len; _key++) {
    args[_key - 1] = arguments[_key];
  }

  return arr.concat.apply(arr, args);
};
// arrayConcat([1], 2, [3], [[4]]) -> [1,2,3,[4]]
```
[⬆ back to top](#table-of-contents)

### Array difference
#### 差异
- Create a `Set` from `b`, then use `Array.filter()` on `a` to only keep values not contained in `b`.
- ES6
```js
const difference = (a, b) => { const s = new Set(b); return a.filter(x => !s.has(x)); };
// difference([1,2,3], [1,2]) -> [3]
```
- ES5
```js
var difference = function difference(a, b) {
  var s = new Set(b);return a.filter(function (x) {
    return !s.has(x);
  });
};
// difference([1,2,3], [1,2]) -> [3]
```
[⬆ back to top](#table-of-contents)

### Array intersection
#### 交叉
- Create a `Set` from `b`, then use `Array.filter()` on `a` to only keep values contained in `b`.
- ES6
```js
const intersection = (a, b) => { const s = new Set(b); return a.filter(x => s.has(x)); };
// intersection([1,2,3], [4,3,2]) -> [2,3]
```
- ES5
```js
var intersection = function intersection(a, b) {
  var s = new Set(b);return a.filter(function (x) {
    return s.has(x);
  });
};
// intersection([1,2,3], [4,3,2]) -> [2,3]
```
[⬆ back to top](#table-of-contents)

### Array union
#### 联合
- Create a `Set` with all values of `a` and `b` and convert to an array.

- ES6
```js
const union = (a, b) => Array.from(new Set([...a, ...b]));
// union([1,2,3], [4,3,2]) -> [1,2,3,4]
```
- ES5
```js
function _toConsumableArray(arr) {
  if (Array.isArray(arr)) {
    for (var i = 0, arr2 = Array(arr.length); i < arr.length; i++) {
      arr2[i] = arr[i];
    }
    return arr2;
  } else {
    return Array.from(arr);
  }
}

var union = function union(a, b) {
  return Array.from(
    new Set([].concat(_toConsumableArray(a), _toConsumableArray(b)))
  );
};
// union([1,2,3], [4,3,2]) -> [1,2,3,4]
```
[⬆ back to top](#table-of-contents)

### Average of array of numbers
#### 平均
- Use `Array.reduce()` to add each value to an accumulator, initialized with a value of `0`, divide by the `length` of the array.

- ES6
```js
const average = arr => arr.reduce((acc, val) => acc + val, 0) / arr.length;
// average([1,2,3]) -> 2
```
- ES5
```js
var average = function average(arr) {
  return (
    arr.reduce(function(acc, val) {
      return acc + val;
    }, 0) / arr.length
  );
};
// average([1,2,3]) -> 2
```
[⬆ back to top](#table-of-contents)

### Chunk array
#### 重组整列
- Use `Array.from()` to create a new array, that fits the number of chunks that will be produced.
Use `Array.slice()` to map each element of the new array to a chunk the length of `size`.
If the original array can't be split evenly, the final chunk will contain the remaining elements.

- ES6
```js
const chunk = (arr, size) =>
  Array.from({length: Math.ceil(arr.length / size)}, (v, i) => arr.slice(i * size, i * size + size));
// chunk([1,2,3,4,5], 2) -> [[1,2],[3,4],5]
```
- ES5
```js
var chunk = function chunk(arr, size) {
  return Array.from({ length: Math.ceil(arr.length / size) }, function(v, i) {
    return arr.slice(i * size, i * size + size);
  });
};

// chunk([1,2,3,4,5], 2) -> [[1,2],[3,4],5]
```
[⬆ back to top](#table-of-contents)

### Compact
#### 有效值
- Use `Array.filter()` to filter out falsey values (`false`, `null`, `0`, `""`, `undefined`, and `NaN`).

- ES6
```js
const compact = (arr) => arr.filter(v => v);
// compact([0, 1, false, 2, '', 3, 'a', 'e'*23, NaN, 's', 34]) -> [ 1, 2, 3, 'a', 's', 34 ]
```
- ES5
```js
var compact = function compact(arr) {
  return arr.filter(function(v) {
    return v;
  });
};
// compact([0, 1, false, 2, '', 3, 'a', 'e'*23, NaN, 's', 34]) -> [ 1, 2, 3, 'a', 's', 34 ]
```
[⬆ back to top](#table-of-contents)

### Count occurrences of a value in array
#### 存在总数
- Use `Array.reduce()` to increment a counter each time you encounter the specific value inside the array.

- ES6
```js
const countOccurrences = (arr, value) => arr.reduce((a, v) => v === value ? a + 1 : a + 0, 0);
// countOccurrences([1,1,2,1,2,3], 1) -> 3
```
- ES5
```js
const countOccurrences = (arr, value) => arr.reduce((a, v) => v === value ? a + 1 : a + 0, 0);
// countOccurrences([1,1,2,1,2,3], 1) -> 3
```
[⬆ back to top](#table-of-contents)

### Deep flatten array
#### 深平阵数组
- Use recursion.
Use `Array.reduce()` to get all elements that are not arrays, flatten each element that is an array.

- ES6
```js
const deepFlatten = arr =>
  arr.reduce((a, v) => a.concat(Array.isArray(v) ? deepFlatten(v) : v), []);
// deepFlatten([1,[2],[[3],4],5]) -> [1,2,3,4,5]
```
- ES5
```js
var deepFlatten = function deepFlatten(arr) {
  return arr.reduce(function(a, v) {
    return a.concat(Array.isArray(v) ? deepFlatten(v) : v);
  }, []);
};
// deepFlatten([1,[2],[[3],4],5]) -> [1,2,3,4,5]
```
[⬆ back to top](#table-of-contents)

### Drop elements in array
#### 提取条件项
- Loop through the array, using `Array.shift()` to drop the first element of the array until the returned value from the function is `true`. 
Returns the remaining elements.

- ES6
```js
const dropElements = (arr, func) => {
  while (arr.length > 0 && !func(arr[0])) arr.shift();
  return arr;
};
// dropElements([1, 2, 3, 4], n => n >= 3) -> [3,4]
```
- ES5
```js
var dropElements = function dropElements(arr, func) {
  while (arr.length > 0 && !func(arr[0])) {
    arr.shift();
  }
  return arr;
};
// dropElements([1, 2, 3, 4], n => n >= 3) -> [3,4]
```
[⬆ back to top](#table-of-contents)

### Fill array

Use `Array.map()` to map values between `start` (inclusive) and `end` (exclusive) to `value`.
Omit `start` to start at the first element and/or `end` to finish at the last.

- ES6
```js
const fillArray = (arr, value, start = 0, end = arr.length) =>
  arr.map((v, i) => i >= start && i < end ? value : v);
// fillArray([1,2,3,4],'8',1,3) -> [1,'8','8',4]
```
- ES5
```js
var fillArray = function fillArray(arr, value) {
  var start =
    arguments.length > 2 && arguments[2] !== undefined ? arguments[2] : 0;
  var end =
    arguments.length > 3 && arguments[3] !== undefined
      ? arguments[3]
      : arr.length;
  return arr.map(function(v, i) {
    return i >= start && i < end ? value : v;
  });
};
// fillArray([1,2,3,4],'8',1,3) -> [1,'8','8',4]
```
[⬆ back to top](#table-of-contents)

### Filter out non-unique values in an array

Use `Array.filter()` for an array containing only the unique values.

- ES6
```js
const filterNonUnique = arr => arr.filter(i => arr.indexOf(i) === arr.lastIndexOf(i));
// filterNonUnique([1,2,2,3,4,4,5]) -> [1,3,5]
```
- ES5
```js
var filterNonUnique = function filterNonUnique(arr) {
  return arr.filter(function(i) {
    return arr.indexOf(i) === arr.lastIndexOf(i);
  });
};
// filterNonUnique([1,2,2,3,4,4,5]) -> [1,3,5]
```
[⬆ back to top](#table-of-contents)

### Flatten array up to depth

Use recursion, decrementing `depth` by 1 for each level of depth.
Use `Array.reduce()` and `Array.concat()` to merge elements or arrays.
Base case, for `depth` equal to `1` stops recursion.
Omit the second element, `depth` to flatten only to a depth of `1` (single flatten).

- ES6
```js
const flattenDepth = (arr, depth = 1) =>
  depth != 1 ? arr.reduce((a, v) => a.concat(Array.isArray(v) ? flattenDepth(v, depth - 1) : v), [])
  : arr.reduce((a, v) => a.concat(v), []);
// flattenDepth([1,[2],[[[3],4],5]], 2) -> [1,2,[3],4,5]
```
- ES5
```js
var flattenDepth = function flattenDepth(arr) {
  var depth =
    arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : 1;
  return depth != 1
    ? arr.reduce(function(a, v) {
        return a.concat(Array.isArray(v) ? flattenDepth(v, depth - 1) : v);
      }, [])
    : arr.reduce(function(a, v) {
        return a.concat(v);
      }, []);
};
// flattenDepth([1,[2],[[[3],4],5]], 2) -> [1,2,[3],4,5]
```
[⬆ back to top](#table-of-contents)

### Flatten array

Use `Array.reduce()` to get all elements inside the array and `concat()` to flatten them.

- ES6
```js
const flatten = arr => arr.reduce((a, v) => a.concat(v), []);
// flatten([1,[2],3,4]) -> [1,2,3,4]
```
- ES5
```js
var flatten = function flatten(arr) {
  return arr.reduce(function(a, v) {
    return a.concat(v);
  }, []);
};

// flatten([1,[2],3,4]) -> [1,2,3,4]
```
[⬆ back to top](#table-of-contents)

### Get max value from array

Use `Math.max()` combined with the spread operator (`...`) to get the maximum value in the array.

- ES6
```js
const arrayMax = arr => Math.max(...arr);
// arrayMax([10, 1, 5]) -> 10
```
- ES6
```js
function _toConsumableArray(arr) {
  if (Array.isArray(arr)) {
    for (var i = 0, arr2 = Array(arr.length); i < arr.length; i++) {
      arr2[i] = arr[i];
    }
    return arr2;
  } else {
    return Array.from(arr);
  }
}

var arrayMax = function arrayMax(arr) {
  return Math.max.apply(Math, _toConsumableArray(arr));
};
// arrayMax([10, 1, 5]) -> 10
```
[⬆ back to top](#table-of-contents)

### Get min value from array

Use `Math.min()` combined with the spread operator (`...`) to get the minimum value in the array.

- ES6
```js
const arrayMin = arr => Math.min(...arr);
// arrayMin([10, 1, 5]) -> 1
```
- ES6
```js
function _toConsumableArray(arr) {
  if (Array.isArray(arr)) {
    for (var i = 0, arr2 = Array(arr.length); i < arr.length; i++) {
      arr2[i] = arr[i];
    }
    return arr2;
  } else {
    return Array.from(arr);
  }
}

var arrayMin = function arrayMin(arr) {
  return Math.min.apply(Math, _toConsumableArray(arr));
};
// arrayMin([10, 1, 5]) -> 1
```
[⬆ back to top](#table-of-contents)

### Group by

Use `Array.map()` to map the values of an array to a function or property name.
Use `Array.reduce()` to create an object, where the keys are produced from the mapped results.

- ES6
```js
const groupBy = (arr, func) =>
  arr.map(typeof func === 'function' ? func : val => val[func])
    .reduce((acc, val, i) => { acc[val] = (acc[val] || []).concat(arr[i]); return acc; }, {});
// groupBy([6.1, 4.2, 6.3], Math.floor) -> {4: [4.2], 6: [6.1, 6.3]}
// groupBy(['one', 'two', 'three'], 'length') -> {3: ['one', 'two'], 5: ['three']}
```
- ES6
```js
var groupBy = function groupBy(arr, func) {
  return arr
    .map(
      typeof func === "function"
        ? func
        : function(val) {
            return val[func];
          }
    )
    .reduce(function(acc, val, i) {
      acc[val] = (acc[val] || []).concat(arr[i]);
      return acc;
    }, {});
};
// groupBy([6.1, 4.2, 6.3], Math.floor) -> {4: [4.2], 6: [6.1, 6.3]}
// groupBy(['one', 'two', 'three'], 'length') -> {3: ['one', 'two'], 5: ['three']}
```
[⬆ back to top](#table-of-contents)

### Head of list

Use `arr[0]` to return the first element of the passed array.

- ES6
```js
const head = arr => arr[0];
// head([1,2,3]) -> 1
```
- ES6
```js
var head = function head(arr) {
  return arr[0];
};
// head([1,2,3]) -> 1
```
[⬆ back to top](#table-of-contents)

### Initial of list

Use `arr.slice(0,-1)`to return all but the last element of the array.

- ES6
```js
const initial = arr => arr.slice(0, -1);
// initial([1,2,3]) -> [1,2]
```
- ES6
```js
var initial = function initial(arr) {
  return arr.slice(0, -1);
};
// initial([1,2,3]) -> [1,2]
```
[⬆ back to top](#table-of-contents)

### Initialize array with range

Use `Array(end-start)` to create an array of the desired length, `Array.map()` to fill with the desired values in a range.
You can omit `start` to use a default value of `0`.

- ES6
```js
const initializeArrayRange = (end, start = 0) =>
  Array.apply(null, Array(end - start)).map((v, i) => i + start);
// initializeArrayRange(5) -> [0,1,2,3,4]
```
- ES6
```js
var initializeArrayRange = function initializeArrayRange(end) {
  var start =
    arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : 0;
  return Array.apply(null, Array(end - start)).map(function(v, i) {
    return i + start;
  });
};
// initializeArrayRange(5) -> [0,1,2,3,4]
```
[⬆ back to top](#table-of-contents)

### Initialize array with values

Use `Array(n)` to create an array of the desired length, `fill(v)` to fill it with the desired values.
You can omit `value` to use a default value of `0`.

- ES6
```js
const initializeArray = (n, value = 0) => Array(n).fill(value);
// initializeArray(5, 2) -> [2,2,2,2,2]
```
- ES6
```js
var initializeArray = function initializeArray(n) {
  var value =
    arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : 0;
  return Array(n).fill(value);
};
// initializeArray(5, 2) -> [2,2,2,2,2]
```
[⬆ back to top](#table-of-contents)

### Last of list

Use `arr.slice(-1)[0]` to get the last element of the given array.

- ES6
```js
const last = arr => arr.slice(-1)[0];
// last([1,2,3]) -> 3
```
- ES6
```js
var last = function last(arr) {
  return arr.slice(-1)[0];
};
// last([1,2,3]) -> 3
```
[⬆ back to top](#table-of-contents)

### Median of array of numbers

Find the middle of the array, use `Array.sort()` to sort the values.
Return the number at the midpoint if `length` is odd, otherwise the average of the two middle numbers.

- ES6
```js
const median = arr => {
  const mid = Math.floor(arr.length / 2), nums = arr.sort((a, b) => a - b);
  return arr.length % 2 !== 0 ? nums[mid] : (nums[mid - 1] + nums[mid]) / 2;
};
// median([5,6,50,1,-5]) -> 5
// median([0,10,-2,7]) -> 3.5
```
- ES6
```js
var median = function median(arr) {
  var mid = Math.floor(arr.length / 2),
    nums = arr.sort(function(a, b) {
      return a - b;
    });
  return arr.length % 2 !== 0 ? nums[mid] : (nums[mid - 1] + nums[mid]) / 2;
};
// median([5,6,50,1,-5]) -> 5
// median([0,10,-2,7]) -> 3.5
```
[⬆ back to top](#table-of-contents)

### Nth element of array

Use `Array.slice()` to get an array containing the nth element at the first place. 
If the index is out of bounds, return `[]`.
Omit the second argument, `n`, to get the first element of the array.

- ES6
```js
const nth = (arr, n=0) => (n>0? arr.slice(n,n+1) : arr.slice(n))[0];
// nth(['a','b','c'],1) -> 'b'
// nth(['a','b','b']-2) -> 'a'
```
- ES6
```js
var nth = function nth(arr) {
  var n = arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : 0;
  return (n > 0 ? arr.slice(n, n + 1) : arr.slice(n))[0];
};
// nth(['a','b','c'],1) -> 'b'
// nth(['a','b','b']-2) -> 'a'
```
[⬆ back to top](#table-of-contents)

### Pick

Use `Array.reduce()` to convert the filtered/picked keys back to a object with the corresponding key:value pair if the key exist in the obj.

- ES6
```js
const pick = (obj, arr) =>
  arr.reduce((acc, curr) => (curr in obj && (acc[curr] = obj[curr]), acc), {});
// pick({ 'a': 1, 'b': '2', 'c': 3 }, ['a', 'c']) -> { 'a': 1, 'c': 3 }
// pick(object, ['a', 'c'])['a'] -> 1
```
- ES6
```js
var pick = function pick(obj, arr) {
  return arr.reduce(function(acc, curr) {
    return curr in obj && (acc[curr] = obj[curr]), acc;
  }, {});
};
// pick({ 'a': 1, 'b': '2', 'c': 3 }, ['a', 'c']) -> { 'a': 1, 'c': 3 }
// pick(object, ['a', 'c'])['a'] -> 1
```
[⬆ back to top](#table-of-contents)

### Shuffle array

Use `Array.sort()` to reorder elements, using `Math.random()` in the comparator.

- ES6
```js
const shuffle = arr => arr.sort(() => Math.random() - 0.5);
// shuffle([1,2,3]) -> [2,3,1]
```
- ES6
```js
var shuffle = function shuffle(arr) {
  return arr.sort(function() {
    return Math.random() - 0.5;
  });
};
// shuffle([1,2,3]) -> [2,3,1]
```
[⬆ back to top](#table-of-contents)

### Similarity between arrays

Use `filter()` to remove values that are not part of `values`, determined using `includes()`.

- ES6
```js
const similarity = (arr, values) => arr.filter(v => values.includes(v));
// similarity([1,2,3], [1,2,4]) -> [1,2]
```
- ES6
```js
var similarity = function similarity(arr, values) {
  return arr.filter(function(v) {
    return values.includes(v);
  });
};
// similarity([1,2,3], [1,2,4]) -> [1,2]
```
[⬆ back to top](#table-of-contents)

### Sum of array of numbers

Use `Array.reduce()` to add each value to an accumulator, initialized with a value of `0`.

- ES6
```js
const sum = arr => arr.reduce((acc, val) => acc + val, 0);
// sum([1,2,3,4]) -> 10
```
- ES6
```js
var sum = function sum(arr) {
  return arr.reduce(function(acc, val) {
    return acc + val;
  }, 0);
};
// sum([1,2,3,4]) -> 10
```
[⬆ back to top](#table-of-contents)

### Tail of list

Return `arr.slice(1)` if the array's `length` is more than `1`, otherwise return the whole array.

- ES6
```js
const tail = arr => arr.length > 1 ? arr.slice(1) : arr;
// tail([1,2,3]) -> [2,3]
// tail([1]) -> [1]
```
- ES6
```js
var tail = function tail(arr) {
  return arr.length > 1 ? arr.slice(1) : arr;
};
// tail([1,2,3]) -> [2,3]
// tail([1]) -> [1]
```
[⬆ back to top](#table-of-contents)

### Take

Use `Array.slice()` to create a slice of the array with `n` elements taken from the beginning.

- ES6
```js
const take = (arr, n = 1) => arr.slice(0, n);
// take([1, 2, 3], 5) -> [1, 2, 3]
// take([1, 2, 3], 0) -> []
```
- ES6
```js
var take = function take(arr) {
  var n = arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : 1;
  return arr.slice(0, n);
};
// take([1, 2, 3], 5) -> [1, 2, 3]
// take([1, 2, 3], 0) -> []
```
[⬆ back to top](#table-of-contents)

### Unique values of array

Use ES6 `Set` and the `...rest` operator to discard all duplicated values.

- ES6
```js
const unique = arr => [...new Set(arr)];
// unique([1,2,2,3,4,4,5]) -> [1,2,3,4,5]
```
- ES6
```js
function _toConsumableArray(arr) {
  if (Array.isArray(arr)) {
    for (var i = 0, arr2 = Array(arr.length); i < arr.length; i++) {
      arr2[i] = arr[i];
    }
    return arr2;
  } else {
    return Array.from(arr);
  }
}

var unique = function unique(arr) {
  return [].concat(_toConsumableArray(new Set(arr)));
};
// unique([1,2,2,3,4,4,5]) -> [1,2,3,4,5]
```
[⬆ back to top](#table-of-contents)
## Browser

### Bottom visible

Use `scrollY`, `scrollHeight` and `clientHeight` to determine if the bottom of the page is visible.

- ES6
```js
const bottomVisible = _ =>
  document.documentElement.clientHeight + window.scrollY >= document.documentElement.scrollHeight || document.documentElement.clientHeight;
// bottomVisible() -> true
```
- ES6
```js
var bottomVisible = function bottomVisible(_) {
  return (
    document.documentElement.clientHeight + window.scrollY >=
      document.documentElement.scrollHeight ||
    document.documentElement.clientHeight
  );
};
// bottomVisible() -> true
```
[⬆ back to top](#table-of-contents)

### Current URL

Use `window.location.href` to get current URL.

- ES6
```js
const currentUrl = _ => window.location.href;
// currentUrl() -> 'https://google.com'
```
- ES6
```js
var currentUrl = function currentUrl(_) {
  return window.location.href;
};
// currentUrl() -> 'https://google.com'
```
[⬆ back to top](#table-of-contents)

### Element is visible in viewport

Use `Element.getBoundingClientRect()` and the `window.inner(Width|Height)` values
to determine if a given element is visible in the viewport.
Omit the second argument to determine if the element is entirely visible, or specify `true` to determine if
it is partially visible.

- ES6
```js
const elementIsVisibleInViewport = (el, partiallyVisible = false) => {
  const { top, left, bottom, right } = el.getBoundingClientRect();
  return partiallyVisible
    ? ((top > 0 && top < innerHeight) || (bottom > 0 && bottom < innerHeight)) &&
      ((left > 0 && left < innerWidth) || (right > 0 && right < innerWidth))
    : top >= 0 && left >= 0 && bottom <= innerHeight && right <= innerWidth;
};
// e.g. 100x100 viewport and a 10x10px element at position {top: -1, left: 0, bottom: 9, right: 10}
// elementIsVisibleInViewport(el) -> false (not fully visible)
// elementIsVisibleInViewport(el, true) -> true (partially visible)
```
- ES6
```js
var elementIsVisibleInViewport = function elementIsVisibleInViewport(el) {
  var partiallyVisible =
    arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : false;

  var _el$getBoundingClient = el.getBoundingClientRect(),
    top = _el$getBoundingClient.top,
    left = _el$getBoundingClient.left,
    bottom = _el$getBoundingClient.bottom,
    right = _el$getBoundingClient.right;

  return partiallyVisible
    ? ((top > 0 && top < innerHeight) ||
        (bottom > 0 && bottom < innerHeight)) &&
      ((left > 0 && left < innerWidth) || (right > 0 && right < innerWidth))
    : top >= 0 && left >= 0 && bottom <= innerHeight && right <= innerWidth;
};
// e.g. 100x100 viewport and a 10x10px element at position {top: -1, left: 0, bottom: 9, right: 10}
// elementIsVisibleInViewport(el) -> false (not fully visible)
// elementIsVisibleInViewport(el, true) -> true (partially visible)
```
[⬆ back to top](#table-of-contents)

### Get scroll position

Use `pageXOffset` and `pageYOffset` if they are defined, otherwise `scrollLeft` and `scrollTop`.
You can omit `el` to use a default value of `window`.

- ES6
```js
const getScrollPos = (el = window) =>
  ({x: (el.pageXOffset !== undefined) ? el.pageXOffset : el.scrollLeft,
    y: (el.pageYOffset !== undefined) ? el.pageYOffset : el.scrollTop});
// getScrollPos() -> {x: 0, y: 200}
```
- ES6
```js
var getScrollPos = function getScrollPos() {
  var el =
    arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : window;
  return {
    x: el.pageXOffset !== undefined ? el.pageXOffset : el.scrollLeft,
    y: el.pageYOffset !== undefined ? el.pageYOffset : el.scrollTop
  };
};
// getScrollPos() -> {x: 0, y: 200}
```
[⬆ back to top](#table-of-contents)

### Redirect to URL

Use `window.location.href` or `window.location.replace()` to redirect to `url`.
Pass a second argument to simulate a link click (`true` - default) or an HTTP redirect (`false`).

- ES6
```js
const redirect = (url, asLink = true) =>
  asLink ? window.location.href = url : window.location.replace(url);
// redirect('https://google.com')
```
- ES6
```js
var redirect = function redirect(url) {
  var asLink =
    arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : true;
  return asLink ? (window.location.href = url) : window.location.replace(url);
};
// redirect('https://google.com')
```
[⬆ back to top](#table-of-contents)

### Scroll to top

Get distance from top using `document.documentElement.scrollTop` or `document.body.scrollTop`.
Scroll by a fraction of the distance from top. Use `window.requestAnimationFrame()` to animate the scrolling.

- ES6
```js
const scrollToTop = _ => {
  const c = document.documentElement.scrollTop || document.body.scrollTop;
  if (c > 0) {
    window.requestAnimationFrame(scrollToTop);
    window.scrollTo(0, c - c / 8);
  }
};
// scrollToTop()
```
- ES6
```js
var scrollToTop = function scrollToTop(_) {
  var c = document.documentElement.scrollTop || document.body.scrollTop;
  if (c > 0) {
    window.requestAnimationFrame(scrollToTop);
    window.scrollTo(0, c - c / 8);
  }
};
// scrollToTop()
```
[⬆ back to top](#table-of-contents)
## Date

### Get days difference between dates

Calculate the difference (in days) between to `Date` objects.

- ES6
```js
const getDaysDiffBetweenDates = (dateInitial, dateFinal) => (dateFinal - dateInitial) / (1000 * 3600 * 24);
// getDaysDiffBetweenDates(new Date("2017-12-13"), new Date("2017-12-22")) -> 9
```
- ES6
```js
var getDaysDiffBetweenDates = function getDaysDiffBetweenDates(
  dateInitial,
  dateFinal
) {
  return (dateFinal - dateInitial) / (1000 * 3600 * 24);
};
// getDaysDiffBetweenDates(new Date("2017-12-13"), new Date("2017-12-22")) -> 9
```
[⬆ back to top](#table-of-contents)
## Function

### Chain asynchronous functions

Loop through an array of functions containing asynchronous events, calling `next` when each asynchronous event has completed.

- ES6
```js
const chainAsync = fns => { let curr = 0; const next = () => fns[curr++](next); next(); };
/*
chainAsync([
  next => { console.log('0 seconds'); setTimeout(next, 1000); },
  next => { console.log('1 second');  setTimeout(next, 1000); },
  next => { console.log('2 seconds'); }
])
*/
```
- ES6
```js
var chainAsync = function chainAsync(fns) {
  var curr = 0;
  var next = function next() {
    return fns[curr++](next);
  };
  next();
};
/*
chainAsync([
  next => { console.log('0 seconds'); setTimeout(next, 1000); },
  next => { console.log('1 second');  setTimeout(next, 1000); },
  next => { console.log('2 seconds'); }
])
*/
```
[⬆ back to top](#table-of-contents)

### Curry

Use recursion.
If the number of provided arguments (`args`) is sufficient, call the passed function `f`.
Otherwise return a curried function `f` that expects the rest of the arguments.
If you want to curry a function that accepts a variable number of arguments (a variadic function, e.g. `Math.min()`), you can optionally pass the number of arguments to the second parameter `arity`.

- ES6
```js
const curry = (fn, arity = fn.length, ...args) =>
  arity <= args.length
    ? fn(...args)
    : curry.bind(null, fn, arity, ...args);
// curry(Math.pow)(2)(10) -> 1024
// curry(Math.min, 3)(10)(50)(2) -> 2
```
- ES6
```js
var curry = function curry(fn) {
  for (
    var _len = arguments.length,
      args = Array(_len > 2 ? _len - 2 : 0),
      _key = 2;
    _key < _len;
    _key++
  ) {
    args[_key - 2] = arguments[_key];
  }

  var arity =
    arguments.length > 1 && arguments[1] !== undefined
      ? arguments[1]
      : fn.length;
  return arity <= args.length
    ? fn.apply(undefined, args)
    : curry.bind.apply(curry, [null, fn, arity].concat(args));
};
// curry(Math.pow)(2)(10) -> 1024
// curry(Math.min, 3)(10)(50)(2) -> 2
```
[⬆ back to top](#table-of-contents)

### Pipe

Use `Array.reduce()` to pass value through functions.

- ES6
```js
const pipe = (...funcs) => arg => funcs.reduce((acc, func) => func(acc), arg);
// pipe(btoa, x => x.toUpperCase())("Test") -> "VGVZDA=="
```
- ES6
```js
var pipe = function pipe() {
  for (
    var _len = arguments.length, funcs = Array(_len), _key = 0;
    _key < _len;
    _key++
  ) {
    funcs[_key] = arguments[_key];
  }

  return function(arg) {
    return funcs.reduce(function(acc, func) {
      return func(acc);
    }, arg);
  };
};
// pipe(btoa, x => x.toUpperCase())("Test") -> "VGVZDA=="
```
[⬆ back to top](#table-of-contents)

### Promisify

Use currying to return a function returning a `Promise` that calls the original function. 
Use the `...rest` operator to pass in all the parameters. 

*In Node 8+, you can use [`util.promisify`](https://nodejs.org/api/util.html#util_util_promisify_original)*

- ES6
```js
const promisify = func =>
  (...args) =>
    new Promise((resolve, reject) =>
      func(...args, (err, result) =>
        err ? reject(err) : resolve(result))
    );
// const delay = promisify((d, cb) => setTimeout(cb, d))
// delay(2000).then(() => console.log('Hi!')) -> Promise resolves after 2s
```
- ES6
```js
var promisify = function promisify(func) {
  return function() {
    for (
      var _len = arguments.length, args = Array(_len), _key = 0;
      _key < _len;
      _key++
    ) {
      args[_key] = arguments[_key];
    }

    return new Promise(function(resolve, reject) {
      return func.apply(
        undefined,
        args.concat([
          function(err, result) {
            return err ? reject(err) : resolve(result);
          }
        ])
      );
    });
  };
};
// const delay = promisify((d, cb) => setTimeout(cb, d))
// delay(2000).then(() => console.log('Hi!')) -> Promise resolves after 2s
```
[⬆ back to top](#table-of-contents)

### Run promises in series

Run an array of promises in series using `Array.reduce()` by creating a promise chain, where each promise returns the next promise when resolved.

- ES6
```js
const series = ps => ps.reduce((p, next) => p.then(next), Promise.resolve());
// const delay = (d) => new Promise(r => setTimeout(r, d))
// series([() => delay(1000), () => delay(2000)]) -> executes each promise sequentially, taking a total of 3 seconds to complete
```
- ES6
```js
var series = function series(ps) {
  return ps.reduce(function(p, next) {
    return p.then(next);
  }, Promise.resolve());
};
// const delay = (d) => new Promise(r => setTimeout(r, d))
// series([() => delay(1000), () => delay(2000)]) -> executes each promise sequentially, taking a total of 3 seconds to complete
```
[⬆ back to top](#table-of-contents)

### Sleep

Delay executing part of an `async` function, by putting it to sleep, returning a `Promise`.

- ES6
```js
const sleep = ms => new Promise(resolve => setTimeout(resolve, ms));
/*
async function sleepyWork() {
  console.log('I\'m going to sleep for 1 second.');
  await sleep(1000);
  console.log('I woke up after 1 second.');
}
*/
```
- ES6
```js
var sleep = function sleep(ms) {
  return new Promise(function(resolve) {
    return setTimeout(resolve, ms);
  });
};
/*
async function sleepyWork() {
  console.log('I\'m going to sleep for 1 second.');
  await sleep(1000);
  console.log('I woke up after 1 second.');
}
*/
```
[⬆ back to top](#table-of-contents)
## Math

### Collatz algorithm

If `n` is even, return `n/2`. Otherwise  return `3n+1`.

- ES6
```js
const collatz = n => (n % 2 == 0) ? (n / 2) : (3 * n + 1);
// collatz(8) --> 4
// collatz(5) --> 16
```
- ES6
```js
var collatz = function collatz(n) {
  return n % 2 == 0 ? n / 2 : 3 * n + 1;
};
// collatz(8) --> 4
// collatz(5) --> 16
```
[⬆ back to top](#table-of-contents)

### Distance between two points

Use `Math.hypot()` to calculate the Euclidean distance between two points.

- ES6
```js
const distance = (x0, y0, x1, y1) => Math.hypot(x1 - x0, y1 - y0);
// distance(1,1, 2,3) -> 2.23606797749979
```
- ES6
```js
var distance = function distance(x0, y0, x1, y1) {
  return Math.hypot(x1 - x0, y1 - y0);
};
// distance(1,1, 2,3) -> 2.23606797749979
```
[⬆ back to top](#table-of-contents)

### Divisible by number

Use the modulo operator (`%`) to check if the remainder is equal to `0`.

- ES6
```js
const isDivisible = (dividend, divisor) => dividend % divisor === 0;
// isDivisible(6,3) -> true
```
- ES6
```js
var isDivisible = function isDivisible(dividend, divisor) {
  return dividend % divisor === 0;
};
// isDivisible(6,3) -> true
```
[⬆ back to top](#table-of-contents)

### Even or odd number

Checks whether a number is odd or even using the modulo (`%`) operator.
Returns `true` if the number is even, `false` if the number is odd.

- ES6
```js
const isEven = num => num % 2 === 0;
// isEven(3) -> false
```
- ES6
```js
var isEven = function isEven(num) {
  return num % 2 === 0;
};
// isEven(3) -> false
```
[⬆ back to top](#table-of-contents)

### Factorial

Use recursion.
If `n` is less than or equal to `1`, return `1`.
Otherwise, return the product of `n` and the factorial of `n - 1`.

- ES6
```js
const factorial = n => n <= 1 ? 1 : n * factorial(n - 1);
// factorial(6) -> 720
```
- ES6
```js
var factorial = function factorial(n) {
  return n <= 1 ? 1 : n * factorial(n - 1);
};
// factorial(6) -> 720
```
[⬆ back to top](#table-of-contents)

### Fibonacci array generator

Create an empty array of the specific length, initializing the first two values (`0` and `1`).
Use `Array.reduce()` to add values into the array, using the sum of the last two values, except for the first two.

- ES6
```js
const fibonacci = n =>
  Array(n).fill(0).reduce((acc, val, i) => acc.concat(i > 1 ? acc[i - 1] + acc[i - 2] : i), []);
// fibonacci(5) -> [0,1,1,2,3]
```
- ES6
```js
var fibonacci = function fibonacci(n) {
  return Array(n)
    .fill(0)
    .reduce(function(acc, val, i) {
      return acc.concat(i > 1 ? acc[i - 1] + acc[i - 2] : i);
    }, []);
};
// fibonacci(5) -> [0,1,1,2,3]
```
[⬆ back to top](#table-of-contents)

### Greatest common divisor (GCD)

Use recursion.
Base case is when `y` equals `0`. In this case, return `x`.
Otherwise, return the GCD of `y` and the remainder of the division `x/y`.

- ES6
```js
const gcd = (x, y) => !y ? x : gcd(y, x % y);
// gcd (8, 36) -> 4
```
- ES6
```js
var gcd = function gcd(x, y) {
  return !y ? x : gcd(y, x % y);
};
// gcd (8, 36) -> 4
```
[⬆ back to top](#table-of-contents)

### Hamming distance

Use XOR operator (`^`) to find the bit difference between the two numbers, convert to binary string using `toString(2)`.
Count and return the number of `1`s in the string, using `match(/1/g)`.

- ES6
```js
const hammingDistance = (num1, num2) =>
  ((num1 ^ num2).toString(2).match(/1/g) || '').length;
// hammingDistance(2,3) -> 1
```
- ES6
```js
var hammingDistance = function hammingDistance(num1, num2) {
  return ((num1 ^ num2).toString(2).match(/1/g) || "").length;
};
// hammingDistance(2,3) -> 1
```
[⬆ back to top](#table-of-contents)

### Percentile

Use `Array.reduce()` to calculate how many numbers are below the value and how many are the same value and
apply the percentile formula.

- ES6
```js
const percentile = (arr, val) => 
  100 * arr.reduce((acc,v) => acc + (v < val ? 1 : 0) + (v === val ? 0.5 : 0), 0) / arr.length;
// percentile([1,2,3,4,5,6,7,8,9,10], 6) -> 55
 ```
- ES6
```js
var percentile = function percentile(arr, val) {
  return (
    100 *
    arr.reduce(function(acc, v) {
      return acc + (v < val ? 1 : 0) + (v === val ? 0.5 : 0);
    }, 0) /
    arr.length
  );
};
// percentile([1,2,3,4,5,6,7,8,9,10], 6) -> 55
 ```
[⬆ back to top](#table-of-contents)

### Powerset

Use `Array.reduce()` combined with `Array.map()` to iterate over elements and combine into an array containing all combinations.

- ES6
```js
const powerset = arr =>
  arr.reduce((a, v) => a.concat(a.map(r => [v].concat(r))), [[]]);
// powerset([1,2]) -> [[], [1], [2], [2,1]]
```
- ES6
```js
var powerset = function powerset(arr) {
  return arr.reduce(
    function(a, v) {
      return a.concat(
        a.map(function(r) {
          return [v].concat(r);
        })
      );
    },
    [[]]
  );
};
// powerset([1,2]) -> [[], [1], [2], [2,1]]
```
[⬆ back to top](#table-of-contents)

### Round number to n digits

Use `Math.round()` and template literals to round the number to the specified number of digits.
Omit the second argument, `decimals` to round to an integer.

- ES6
```js
const round = (n, decimals=0) => Number(`${Math.round(`${n}e${decimals}`)}e-${decimals}`);
// round(1.005, 2) -> 1.01
```
- ES6
```js
var round = function round(n) {
  var decimals =
    arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : 0;
  return Number(Math.round(n + "e" + decimals) + "e-" + decimals);
};
// round(1.005, 2) -> 1.01
```
[⬆ back to top](#table-of-contents)

### Standard deviation

Use `Array.reduce()` to calculate the mean, variance and the sum of the variance of the values, the variance of the values, then
determine the standard deviation.
You can omit the second argument to get the sample standard deviation or set it to `true` to get the population standard deviation.

- ES6
```js
const standardDeviation = (arr, usePopulation = false) => {
  const mean = arr.reduce((acc, val) => acc + val, 0) / arr.length;
  return Math.sqrt(
    arr.reduce((acc, val) => acc.concat(Math.pow(val - mean, 2)), [])
       .reduce((acc, val) => acc + val, 0) / (arr.length - (usePopulation ? 0 : 1))
  );
};
// standardDeviation([10,2,38,23,38,23,21]) -> 13.284434142114991 (sample)
// standardDeviation([10,2,38,23,38,23,21], true) -> 12.29899614287479 (population)
```
- ES6
```js
var standardDeviation = function standardDeviation(arr) {
  var usePopulation =
    arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : false;

  var mean =
    arr.reduce(function(acc, val) {
      return acc + val;
    }, 0) / arr.length;
  return Math.sqrt(
    arr
      .reduce(function(acc, val) {
        return acc.concat(Math.pow(val - mean, 2));
      }, [])
      .reduce(function(acc, val) {
        return acc + val;
      }, 0) /
      (arr.length - (usePopulation ? 0 : 1))
  );
};
// standardDeviation([10,2,38,23,38,23,21]) -> 13.284434142114991 (sample)
// standardDeviation([10,2,38,23,38,23,21], true) -> 12.29899614287479 (population)
```
[⬆ back to top](#table-of-contents)
## Media

### Speech synthesis (experimental)

Use `SpeechSynthesisUtterance.voice` and `indow.speechSynthesis.getVoices()` to convert a message to speech.
Use `window.speechSynthesis.speak()` to play the message.

Learn more about the [SpeechSynthesisUtterance interface of the Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesisUtterance).

- ES6
```js
const speak = message => {
  const msg = new SpeechSynthesisUtterance(message);
  msg.voice = window.speechSynthesis.getVoices()[0];
  window.speechSynthesis.speak(msg);
};
// speak('Hello, World') -> plays the message
```
- ES6
```js
var speak = function speak(message) {
  var msg = new SpeechSynthesisUtterance(message);
  msg.voice = window.speechSynthesis.getVoices()[0];
  window.speechSynthesis.speak(msg);
};
// speak('Hello, World') -> plays the message
```
[⬆ back to top](#table-of-contents)
## Object

### Object from key-value pairs

Use `Array.reduce()` to create and combine key-value pairs.

- ES6
```js
const objectFromPairs = arr => arr.reduce((a, v) => (a[v[0]] = v[1], a), {});
// objectFromPairs([['a',1],['b',2]]) -> {a: 1, b: 2}
```
- ES6
```js
var objectFromPairs = function objectFromPairs(arr) {
  return arr.reduce(function(a, v) {
    return (a[v[0]] = v[1]), a;
  }, {});
};
// objectFromPairs([['a',1],['b',2]]) -> {a: 1, b: 2}
```
[⬆ back to top](#table-of-contents)

### Object to key-value pairs

Use `Object.keys()` and `Array.map()` to iterate over the object's keys and produce an array with key-value pairs.

- ES6
```js
const objectToPairs = obj => Object.keys(obj).map(k => [k, obj[k]]);
// objectToPairs({a: 1, b: 2}) -> [['a',1],['b',2]])
```
- ES6
```js
var objectToPairs = function objectToPairs(obj) {
  return Object.keys(obj).map(function(k) {
    return [k, obj[k]];
  });
};
// objectToPairs({a: 1, b: 2}) -> [['a',1],['b',2]])
```
[⬆ back to top](#table-of-contents)

### Shallow clone object

Use the object `...spread` operator to spread the properties of the target object into the clone.

- ES6
```js
const shallowClone = obj => ({ ...obj });
/*
const a = { x: true, y: 1 };
const b = shallowClone(a);
a === b -> false
*/
```
[⬆ back to top](#table-of-contents)
## String

### Anagrams of string (with duplicates)

Use recursion.
For each letter in the given string, create all the partial anagrams for the rest of its letters.
Use `Array.map()` to combine the letter with each partial anagram, then `Array.reduce()` to combine all anagrams in one array.
Base cases are for string `length` equal to `2` or `1`.

- ES6
```js
const anagrams = str => {
  if (str.length <= 2) return str.length === 2 ? [str, str[1] + str[0]] : [str];
  return str.split('').reduce((acc, letter, i) =>
    acc.concat(anagrams(str.slice(0, i) + str.slice(i + 1)).map(val => letter + val)), []);
};
// anagrams('abc') -> ['abc','acb','bac','bca','cab','cba']
```
- ES6
```js
var anagrams = function anagrams(str) {
  if (str.length <= 2) return str.length === 2 ? [str, str[1] + str[0]] : [str];
  return str.split("").reduce(function(acc, letter, i) {
    return acc.concat(
      anagrams(str.slice(0, i) + str.slice(i + 1)).map(function(val) {
        return letter + val;
      })
    );
  }, []);
};
// anagrams('abc') -> ['abc','acb','bac','bca','cab','cba']
```
[⬆ back to top](#table-of-contents)

### Capitalize first letter of every word

Use `replace()` to match the first character of each word and `toUpperCase()` to capitalize it.

- ES6
```js
const capitalizeEveryWord = str => str.replace(/\b[a-z]/g, char => char.toUpperCase());
// capitalizeEveryWord('hello world!') -> 'Hello World!'
```
- ES6
```js
var capitalizeEveryWord = function capitalizeEveryWord(str) {
  return str.replace(/\b[a-z]/g, function(char) {
    return char.toUpperCase();
  });
};
// capitalizeEveryWord('hello world!') -> 'Hello World!'
```
[⬆ back to top](#table-of-contents)

### Capitalize first letter

Use `slice(0,1)` and `toUpperCase()` to capitalize first letter, `slice(1)` to get the rest of the string.
Omit the `lowerRest` parameter to keep the rest of the string intact, or set it to `true` to convert to lower case.

- ES6
```js
const capitalize = (str, lowerRest = false) =>
  str.slice(0, 1).toUpperCase() + (lowerRest ? str.slice(1).toLowerCase() : str.slice(1));
// capitalize('myName', true) -> 'Myname'
```
- ES6
```js
var capitalize = function capitalize(str) {
  var lowerRest =
    arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : false;
  return (
    str.slice(0, 1).toUpperCase() +
    (lowerRest ? str.slice(1).toLowerCase() : str.slice(1))
  );
};
// capitalize('myName', true) -> 'Myname'
```
[⬆ back to top](#table-of-contents)

### Check for palindrome

Convert string `toLowerCase()` and use `replace()` to remove non-alphanumeric characters from it.
Then, `split('')` into individual characters, `reverse()`, `join('')` and compare to the original, unreversed string, after converting it `tolowerCase()`.

- ES6
```js
const palindrome = str => {
  const s = str.toLowerCase().replace(/[\W_]/g,'');
  return s === s.split('').reverse().join('');
}
// palindrome('taco cat') -> true
 ```
- ES6
```js
var palindrome = function palindrome(str) {
  var s = str.toLowerCase().replace(/[\W_]/g, "");
  return (
    s ===
    s
      .split("")
      .reverse()
      .join("")
  );
};
// palindrome('taco cat') -> true
 ```
[⬆ back to top](#table-of-contents)

### Reverse a string

Use array destructuring and `Array.reverse()` to reverse the order of the characters in the string.
Combine characters to get a string using `join('')`.

- ES6
```js
const reverseString = str => [...str].reverse().join('');
// reverseString('foobar') -> 'raboof'
```

[⬆ back to top](#table-of-contents)

### Sort characters in string (alphabetical)

Split the string using `split('')`, `Array.sort()` utilizing `localeCompare()`, recombine using `join('')`.

- ES6
```js
const sortCharactersInString = str =>
  str.split('').sort((a, b) => a.localeCompare(b)).join('');
// sortCharactersInString('cabbage') -> 'aabbceg'
```

[⬆ back to top](#table-of-contents)

### Truncate a String

Determine if the string's `length` is greater than `num`.
Return the string truncated to the desired length, with `...` appended to the end or the original string.

- ES6
```js
const truncate = (str, num) =>
  str.length > num ? str.slice(0, num > 3 ? num - 3 : num) + '...' : str;
// truncate('boomerang', 7) -> 'boom...'
```

[⬆ back to top](#table-of-contents)
## Utility

### Escape regular expression

Use `replace()` to escape special characters.

- ES6
```js
const escapeRegExp = str => str.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
// escapeRegExp('(test)') -> \\(test\\)
```

[⬆ back to top](#table-of-contents)

### Get native type of value

Returns lower-cased constructor name of value, "undefined" or "null" if value is undefined or null

- ES6
```js
const getType = v =>
  v === undefined ? 'undefined' : v === null ? 'null' : v.constructor.name.toLowerCase();
// getType(new Set([1,2,3])) -> "set"
```

[⬆ back to top](#table-of-contents)

### Is array

Use `Array.isArray()` to check if a value is classified as an array.

- ES6
```js
const isArray = val => !!val && Array.isArray(val);
// isArray(null) -> false
// isArray([1]) -> true
```

[⬆ back to top](#table-of-contents)

### Is boolean

Use `typeof` to check if a value is classified as a boolean primitive.

- ES6
```js
const isBoolean = val => typeof val === 'boolean';
// isBoolean(null) -> false
// isBoolean(false) -> true
```

[⬆ back to top](#table-of-contents)

### Is function

Use `typeof` to check if a value is classified as a function primitive.

- ES6
```js
const isFunction = val => val && typeof val === 'function';
// isFunction('x') -> false
// isFunction(x => x) -> true
```

[⬆ back to top](#table-of-contents)

### Is number

Use `typeof` to check if a value is classified as a number primitive.

- ES6
```js
const isNumber = val => typeof val === 'number';
// isNumber('1') -> false
// isNumber(1) -> true
```

[⬆ back to top](#table-of-contents)

### Is string

Use `typeof` to check if a value is classified as a string primitive.

- ES6
```js
const isString = val => typeof val === 'string';
// isString(10) -> false
// isString('10') -> true
```

[⬆ back to top](#table-of-contents)

### Is symbol

Use `typeof` to check if a value is classified as a symbol primitive.

- ES6
```js
const isSymbol = val => typeof val === 'symbol';
// isSymbol('x') -> false
// isSymbol(Symbol('x')) -> true
```

[⬆ back to top](#table-of-contents)

### Measure time taken by function

Use `console.time()` and `console.timeEnd()` to measure the difference between the start and end times to determine how long the callback took to execute.

- ES6
```js
const timeTaken = callback => {
  console.time('timeTaken');
  const r = callback();
  console.timeEnd('timeTaken');
  return r;
};
// timeTaken(() => Math.pow(2, 10)) -> 1024
// (logged): timeTaken: 0.02099609375ms
```

[⬆ back to top](#table-of-contents)

### Number to array of digits

Convert the number to a string, use `split()` to convert build an array.
Use `Array.map()` and `parseInt()` to transform each value to an integer. 

- ES6
```js
const digitize = n => (''+n).split('').map(i => parseInt(i));
// digitize(2334) -> [2, 3, 3, 4]
```

[⬆ back to top](#table-of-contents)

### Ordinal suffix of number

Use the modulo operator (`%`) to find values of single and tens digits.
Find which ordinal pattern digits match.
If digit is found in teens pattern, use teens ordinal.

- ES6
```js
const toOrdinalSuffix = num => {
  const int = parseInt(num), digits = [(int % 10), (int % 100)],
    ordinals = ['st', 'nd', 'rd', 'th'], oPattern = [1, 2, 3, 4],
    tPattern = [11, 12, 13, 14, 15, 16, 17, 18, 19];
  return oPattern.includes(digits[0]) && !tPattern.includes(digits[1]) ? int + ordinals[digits[0] - 1] : int + ordinals[3];
};
// toOrdinalSuffix("123") -> "123rd"
```

[⬆ back to top](#table-of-contents)

### Random integer in range

Use `Math.random()` to generate a random number and map it to the desired range, using `Math.floor()` to make it an integer.

- ES6
```js
const randomIntegerInRange = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;
// randomIntegerInRange(0, 5) -> 2
```

[⬆ back to top](#table-of-contents)

### Random number in range

Use `Math.random()` to generate a random value, map it to the desired range using multiplication.

- ES6
```js
const randomInRange = (min, max) => Math.random() * (max - min) + min;
// randomInRange(2,10) -> 6.0211363285087005
```

[⬆ back to top](#table-of-contents)

### RGB to hexadecimal

Convert given RGB parameters to hexadecimal string using bitwise left-shift operator (`<<`) and `toString(16)`, then `padStart(6,'0')` to get a 6-digit hexadecimal value.

- ES6
```js
const rgbToHex = (r, g, b) => ((r << 16) + (g << 8) + b).toString(16).padStart(6, '0');
// rgbToHex(255, 165, 1) -> 'ffa501'
```

[⬆ back to top](#table-of-contents)

### Swap values of two variables

Use array destructuring to swap values between two variables.

- ES6
```js
[varA, varB] = [varB, varA];
// [x, y] = [y, x]
```

[⬆ back to top](#table-of-contents)

### URL parameters

Use `match()` with an appropriate regular expression to get all key-value pairs, `Array.reduce()` to map and combine them into a single object.
Pass `location.search` as the argument to apply to the current `url`.

- ES6
```js
const getUrlParameters = url =>
  url.match(/([^?=&]+)(=([^&]*))/g).reduce(
    (a, v) => (a[v.slice(0, v.indexOf('='))] = v.slice(v.indexOf('=') + 1), a), {}
  );
// getUrlParameters('http://url.com/page?name=Adam&surname=Smith') -> {name: 'Adam', surname: 'Smith'}
```

[⬆ back to top](#table-of-contents)

### UUID generator

Use `crypto` API to generate a UUID, compliant with [RFC4122](https://www.ietf.org/rfc/rfc4122.txt) version 4.

- ES6
```js
const uuid = _ =>
  ([1e7] + -1e3 + -4e3 + -8e3 + -1e11).replace(/[018]/g, c =>
    (c ^ crypto.getRandomValues(new Uint8Array(1))[0] & 15 >> c / 4).toString(16)
  );
// uuid() -> '7982fcfe-5721-4632-bede-6000885be57d'
```

[⬆ back to top](#table-of-contents)

### Validate email

Use a regular experssion to check if the email is valid.
Returns `true` if email is valid, `false` if not.

- ES6
```js
const validateEmail = str =>
  /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(str);
// validateEmail(mymail@gmail.com) -> true
```

[⬆ back to top](#table-of-contents)

### Validate number

Use `!isNaN` in combination with `parseFloat()` to check if the argument is a number.
Use `isFinite()` to check if the number is finite.
Use `Number()` to check if the coercion holds.

- ES6
```js
const validateNumber = n => !isNaN(parseFloat(n)) && isFinite(n) && Number(n) == n;
// validateNumber('10') -> true
```

[⬆ back to top](#table-of-contents)

### Value or default

Returns value, or default value if passed value is `falsy`.

- ES6
```js
const valueOrDefault = (value, d) => value || d;
// valueOrDefault(NaN, 30) -> 30
```

[⬆ back to top](#table-of-contents)

## Credits

*Icons made by [Smashicons](https://www.flaticon.com/authors/smashicons) from [www.flaticon.com](https://www.flaticon.com/) is licensed by [CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/).*

