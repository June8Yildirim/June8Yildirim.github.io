+++
title = "Interpolation Search"
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

## Interpolation Search

<!--more-->

- Time Complexity:
- -Best case: O(1)
- -Worst case: O(n)
- -O((log(log(n))) If the data are uniformly distributed

```javascript
export function interpolationSearch(arr, key) {
  const length = arr.length - 1;
  let low = 0;
  let high = length;
  let position = -1;
  let delta = -1;

  // Because the array is sorted the key must be between low and high
  while (low <= high && key >= arr[low] && key <= arr[high]) {
    delta = (key - arr[low]) / (arr[high] - arr[low]);
    position = low + Math.floor((high - low) * delta);

    // Target found return its position
    if (arr[position] === key) {
      return position;
    }

    // If the key is larger then it is in the upper part of the array
    if (arr[position] < key) {
      low = position + 1;
      // If the key is smaller then it is in the lower part of the array
    } else {
      high = position - 1;
    }
  }

  return -1;
}

// const arr = [2, 6, 8, 10, 12, 14, 16, 18, 20, 22, 26, 34, 39]

// interpolationSearch(arr, 2)
// interpolationSearch(arr, 12)
// interpolationSearch(arr, 1000)
// interpolationSearch(arr, 39)
```
