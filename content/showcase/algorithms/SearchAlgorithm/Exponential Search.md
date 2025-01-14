+++
title = "Exponential Search"
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

# Exponential Search

<!--more-->

#### Prerequisites

- [Binary Search algorithm](https://github.com/faridevnz/Algorithms-Explanation/blob/master/en/Search%20Algorithms/Binary%20Search.md)

#### Problem Statement

Given a sorted array of _n_ elements, write a function to search for the index of a given element (target)

#### Approach

- Search for the **range** within which the target is included increasing _index_ by powers of 2
- If this range exists in array apply the Binary Search algorithm over it
- Else return -1

#### Example

```markdown
arr = [1, 2, 3, 4, 5, 6, 7, ... 998, 999, 1_000]

target = 998
index = 0

1. SEARCHING FOR THE RANGE
   index = 1, 2, 4, 8, 16, 32, 64, ..., 512, ..., 1_024
   after 10 iteration we have the index at 1_024 and outside of the array
2. BINARY SEARCH
   Now we can apply the binary search on the subarray from 512 and 1_000.
```

**_Note_**: we apply the Binary Search from 512 to 1_000 because at `i = 2^10 = 1_024` the array is finisced and the target number is less than the latest index of the array ( 1_000 ).

#### Time Complexity

**worst case:** `O(log *i*)` where `*i* = index` (position) of the target

**best case:** `O(*1*)`

#### Complexity Explanation

- The complexity of the first part of the algorithm is **O( log _i_ )** because if _i_ is the position of the target in the array, after doubling the search _index_ `⌈log(i)⌉` times, the algorithm will be at a search index that is greater than or equal to _i_. We can write `2^⌈log(i)⌉ >= i`
- The complexity of the second part of the algorithm also is **O ( log _i_ )** because that is a simple Binary Search. The Binary Search complexity ( as explained [here](https://github.com/faridevnz/Algorithms-Explanation/blob/master/en/Search%20Algorithms/Binary%20Search.md) ) is O( _n_ ) where _n_ is the length of the array. In the Exponential Search, the length of the array on which the algorithm is applied is `2^i - 2^(i-1)`, put into words it means '( the length of the array from start to _i_ ) - ( the part of array skipped until the previous iteration )'. Is simple verify that `2^i - 2^(i-1) = 2^(i-1)`

After this detailed explanation we can say that the the complexity of the Exponential Search is:

```mathematica
O(log i) + O(log i) = 2O(log i) = O(log i)
```

#### Binary Search vs Exponential Search

Let's take a look at this comparison with a less theoretical example. Imagine we have an array with`1_000_000` elements and we want to search an element that is in the `4th` position. It's easy to see that:

- The Binary Search start from the middle of the array and arrive to the 4th position after many iterations
- The Exponential Search arrive at the 4th index after only 2 iterations

#### Code Implementation Links

- [C++](https://github.com/TheAlgorithms/C-Plus-Plus/blob/master/search/exponential_search.cpp)
- [JavaScript](https://github.com/TheAlgorithms/Javascript/blob/master/Search/ExponentialSearch.js)

### Exponential Search Implementation

- The algorithm consists of two stages. The first stage determines a
- range in which the search key would reside if it were in the list.
- In the second stage, a binary search is performed on this range.

```JavaScript
function binarySearch (arr, value, floor, ceiling) {
  // Middle index
  const mid = Math.floor((floor + ceiling) / 2)

  // If value is at the mid position return this position
  if (arr[mid] === value) {
    return mid
  }

  if (floor > ceiling) return -1

  // If the middle element is great than the value
  // search the left part of the array
  if (arr[mid] > value) {
    return binarySearch(arr, value, floor, mid - 1)
    // If the middle element is lower than the value
    // search the right part of the array
  } else {
    return binarySearch(arr, value, mid + 1, ceiling)
  }
}

function exponentialSearch (arr, length, value) {
  // If value is the first element of the array return this position
  if (arr[0] === value) {
    return 0
  }

  // Find range for binary search
  let i = 1
  while (i < length && arr[i] <= value) {
    i = i * 2
  }

  // Call binary search for the range found above
  return binarySearch(arr, value, i / 2, Math.min(i, length))
}

export { binarySearch, exponentialSearch }

// const arr = [2, 3, 4, 10, 40, 65, 78, 100]
// const value = 78
// const result = exponentialSearch(arr, arr.length, value)

```
