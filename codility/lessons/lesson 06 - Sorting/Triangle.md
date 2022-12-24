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
    // return 0 : if A has less than 3 elements
    if(A.length < 3) {
        return 0;
    }
    // if A has more than 3 elements
    else {
        // sort A by ascending order
        A.sort((a, b) => {return a - b;})

        // itertate to find tuplet
        for(let i=0;i<A.length-2;i++) {
            if(A[i] + A[i + 1] <= A[i + 2]) {
                continue;
            }

            if(A[i + 1] + A[i + 2] <= A[i]) {
                continue;
            }

            if(A[i + 2] + A[i] <= A[i + 1]) {
                continue;
            }

            // return 1 : if all exceptions can not be applied
            return 1;
        }

        // return 0 : if there exists no tuplet
        return 0;
    }
}
```

<br>

# Result
<img width="839" alt="image" src="https://user-images.githubusercontent.com/74173976/209441767-04f47997-403a-4c6a-a990-f71128e259fc.png">
