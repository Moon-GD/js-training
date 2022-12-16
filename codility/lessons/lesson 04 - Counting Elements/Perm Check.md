# Perm Check

<br>

# <a href="https://app.codility.com/programmers/lessons/4-counting_elements/">문제</a>

<br>

##### A non-empty array A consisting of N integers is given.
##### A permutation is a sequence containing each element from 1 to N once, and only once.
##### For example, array A such that:
    A[0] = 4
    A[1] = 1
    A[2] = 3
    A[3] = 2
##### is a permutation, but array A such that:
    A[0] = 4
    A[1] = 1
    A[2] = 3
##### is not a permutation, because value 2 is missing.
##### The goal is to check whether array A is a permutation.
##### Write a function:
##### function solution(A);
##### that, given an array A, returns 1 if array A is a permutation and 0 if it is not.
##### For example, given array A such that:
    A[0] = 4
    A[1] = 1
    A[2] = 3
    A[3] = 2
##### the function should return 1.
##### Given array A such that:
    A[0] = 4
    A[1] = 1
    A[2] = 3
##### the function should return 0.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [1..100,000];
##### each element of array A is an integer within the range [1..1,000,000,000].

<br>

# My Code

```javascript
function getSumFromOneToX(X) {
    let sumFromOneToX = 0;

    for(let i=1;i<=X;i++) {
        sumFromOneToX += i;
    }

    return sumFromOneToX;
}

function solution(A) {
    // get length of A
    let length = A.length

    // initialize : check array
    let check = [];
    for(let i=0;i<=length;i++) {
        check[i] = false;
    }

    // initialize : sum of A
    let totalSum = 0;

    for(let i=0;i<length;i++) {
        let number = A[i];

        // number was visited
        if(check[number]) {
            return 0;
        }
        // new number
        else {
            // update : check array
            check[number] = true;

            // update : sum of A
            totalSum += number;
        }
    }

    // get sum from 1 to length
    let sumFromOneToLength = getSumFromOneToX(length);

    // the permutation condition is satisfied
    if(sumFromOneToLength == totalSum) {
        return 1;
    }
    // else
    else {
        return 0;
    }
}
```

<br>

# Result
<img width="856" alt="image" src="https://user-images.githubusercontent.com/74173976/208089495-dad8a936-d007-4aef-a845-ebd9174f8301.png">
