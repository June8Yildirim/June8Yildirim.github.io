+++
title = "Binary Search"
date = "2024-12-12T15:50:48-05:00"
author = ""
authorTwitter = "" #do not include @
cover = ""
coverCaption = ""
tags = ["", ""]
keywords = ["", ""]
description = ""
showFullContent = false
readingTime = false
hideComments = false
color = "" #color from the theme settings
+++

# Binary Search (A divide and conquer algorithm)

#### Problem Statement

Given a sorted array of n elements, write a function to search for the index of a given element (target)

<!--more-->

#### Approach

- Search for the array by dividing the array in half repeatedly.
- Initially consider the actual array and pick the element at the middle index
- Keep a lower index i.e. 0 and higher index i.e. length of array
- If it is equal to the target element then return the index
- Else if it is greater than the target element then consider only the left half of array. (lower index = 0, higher = middle - 1)
- Else if it is less than the target element then consider only the right half of array. (lower index = middle + 1, higher = length of array)
- Return -(insertion index + 1) if the target element is not found in the array (If the lower index is greater than or equal to higher index). Some simpler implementations just return -1 if the element is not found. The offset of 1 must be added as the insertion index might be 0 (the searched value might be smaller than all elements in the array). As indexing starts at 0, this must be distinguishable from the case where the target element has the index 0.

#### Time Complexity

O(log n) Worst Case  
O(1) Best Case (If middle element of initial array is the target element)

#### Space Complexity

O(1) For iterative approach  
O(1) For recursive approach _if tail call optimization is used_, O(log n) due to recursion call stack, otherwise

#### Example

```
arr = [1,2,3,4,5,6,7]

target = 2
Initially the element at middle index is 4 which is greater than 2. Therefore we search the left half of the
array i.e. [1,2,3].
Here we find the middle element equal to target element so we return its index i.e. 1

target = 9
A simple Binary Search implementation may return -1 as 9 is not present in the array. A more complex one would return the index at which 9 would have to be inserted, which would be `-8` (last position in the array (7) plus one (7+1), negated)`.
```

#### Code Implementation Links

- [Java](https://github.com/TheAlgorithms/Java/blob/master/Searches/BinarySearch.java)
- [C++](https://github.com/TheAlgorithms/C-Plus-Plus/blob/master/Search/Binary%20Search.cpp)
- [Python](https://github.com/TheAlgorithms/Python/blob/master/searches/binary_search.py)
- [C-Sharp](https://github.com/TheAlgorithms/C-Sharp/blob/master/searches/binary_search.cs)
- [C](https://github.com/TheAlgorithms/C/blob/master/searching/Binary_Search.c)

#### Video Explanation

[A CS50 video explaining the Binary Search Algorithm](https://www.youtube.com/watch?v=5xlIPT1FRcA)

#### Animation Explanation

- [Tute Board](https://boardhub.github.io/tute/?wd=binarySearchAlgo2)

## Binary Search Implementation

[Binary Search](https://en.wikipedia.org/wiki/Binary_search_algorithm)

- Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

```javascript
function binarySearchRecursive(arr, x, low = 0, high = arr.length - 1) {
  const mid = Math.floor(low + (high - low) / 2);

  if (high >= low) {
    if (arr[mid] === x) {
      // item found => return its index
      return mid;
    }

    if (x < arr[mid]) {
      // arr[mid] is an upper bound for x, so if x is in arr => low <= x < mid
      return binarySearchRecursive(arr, x, low, mid - 1);
    } else {
      // arr[mid] is a lower bound for x, so if x is in arr => mid < x <= high
      return binarySearchRecursive(arr, x, mid + 1, high);
    }
  } else {
    // if low > high => we have searched the whole array without finding the item
    return -1;
  }
}
function binarySearchIterative(arr, x, low = 0, high = arr.length - 1) {
  while (high >= low) {
    const mid = Math.floor(low + (high - low) / 2);

    if (arr[mid] === x) {
      // item found => return its index
      return mid;
    }

    if (x < arr[mid]) {
      // arr[mid] is an upper bound for x, so if x is in arr => low <= x < mid
      high = mid - 1;
    } else {
      // arr[mid] is a lower bound for x, so if x is in arr => mid < x <= high
      low = mid + 1;
    }
  }
  // if low > high => we have searched the whole array without finding the item
  return -1;
}

export { binarySearchIterative, binarySearchRecursive };
```
