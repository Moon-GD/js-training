# Distinct

<br>

# <a href="https://app.codility.com/programmers/lessons/6-sorting/">문제</a>

<br>

##### Write a function
##### function solution(A)
##### that, given an array A consisting of N integers, returns the number of distinct values in array A.
##### For example, given array A consisting of six elements such that:
 A[0] = 2    A[1] = 1    A[2] = 1
 A[3] = 2    A[4] = 3    A[5] = 1
##### the function should return 3, because there are 3 distinct values appearing in array A, namely 1, 2 and 3.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [0..100,000]
##### each element of array A is an integer within the range [−1,000,000..1,000,000].

<br>

# My Code

```javascript
function solution(A) {
    // declare : array that checks each element in A
    let checkArray = new Array(2000001);

    // declare : a variable that will be returned
    let count = 0;

    for(let i=0;i<A.length;i++) {
        // continue : if A[i] was visited
        if(checkArray[A[i] + 1000000]) {
            continue;
        }
        // if A[i] is new element
        else {
            // update : check array of A[i]
            checkArray[A[i] + 1000000] = true;

            // update : +1 to count
            count += 1;
        }
    }

    return count;
}
```

<br>

# Result
<img width="858" alt="image" src="https://user-images.githubusercontent.com/74173976/209284450-b0162e08-586e-4cec-b129-d2975009b025.png">
