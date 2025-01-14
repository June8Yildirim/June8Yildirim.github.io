+++
title = "MergeSort"
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

## Merge Sort

Merge Sort is a divide-and-conquer algorithm that splits the array into halves, recursively sorts each half, and then merges the sorted halves.

<!--more-->

#### Approach

- Find a mid point and divide the array into to halves based on the mid point
- Recursively call the merge sort function for both the halves
- Merge the two sorted halves to get the sorted array

```java
public class MergeSort {
    public static void mergeSort(int[] array) {
        if (array.length < 2) return;
        int mid = array.length / 2;
        int[] left = new int[mid];
        int[] right = new int[array.length - mid];

        System.arraycopy(array, 0, left, 0, mid);
        System.arraycopy(array, mid, right, 0, array.length - mid);

        mergeSort(left);
        mergeSort(right);
        merge(array, left, right);
    }

private static void merge(int[] array, int[] left, int[] right) {
        int i = 0, j = 0, k = 0;
        while (i < left.length && j < right.length) {
            if (left[i] <= right[j]) {
                array[k++] = left[i++];
            } else {
                array[k++] = right[j++];
            }
        }
        while (i < left.length) {
            array[k++] = left[i++];
        }
        while (j < right.length) {
            array[k++] = right[j++];
        }
    }
}
```

### Complexity

- Best/Worst/Average case: O(n log ⁡n)
- Space complexity: O(n)

#### Example 1

```
arr = [1, 3, 9, 5, 0, 2]

Divide the array in two halves [1, 3, 9] and [5, 0, 2]

Recursively call merge sort function for both these halves which will provide sorted halves
=> [1, 3, 9] & [0, 2, 5]

Now merge both these halves to get the sorted array [0, 1, 2, 3, 5, 9]
```

#### Example 2

```
arr = [1, 9, 2, 5, 7, 3, 6, 4]

Divide the array into two halves [1, 9, 2, 5] and [7, 3, 6, 4]

As you can see that the above two halves are not yet sorted, so divide both of them into two halves again.

This time we get four arrays as [1, 9], [2, 5], [7, 3] and [6, 4].

We see that the last two arrays are again not sorted, so we divide them again into two halves and we will get [7], [3], [6], and [4].

Since an array of a single element is sorted, we now have all the arrays sorted, now we only need to merge them appropriately.

First, the arrays of one element will be merged as they were divided in last, and are at top of the recursion stack, so we get [3,7] and [4,6].

Now the merge will occur accordingly to the recursion stack, [1, 9] and [2, 5] will be merged and will make [1, 2, 5, 9].

Similarly [3, 7] and [4, 6] will be merged and made [3, 4, 6, 7].

At the next stack level [1, 2, 5, 9] and [3, 4, 6, 7] will be merged and we will get the final sorted array as [1, 2, 3, 4, 5, 6, 7, 9].
```

#### Code Implementation Links

- [Java](https://github.com/TheAlgorithms/Java/blob/master/Sorts/MergeSort.java)
- [Python](https://github.com/TheAlgorithms/Python/blob/master/sorts/merge_sort.py)
- [C-Sharp](https://github.com/TheAlgorithms/C-Sharp/blob/master/Algorithms/Sorters/Comparison/MergeSorter.cs)

#### Video Explanation

[A CS50 video explaining the Merge Sort Algorithm](https://www.youtube.com/watch?v=EeQ8pwjQxTM)
