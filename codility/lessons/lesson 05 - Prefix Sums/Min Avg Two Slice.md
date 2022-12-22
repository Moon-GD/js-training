# Min Avg Two Slice

<br>

# <a href="https://app.codility.com/programmers/lessons/5-prefix_sums/">문제</a>

<br>

##### A non-empty array A consisting of N integers is given. A pair of integers (P, Q), such that 0 ≤ P < Q < N, is called a slice of array A (notice that the slice contains at least two elements). The average of a slice (P, Q) is the sum of A[P] + A[P + 1] + ... + A[Q] divided by the length of the slice. To be precise, the average equals (A[P] + A[P + 1] + ... + A[Q]) / (Q − P + 1).
##### For example, array A such that:
    A[0] = 4
    A[1] = 2
    A[2] = 2
    A[3] = 5
    A[4] = 1
    A[5] = 5
    A[6] = 8
##### contains the following example slices:
##### slice (1, 2), whose average is (2 + 2) / 2 = 2;
##### slice (3, 4), whose average is (5 + 1) / 2 = 3;
##### slice (1, 4), whose average is (2 + 2 + 5 + 1) / 4 = 2.5.
##### The goal is to find the starting position of a slice whose average is minimal.
##### Write a function:
##### function solution(A);
##### that, given a non-empty array A consisting of N integers, returns the starting position of the slice with the minimal average. If there is more than one slice with a minimal average, you should return the smallest starting position of such a slice.
##### For example, given array A such that:
    A[0] = 4
    A[1] = 2
    A[2] = 2
    A[3] = 5
    A[4] = 1
    A[5] = 5
    A[6] = 8
##### the function should return 1, as explained above.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [2..100,000];
##### each element of array A is an integer within the range [−10,000..10,000].

<br>

# My Code

```javascript
function solution(A) {
    // declare : minimal index & AVG
    let minimalIndex = 0;
    let minimalAVG = (A[0] + A[1]) / 2;

    // declare : sum of two elements and three elements, respectively
    let doubleSum = 0;
    let tripleSum = 0;

    for(let i=0;i<A.length;i++) {
        // update : check double average of A[i], A[i+1]
        if(i + 1 < A.length) {
            doubleSum = A[i] + A[i+1];
            if(doubleSum / 2 < minimalAVG) {
                minimalAVG = doubleSum / 2;
                minimalIndex = i;
            }
        }

        // update : check triple average of A[i], A[i+1], A[i+2]
        if(i + 2 < A.length) {
            tripleSum = A[i] + A[i+1] + A[i+2];

            if(tripleSum / 3 < minimalAVG) {
                minimalAVG = tripleSum / 3;
                minimalIndex = i;
            }
        }
    }

    return minimalIndex;
}
```

<br>

# Result
<img width="844" alt="image" src="https://user-images.githubusercontent.com/74173976/209086735-f966d10e-66b9-4a69-a938-c0e0fb61f6fa.png">
