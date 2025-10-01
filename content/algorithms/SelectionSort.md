+++
title = "SelectionSort"
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

## Selection Sort

Selection Sort divides the array into sorted and unsorted parts. It repeatedly selects the smallest (or largest) element from the unsorted part and moves it to the sorted part.

<!--more-->

#### Approach

- select the smallest element from the array
- put it at the beginning of the array
- then select the smallest array from the remaining unsorted list
- append it to the sorted array at the beginning
- keep doing this for every element of the array
- repeat the above process n times

```java
public class SelectionSort {
    public static void selectionSort(int[] array) {
        int n = array.length;
        for (int i = 0; i < n - 1; i++) {
            int minIndex = i;
            for (int j = i + 1; j < n; j++) {
                if (array[j] < array[minIndex]) {
                    minIndex = j;
                }
            }
            // Swap the found minimum element with the first element
            int temp = array[minIndex];
            array[minIndex] = array[i];
            array[i] = temp;
        }
    }
}

```

### Complexity

- Best/Worst/Average case: O(n2)
- Space complexity: O(1)

#### Example

```
arr[] = {80, 10, 40, 30}
Indexes: 0   1   2   3

1. Index = 0
 Select the minimum number from the array (between index 0-3), ie, 10
2. Swap 10  and 80 (arr[0])
3. The array now is {10, 80, 40, 30}

4. Index = 1
 Select the minimum number from the array (between index 1-3), ie, 30
5. Swap 30 and 80 (arr[1])
6. The array now is {10, 30, 40, 80}

7. Index = 2
 Select the minimum number from the array (between index 2-3), ie, 40
8. Swap 40 and 40 (arr[2])
9. The array now is {10, 30, 40, 80}

The array is now sorted.
```

#### Code Implementation Links

- [Java](https://github.com/TheAlgorithms/Java/blob/master/Sorts/SelectionSort.java)
- [Python](https://github.com/TheAlgorithms/Python/blob/master/sorts/selection_sort.py)
- [Go](https://github.com/TheAlgorithms/Go/blob/master/sorts/selection_sort.go)
- [Javascript](https://github.com/TheAlgorithms/Javascript/blob/master/Sorts/selectionSort.js)

#### Video Explanation

[A video explaining the Selection Sort Algorithm](https://www.youtube.com/watch?v=f8hXR_Hvybo)

#### Animation Explanation

- [Tute Board](https://boardhub.github.io/tute/?wd=selectSortAlgo2)
