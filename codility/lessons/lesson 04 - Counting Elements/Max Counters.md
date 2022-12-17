# Max Counters

<br>

# <a href="https://app.codility.com/programmers/lessons/4-counting_elements/">문제</a>

<br>

##### You are given N counters, initially set to 0, and you have two possible operations on them:
##### increase(X) − counter X is increased by 1,
##### max counter − all counters are set to the maximum value of any counter.
##### A non-empty array A of M integers is given. This array represents consecutive operations:
##### if A[K] = X, such that 1 ≤ X ≤ N, then operation K is increase(X),
##### if A[K] = N + 1 then operation K is max counter.
##### For example, given integer N = 5 and array A such that:
    A[0] = 3
    A[1] = 4
    A[2] = 4
    A[3] = 6
    A[4] = 1
    A[5] = 4
    A[6] = 4
##### the values of the counters after each consecutive operation will be:
    (0, 0, 1, 0, 0)
    (0, 0, 1, 1, 0)
    (0, 0, 1, 2, 0)
    (2, 2, 2, 2, 2)
    (3, 2, 2, 2, 2)
    (3, 2, 2, 3, 2)
    (3, 2, 2, 4, 2)
##### The goal is to calculate the value of every counter after all operations.
##### Write a function:
##### class Solution { public int[] solution(int N, int[] A); }
##### that, given an integer N and a non-empty array A consisting of M integers, returns a sequence of integers representing the values of the counters.
##### Result array should be returned as an array of integers.
##### For example, given:
    A[0] = 3
    A[1] = 4
    A[2] = 4
    A[3] = 6
    A[4] = 1
    A[5] = 4
    A[6] = 4
##### the function should return [3, 2, 2, 4, 2], as explained above.
##### Write an efficient algorithm for the following assumptions:
##### N and M are integers within the range [1..100,000];
##### each element of array A is an integer within the range [1..N + 1].

<br>

# My Code

```javascript
function solution(N, A) {
    // N : num(counters)
    // A : operations

    // Initialize : max values
    let prevMaxValue = 0;
    let curMaxValue = 0;

    // Initialize : counters
    let counters = [];
    for(let i=0;i<=N;i++) {
        counters[i] = 0;
    }

    let changedIndex = []

    for(let i=0;i<A.length;i++) {

        // increase
        if(A[i] <= N) {
            // update : A
            counters[A[i]] += 1;

            // update : changed index array
            changedIndex[changedIndex.length] = A[i]

            // update : current max value
            if(curMaxValue < counters[A[i]] + prevMaxValue) {
                curMaxValue = counters[A[i]] + prevMaxValue
            }
        }
        // max counter
        else {
            // update : previous max value to be current max value
            prevMaxValue = curMaxValue;            

            // initialize : value of counters to be 0 whose index included in maxIndex
            for(let i=0;i<changedIndex.length;i++) {
                counters[changedIndex[i]] = 0;
            }

            // initialize : changed index array
            changedIndex = []
        }
    }

    // apply max counter operation to counters
    for(let i=1;i<=N;i++) {
        if(counters[i] <= prevMaxValue) {
            counters[i] += prevMaxValue;
        }
    }

    // delete : 0th element
    counters.shift();

    return counters;
}

```

<br>

# Result
<img width="869" alt="image" src="https://user-images.githubusercontent.com/74173976/208227377-e70cccb9-4b1d-4085-9ee2-ddcf8112dbf7.png">
