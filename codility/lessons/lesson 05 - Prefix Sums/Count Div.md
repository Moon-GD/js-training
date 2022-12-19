# Count Div

<br>

# <a href="https://app.codility.com/programmers/lessons/5-prefix_sums/">문제</a>

<br>

##### Write a function:
##### function solution(A, B, K);
##### that, given three integers A, B and K, returns the number of integers within the range [A..B] that are divisible by K, i.e.:
##### { i : A ≤ i ≤ B, i mod K = 0 }
##### For example, for A = 6, B = 11 and K = 2, your function should return 3, because there are three numbers divisible by 2 within the range [6..11], namely 6, 8 and 10.
##### Write an efficient algorithm for the following assumptions:
##### A and B are integers within the range [0..2,000,000,000];
##### K is an integer within the range [1..2,000,000,000];
##### A ≤ B.

<br>

# My Code

```javascript
function solution(A, B, K) {
    // [A, B] : given closed range
    // K : given divisor

    // declare : counting variable
    let count = 0;

    for(let i=A;i<=B;i++) {
        // if i is divisble by K
        if(i % K == 0) {
            // update : count
            count += 1;
            count += Math.floor((B - i) / K);

            break;
        }
    }

    // return : finishing iterating the loop
    return count;
}
```

<br>

# Result
<img width="859" alt="image" src="https://user-images.githubusercontent.com/74173976/208374011-ee7b8d3b-0379-4f8d-bde4-bcb1a0160c00.png">
