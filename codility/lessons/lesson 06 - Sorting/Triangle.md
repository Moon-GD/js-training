# Triangle

<br>

# <a href="https://app.codility.com/programmers/lessons/6-sorting/">문제</a>

<br>

##### An array A consisting of N integers is given. A triplet (P, Q, R) is triangular if 0 ≤ P < Q < R < N and:
##### A[P] + A[Q] > A[R],
##### A[Q] + A[R] > A[P],
##### A[R] + A[P] > A[Q].
##### For example, consider array A such that:
  A[0] = 10    A[1] = 2    A[2] = 5
  A[3] = 1     A[4] = 8    A[5] = 20
##### Triplet (0, 2, 4) is triangular.
##### Write a function:
##### function solution(A);
##### that, given an array A consisting of N integers, returns 1 if there exists a triangular triplet for this array and returns 0 otherwise.
##### For example, given array A such that:
  A[0] = 10    A[1] = 2    A[2] = 5
  A[3] = 1     A[4] = 8    A[5] = 20
##### the function should return 1, as explained above. Given array A such that:
  A[0] = 10    A[1] = 50    A[2] = 5
  A[3] = 1
##### the function should return 0.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [0..100,000];
##### each element of array A is an integer within the range [−2,147,483,648..2,147,483,647].

<br>

# My Code

```javascript
function solution(A) {
    // sort : sort A by ascending
    A.sort((a, b) => {return a - b;})

    for(let i=0;i<A.length-3;i++) {
        // return 1 : if tuplet is found
        if(A[i] + A[i + 1] > A[i + 2]) {
            return 1;
        }
    }

    // return 0 : if no tuplet is found
    return 0;
}
```

<br>

# Result
<img width="825" alt="image" src="https://user-images.githubusercontent.com/74173976/209441075-328f2735-f62f-4202-b6f4-27fd4b58098c.png">
