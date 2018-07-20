Add your answers to the questions below.

1. What is the runtime complexity of your `depth_first_for_each` method?

The runtime complexity is **O(n)**. While it's doing a funky recursive thing, it's ultimately considering each node once, so it can't be any less than O(n). 

Conversely, if it was *more* than O(n), we would expect the number of elements in the output array in the test to be larger than the number of inputs (considering that the CB is only doing an O(1) operation). It isn't; the output is exactly proportional to the input. 

Thus, **O(n)** is the most apprpriate classification.

2. What is the space complexity of your `depth_first_for_each` function?

The way I've written the function is O(1). I don't explicity ask for more memory for each execution of the function. However, because the function is used recursively, the space complexity might be **O(n)**, for some memory might need to be allocated for each function call. The number of function calls is linear, so therefore the space complexity should be linear, too.

3. What is the runtime complexity of your `breadth_first_for_each` method?

Runtime complexity is **O(n)**. The function ultimately makes a list and puts every node in it,iterates over it, and performs the CB on each node's value.

4. What is the space complexity of your `breadth_first_for_each` method?

My best guess is **O(log n)**. I don't think it's appropriate to say it's linear, because the list the function needs to hold will never be as large as the input (*the nodes of the tree*). This is because after the CB is called on the node's value, it's direct children are unpacked, then the node itself gets shifted off the list. 

With that said, the list gets bigger when the tree is bigger, so I think O(log n) is a good guess.

5. What is the runtime complexity of your `heapsort` function?



6. What is the space complexity of the `heapsort` function? Recall that your implementation should return a new array with the sorted data. What would be the space complexity if your function instead altered the input array?