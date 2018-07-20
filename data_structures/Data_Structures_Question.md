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

My heap sort needs to add each element in the list to the heap. This is O(log n).

I then need to delete each node in the heap. The deletion is also O(log n). The return value of the deletion is then inserted into the first position of the answer list. That insertion is O(n). Finally, we need to do this as many times as there are nodes. 

So we have insertion of O(log n), and a loop O(n) that does an O(log n) deletion and an O(n) insertion into list each iteration.

Not sure how we add all of these together and classify them together. The big stickler is the insertion to the list. If we had a min heap, appending to the list would be O(1), and thus we can throw that out the window.

But because the insertion is there, it's worse than O(n log n). O(n<sup>2</sup> log n)???

6. What is the space complexity of the `heapsort` function? Recall that your implementation should return a new array with the sorted data. What would be the space complexity if your function instead altered the input array?

Not sure space complexity changes. We need to build a heap regardless, so it will always be at least O(n) space complexity. Whether we change the input array or build a new one, the heap gets smaller with every deletion. If you change the array in place, the memory used will become smaller, but you had to use up O(n) in the first place.

In contrast, if you build a new array, the heap gets smaller as the new array gets bigger. In the end, you'll just end up with an O(n) classification anyways.