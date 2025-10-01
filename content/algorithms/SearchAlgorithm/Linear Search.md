+++
title = "Linear Search"
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

# Linear Search

#### Problem Statement

Given an array of n elements, write a function to search for the index of a given element (target)

<!--more-->

#### Approach

- Start iterating with the first element in the array.
- Compare it with the target element
- If it is equal to the target element then return the index
- Else continue iterating
- Return -1 if target element is not found in the array

#### Time Complexity

O(n) Worse Case  
O(1) Best Case (If first element of array is the target element)

#### Space Complexity

O(1)

#### Example

```
arr = [1, 3, 9, 5, 0, 2]

target = 5
Linear Search should return index 3 as 5 is on index 3

target = 6
Linear Search should return -1 as 6 is not present in the array
```

#### Code Implementation Links

- [Java](https://github.com/TheAlgorithms/Java/blob/master/Searches/LinearSearch.java)
- [C++](https://github.com/TheAlgorithms/C-Plus-Plus/blob/master/Search/Linear%20Search.cpp)
- [Python](https://github.com/TheAlgorithms/Python/blob/master/searches/linear_search.py)

#### Video Explanation

[A CS50 video explaining the Linear Search Algorithm](https://www.youtube.com/watch?v=CX2CYIJLwfg)

#### Animation Explanation

- [Tute Board](https://boardhub.github.io/tute/?wd=linearSearchAlgo)

- Linear search or sequential search is a method for finding a target value within a list. It sequentially checks each element of the list for the target value until a match is found or until all the elements have been searched.

```javascript
function SearchArray(searchNum, ar, output = (v) => console.log(v)) {
  const position = Search(ar, searchNum);
  if (position !== -1) {
    output("The element was found at " + (position + 1));
  } else {
    output("The element not found");
  }
}

// Search “theArray” for the specified “key” value
function Search(theArray, key) {
  for (let n = 0; n < theArray.length; n++) {
    if (theArray[n] === key) {
      return n;
    }
  }
  return -1;
}

export { SearchArray, Search };

// const ar = [1, 2, 3, 4, 5, 6, 7, 8, 9]
// SearchArray(3, ar)
// SearchArray(4, ar)
// SearchArray(11, ar)
```
