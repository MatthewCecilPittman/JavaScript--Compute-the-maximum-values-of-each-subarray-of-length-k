# JavaScript--Compute-the-maximum-values-of-each-subarray-of-length-k
Google interview question

```
function maxSubArrayLengthK(nums, k) {
  if (k <= 0) return [];

  const result = [];

  const deque = []; // deque stores the index of numbers
  for (let i = 0; i < nums.length; i++) {
    // checks if the deque is not empty and removes the number that is outside the deque
    // for example: [5, 4, 3, 1] k = 3, when i is 3.
    // Deque is [5, 4, 3] before. Remove 5 because out of window
    // Makes deque always of size k
    if (deque.length !== 0 && deque[0] < i - k + 1) {
      deque.shift();
    }

    // checks if the deque is not empty and pops from the deque smaller or equal numbers
    // deque[deque.length - 1] is the last index
    while (deque.length !== 0 && nums[i] >= nums[deque[deque.length - 1]]) {
      deque.pop();
    }

    deque.push(i);
    if (i >= k - 1) {
      result.push(nums[deque[0]]);
    }
  }
  return result;
}
maxSubArrayLengthK( [10, 5, 2, 7, 8, 7], 3);
```
