# Max Product Of Three

<br>

# <a href="https://app.codility.com/programmers/lessons/6-sorting/">문제</a>

<br>

##### A non-empty array A consisting of N integers is given. The product of triplet (P, Q, R) equates to A[P] * A[Q] * A[R] (0 ≤ P < Q < R < N).
##### For example, array A such that:
  A[0] = -3
  A[1] = 1
  A[2] = 2
  A[3] = -2
  A[4] = 5
  A[5] = 6
##### contains the following example triplets:
##### (0, 1, 2), product is −3 * 1 * 2 = −6
##### (1, 2, 4), product is 1 * 2 * 5 = 10
##### (2, 4, 5), product is 2 * 5 * 6 = 60
##### Your goal is to find the maximal product of any triplet.
##### Write a function:
##### function solution(A);
##### that, given a non-empty array A, returns the value of the maximal product of any triplet.
##### For example, given array A such that:
  A[0] = -3
  A[1] = 1
  A[2] = 2
  A[3] = -2
  A[4] = 5
  A[5] = 6
##### the function should return 60, as the product of triplet (2, 4, 5) is maximal.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [3..100,000];
##### each element of array A is an integer within the range [−1,000..1,000].

<br>

# My Code

```javascript
function solution(A) {
    // A : given array

    // sort : A by ascending order
    A.sort((a, b) => {return a - b;})

    // initialize : calcuate product of most left elements and most right elements
    let leftProduct = Math.max(A[0] * A[1] * A[2], A[0] * A[1] * A[A.length - 1]);
    let rightProduct = A[A.length - 3] * A[A.length - 2] * A[A.length - 1]

    // return : Max(leftProduct, rightProduct)
    if(leftProduct >= rightProduct) {
        return leftProduct;
    }
    else {
        return rightProduct;
    }
}
```

<br>

# Result
<img width="847" alt="image" src="https://user-images.githubusercontent.com/74173976/209286423-e6c8e7bb-687b-4dc0-93e8-507eccde2b51.png">
