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
    // declare : array that records lower & upper bound of i-th circle of A
    let circleInfo = [];

    for(let i=0;i<A.length;i++) {
        // initialize : array of circle info
        circleInfo[i] = [i - A[i], i + A[i]];
    }

    // sort using lower bound
    circleInfo.sort((a, b) => {
        return a[0] - b[0];
    })

    // declare : a variable that will be returned
    let count = 0;

    for(let i=0;i<A.length;i++) {
        let upperBound = circleInfo[i][1];

        for(let j=i+1;j<A.length;j++) {
            // if i-th circle intersects j-th circle
            if(circleInfo[j][0] <= upperBound) {
                // update : count
                count += 1;
            }
            // break : if i-th circle can not intersect j-th circle
            else {
                break;
            }
        }

        // return -1 : if count exceeds 10,000,000
        if(count > 10000000) {
            return -1;
        }
    }

    return count;
}
```

<br>

# Result
<img width="842" alt="image" src="https://user-images.githubusercontent.com/74173976/209617523-aa3c4af2-77e5-4f8a-b6b2-b18f5600d998.png">
