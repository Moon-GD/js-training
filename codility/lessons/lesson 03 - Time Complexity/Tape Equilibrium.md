# Tape Equilibrium

<br>

# <a href="https://app.codility.com/programmers/lessons/3-time_complexity/">문제</a>

<br>

##### A non-empty array A consisting of N integers is given. Array A represents numbers on a tape.
##### Any integer P, such that 0 < P < N, splits this tape into two non-empty parts: A[0], A[1], ..., A[P − 1] and A[P], A[P + 1], ..., A[N − 1].
##### The difference between the two parts is the value of: |(A[0] + A[1] + ... + A[P − 1]) − (A[P] + A[P + 1] + ... + A[N − 1])|
##### In other words, it is the absolute difference between the sum of the first part and the sum of the second part.
##### For example, consider array A such that:
  A[0] = 3
  A[1] = 1
  A[2] = 2
  A[3] = 4
  A[4] = 3
##### We can split this tape in four places:
##### P = 1, difference = |3 − 10| = 7
##### P = 2, difference = |4 − 9| = 5
##### P = 3, difference = |6 − 7| = 1
##### P = 4, difference = |10 − 3| = 7
##### Write a function:
##### class Solution { public int solution(int[] A); }
##### that, given a non-empty array A of N integers, returns the minimal difference that can be achieved.
##### For example, given:
  A[0] = 3
  A[1] = 1
  A[2] = 2
  A[3] = 4
  A[4] = 3
##### the function should return 1, as explained above.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [2..100,000];
##### each element of array A is an integer within the range [−1,000..1,000].

<br>

# My Code

```javascript
function solution(A) {
    // get total sum of A
    let totalSum = A.reduce((x, y) => x + y);

    // initialize current sum & minimal sum
    let curSum = 0;
    let minSum = 0;

    for(let i=0;i<A.length - 1;i++) {
        // update current sum
        curSum += A[i];

        // initialize : minimal sum
        if(i == 0) {
            minSum = Math.abs(2 * curSum - totalSum)
        }
        else {
            // get diff between left sum and right sum
            let difference = Math.abs(2 * curSum - totalSum)

            // update minimal sum
            minSum = Math.min(minSum, difference)
        }
    }

    return minSum;
}
```

<br>

# Result
<img width="833" alt="image" src="https://user-images.githubusercontent.com/74173976/208084820-49f2d7e0-6371-495c-a03a-386d308ada01.png">
