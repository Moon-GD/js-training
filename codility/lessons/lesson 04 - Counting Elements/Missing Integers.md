# Missing Integers

<br>

# <a href="https://app.codility.com/programmers/lessons/4-counting_elements/">문제</a>

<br>

##### This is a demo task.
##### Write a function:
##### function solution(A);
##### that, given an array A of N integers, returns the smallest positive integer (greater than 0) that does not occur in A.
##### For example, given A = [1, 3, 6, 4, 1, 2], the function should return 5.
##### Given A = [1, 2, 3], the function should return 4.
##### Given A = [−1, −3], the function should return 1.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [1..100,000];
##### each element of array A is an integer within the range [−1,000,000..1,000,000].

<br>

# My Code

```javascript
function solution(A) {
    // initialize : count array
    let counts = new Array(100001).fill(false);

    // update : counts array
    for(let i=0;i<A.length;i++) {
        if(A[i] > 0 && counts[A[i]] == false) {
            counts[A[i]] = true
        }
    }

    // find false
    for(let i=1;i<=100000;i++) {
        if(counts[i] == false) {
            return i;
        }
    }

    return 100001;
}
```

<br>

# Result
<img width="848" alt="image" src="https://user-images.githubusercontent.com/74173976/208294849-833d8d78-abac-41f1-bca2-723a50c7a7f1.png">
