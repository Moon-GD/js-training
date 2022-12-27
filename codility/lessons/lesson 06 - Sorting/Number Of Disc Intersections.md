# Number Of Disc Intersections

<br>

# <a href="https://app.codility.com/programmers/lessons/6-sorting/">문제</a>

<br>

##### We draw N discs on a plane. The discs are numbered from 0 to N − 1. An array A of N non-negative integers, specifying the radiuses of the discs, is given. The J-th disc is drawn with its center at (J, 0) and radius A[J].
##### We say that the J-th disc and K-th disc intersect if J ≠ K and the J-th and K-th discs have at least one common point (assuming that the discs contain their borders).
##### The figure below shows discs drawn for N = 6 and A as follows:
  A[0] = 1
  A[1] = 5
  A[2] = 2
  A[3] = 1
  A[4] = 4
  A[5] = 0
##### There are eleven (unordered) pairs of discs that intersect, namely:
##### discs 1 and 4 intersect, and both intersect with all the other discs;
##### disc 2 also intersects with discs 0 and 3.
##### Write a function:
##### function solution(A);
##### that, given an array A describing N discs as explained above, returns the number of (unordered) pairs of intersecting discs. The function should return −1 if the number of intersecting pairs exceeds 10,000,000.
##### Given array A shown above, the function should return 11, as explained above.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [0..100,000];
##### each element of array A is an integer within the range [0..2,147,483,647].

<br>

# My Code

```javascript
function solution(A) {
    // declare : array that records circle info
    let circleInfo = []

    for(let i=0;i<A.length;i++) {
        // update : circle info
        // first param : maximum range to the right end of i th circle
        // second param : minimal range to the left end of i th circle
        circleInfo[i] = [i + A[i], i - A[i]];
    }

    // declare : a variable that will be returned
    let count = 0;

    for(let i=0;i<A.length;i++) {
        for(let j=i+1;j<A.length;j++) {
            // if i th circle can intersect j th circle
            if(circleInfo[i][0] >= circleInfo[j][1]) {
                // update : circle
                count += 1;
            }
        }
    }

    return count;
}

```

<br>

# Result
<img width="830" alt="image" src="https://user-images.githubusercontent.com/74173976/209611983-2fd8690b-e1d3-4812-9ad7-42b20695a464.png">
