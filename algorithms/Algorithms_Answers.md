Add your answers to the Algorithms exercises here.

# Analysis of Algorithms

## Exercise I.

### a)

```
a = 0;
while (a < n * n * n)
  a = a + n * n;
```

O(n), because it takes n operations for a to equal n<sup>3</sup>.

### b)

```
// input array is of length n
i = array.length - 1;
while (array[i] > x && i >= 0)
  i = i/2;
```

O(log n). Since `i` is being halved with each loop, the number of iterations would be less than O(n).

### c)

```
sum = 0;
for (i = 0; i < Math.sqrt(n) / 2; i++)
  for ( j = i; j < 8 + i; j++)
    for (k = j; k < 8 + j; k++)
      sum++;
```

O(n<sup>½</sup>). The second and third loops will ultimately run at constant time, (*that is, the number of loops are not affected by the size of the input*), so they are not regarded when it comes to classifying time complexity. The number of iterations for the first loop is limited by `Math.sqrt()`, so it's classification is best described that way.

### d)

```
sum = 0;
  for (i = 1; i < n; i *= 2)
    for (j = 0; j < n; j++)
      sum++;
```

O(log n * n). The first loop has a `log n` relation ship with the magnitude of `n`. In each of those loops, we're doing an operation for each `n`, which means it's O(n). Together, it's O(log n * n).

### e)

```
sum = 0;
  for (i = 0; i < n; i++)
    for (j = i + 1; j < n; j++)
      for (k = j + 1; k < n; k++)
        for (l = k + 1; l < 10 + k; l++)
          sum++;
```

O(n<sup>3</sup>). The second and third loop have slightly less iterations than the first one, but generally can be classified as O(n) each. The fourth loop is not considered, because that loop will always run 9 times regardless of the magnitude of `n`.

### f) 

```
bunnyEars = function (bunnies) { // here bunnies === n
  if (bunnies === 0) return 0;
  return 2 + bunnyEars(bunnies-1);
}
```

O(n). An operation will be done on each bunny in each function call. 

### g)

```
search = function (array, arraySize, target) { // here arraySize === n
  if (arraySize > 0) {
    if (array[arraySize-1] === target) return true;
    else return search(array, arraySize-1, target);
  }
  return false;
}
```

O(n).

## Exercise II:

a)   Given an array `a` of `n` numbers, design a linear running time algorithm to find the maximum value of `a[j] - a[i]`, where `j ≥ i`.

*Answer pending*

b) Suppose that you have an `n`-story building and plenty of eggs.  Suppose also that an egg is broken if it is thrown off floor `f` or higher, and unbroken otherwise.  Devise a strategy to determine the value of `f` such that the number of dropped eggs is minimized.

In other words, the question is asking how would you find `f`: the floor at which the eggs will start breaking. You could try dropping eggs from each floor and find `f` that way, but it's almost certain that the eggs will not break at floor `1`, and it will almost certainly break at floor `n`. So starting at the ends is inefficient; it's best we start at the median floor.

When we start at the median floor, we can go up and down one floor at a time, but it's probably to keep hopping from mid-point to mid-point, like finding at the median the egg doesn't break, so go to the median floor between the original median and the top and trying again. Once we find a break in our example, we start pinpointing `f` from there.

## Exercise III.

Below is the the pseudo-code for the Quicksort algorithm:

```
function quicksort(array)
  if length(array) <= 1
    return array
  select and remove a pivot element pivot from array
  create empty lists less and greater
  for each x in array
    if x <= pivot then append x to less
    else append x to greater
  return concatenate(quicksort(less), list(pivot), quicksort(greater))
```

a)   Suppose we implement quicksort so that the pivot is always chosen to be the first element of the array.
What is the running time of this algorithm on an input array that is already sorted?  Why?

O(n<sup>2</sup>). Because the elements are not evenly distributed to the `quicksort(less)` and `quicksort(greater)` function calls, `quicksort(greater)` needs to run more times to return the sorted array.

b)   Suppose we implement quicksort so that the pivot is always magically chosen to be the median element
of the array.  What is the running time of this algorithm?  Why?

Assuming concatenation has no runtime implication, the runtime complexity is O(n log n). The answer is like the above, but in this case, both `quicksort(greater)` and `quicksort(lesser)` is called during the process. However, because the median is magically chosen each time, the n for each of the subsequent calls between `less` and `greater` is split evenly.