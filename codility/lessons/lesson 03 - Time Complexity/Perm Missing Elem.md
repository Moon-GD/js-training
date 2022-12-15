# Perm Missing Elem

<br>

# <a href="https://app.codility.com/programmers/lessons/3-time_complexity/">문제</a>

<br>

##### An array A consisting of N different integers is given. The array contains integers in the range [1..(N + 1)], which means that exactly one element is missing.
##### Your goal is to find that missing element.
##### Write a function:
##### class Solution { public int solution(int[] A); }
##### that, given an array A, returns the value of the missing element.
##### For example, given array A such that:
  A[0] = 2
  A[1] = 3
  A[2] = 1
  A[3] = 5
##### the function should return 4, as it is the missing element.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [0..100,000];
##### the elements of A are all distinct;
##### each element of array A is an integer within the range [1..(N + 1)].

<br>

# My Code

```javascript
function solution(A) {
    // A : given array

    // get total sum
    totalSum = 0
    for(let i=1;i<= A.length + 1;i++) {
        totalSum += i
    }

    // get sum of A
    curSum = A.reduce((a, b) => a + b, 0)

    // return missing value
    return totalSum - curSum
}
```

<br>

# Result
<img width="849" alt="image" src="https://user-images.githubusercontent.com/74173976/207807735-2c0753ed-3433-48a0-b48b-661103410c09.png">
