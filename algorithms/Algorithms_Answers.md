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

Unless `array[i] <= x` stops the loop, I think this will go on forever, because `i` will never be less than 0. Can we classify this O(∞), for that's its worst case?

Note: it's O(log n). We'll figure that out later.

### c)

```
sum = 0;
for (i = 0; i < Math.sqrt(n) / 2; i++)
  for ( j = i; j < 8 + i; j++)
    for (k = j; k < 8 + j; k++)
      sum++;
```

O(n<sup>2½</sup>). Maybe.

Note: It's just O(n<sup>½</sup>). The nested loops are constant, because the variables are tied to `i`.

### d)

```
sum = 0;
  for (i = 1; i < n; i *= 2)
    for (j = 0; j < n; j++)
      sum++;
```

Classification is O(n<sup>2</2>). 

Note: it's O(log n * n). 

### e)

```
sum = 0;
  for (i = 0; i < n; i++)
    for (j = i + 1; j < n; j++)
      for (k = j + 1; k < n; k++)
        for (l = k + 1; l < 10 + k; l++)
          sum++;
```

O(n<sup>4</sup>)?

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

O(n). Linear recursion, right?

## Exercise II:

a)   Given an array `a` of `n` numbers, design a linear running time algorithm to find the maximum value of `a[j] - a[i]`, where `j ≥ i`.

```
minVal = a[0]
maxDiff = 0

for i in 1..n
  minVal = min(minVal, a[i])
  maxDiff = max(maxDiff, a[i] - minVal)
```

b) Suppose that you have an `n`-story building and plenty of eggs.  Suppose also that an egg is broken if it is thrown off floor `f` or higher, and unbroken otherwise.  Devise a strategy to determine the value of `f` such that the number of dropped eggs is minimized.

...? `f` should be as large as possible so that the eggs will not break on any floor. It might best that the value of `f` should be ∞, but at least given that `c` is the current floor we're on, have `f` be `f > c`.

If `n` bounds the maximum value of `f`, then `f` should simply be `n`. 

Note: You misunderstood the question. `f` is unknown. It's asking to find a strategy to find `f`.

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

<del>Assuming concatenation has no runtime implication, the runtime complexity will O(n log n). The `n` because we have to iterate through the whole array. The `log n` because we will have to do subsequent iterations with the recursive call to quicksort, but `n` will be shorter each time. In an already sorted array, only `quicksort(greater)` will be called.</del>

Note: O(n<sup>2</sup>)

b)   Suppose we implement quicksort so that the pivot is always magically chosen to be the median element
of the array.  What is the running time of this algorithm?  Why?

Assuming concatenation has no runtime implication, the runtime complexity is probably still O(n log n). The answer is like the above, but in this case, both `quicksort(greater)` and `quicksort(lesser)` is called during the process. However, because the median is magically chosen each time, the n for each of the subsequent calls between `less` and `greater` is split evenly. I think this achieves O(n log n) like above, though we don't need to have a sorted list this time around.