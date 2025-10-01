+++
title = "BubbleSort"
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

## Bubble Sort

<!--more-->

#### Approach

- select the first element of the array
- compare it with its next element
- if it is larger than the next element then swap them
- else do nothing
- keep doing this for every index of the array
- repeat the above process n times.

```java
public class BubbleSort {
    public static void bubbleSort(int[] array) {
        int n = array.length;
        boolean swapped;
        for (int i = 0; i < n - 1; i++) {
            swapped = false;
            for (int j = 0; j < n - i - 1; j++) {
                if (array[j] > array[j + 1]) {
                    // Swap elements
                    int temp = array[j];
                    array[j] = array[j + 1];
                    array[j + 1] = temp;
                    swapped = true;
                }
            }
            if (!swapped) break; // Optimized - stop if no swaps
        }
    }
}
```

### Complexity

- Best case: O(n) (already sorted)
- Worst case: O(n2)
- Space complexity: O(1) (in-place sorting)

#### Example

```
arr[] = {10, 80, 40, 30}
Indexes: 0   1   2   3

1. Index = 0, Number = 10
2. 10 < 80, do nothing and continue

3. Index = 1, Number = 80
4. 80 > 40, swap 80 and 40
5. The array now is {10, 40, 80, 30}

6. Index = 2, Number = 80
7. 80 > 30, swap 80 and 30
8. The array now is {10, 40, 30, 80}

Repeat the Above Steps again

arr[] = {10, 40, 30, 80}
Indexes: 0   1   2   3

1. Index = 0, Number = 10
2. 10 < 40, do nothing and continue

3. Index = 1, Number = 40
4. 40 > 30, swap 40 and 30
5. The array now is {10, 30, 40, 80}

6. Index = 2, Number = 40
7. 40 < 80, do nothing
8. The array now is {10, 30, 40, 80}

Repeat the Above Steps again

arr[] = {10, 30, 40, 80}
Indexes: 0   1   2   3

1. Index = 0, Number = 10
2. 10 < 30, do nothing and continue

3. Index = 1, Number = 30
4. 30 < 40, do nothing and continue

5. Index = 2, Number = 40
6. 40 < 80, do nothing

Since there are no swaps in above steps, it means the array is sorted and we can stop here.
```

#### Code Implementation Links

- [Python](https://github.com/TheAlgorithms/Python/blob/master/sorts/bubble_sort.py)
- [C-Sharp](https://github.com/TheAlgorithms/C-Sharp/blob/master/Algorithms/Sorters/Comparison/BubbleSorter.cs)
- [Go](https://github.com/TheAlgorithms/Go/blob/master/sorts/bubblesort.go)
- [Javascript](https://github.com/TheAlgorithms/Javascript/blob/master/Sorts/BubbleSort.js)

#### Video Explanation

[A video explaining the Bubble Sort Algorithm](https://www.youtube.com/watch?v=Jdtq5uKz-w4)

#### Others

Bubble sort is also known as Sinking sort.

#### Animation Explanation

- [Tute Board](https://boardhub.github.io/tute/?wd=bubbleSortAlgo2)
