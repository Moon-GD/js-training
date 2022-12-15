# Binary Gap

# <a href="https://app.codility.com/programmers/lessons/1-iterations/">문제</a>
## A binary gap within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of N.

For example, number 9 has binary representation 1001 and contains a binary gap of length 2. The number 529 has binary representation 1000010001 and contains two binary gaps: one of length 4 and one of length 3. The number 20 has binary representation 10100 and contains one binary gap of length 1. The number 15 has binary representation 1111 and has no binary gaps. The number 32 has binary representation 100000 and has no binary gaps.

Write a function:

function solution(N);

that, given a positive integer N, returns the length of its longest binary gap. The function should return 0 if N doesn't contain a binary gap.

For example, given N = 1041 the function should return 5, because N has binary representation 10000010001 and so its longest binary gap is of length 5. Given N = 32 the function should return 0, because N has binary representation '100000' and thus no binary gaps.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..2,147,483,647].

<br>

# My Code

```javascript
function solution(N) {
    // N : positive integer

    // initialize : return value
    returnValue = 0

    // N(10) -> N(2)
    stringToN = N.toString(2)

    // index variable
    let first = 0;

    // update return value
    for(let i=0;i<stringToN.length;i++) {
        if(stringToN[i] == '1') {
            // update return value
            returnValue = Math.max(returnValue, i - first - 1);

            // update index variable
            first = i;
        }
    }

    return returnValue;
}

```

<br>

# Result
<img width="867" alt="lesson 01 - 1" src="https://user-images.githubusercontent.com/74173976/207795039-c8ea3336-2257-4e4a-a023-e589f7f12cde.png">
