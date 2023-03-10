# Cyclic Rotation

<br>

# <a href="https://app.codility.com/programmers/lessons/2-arrays/">문제</a>

<br>

##### A non-empty array A consisting of N integers is given. The array contains an odd number of elements, and each element of the array can be paired with another element that has the same value, except for one element that is left unpaired.
##### For example, in array A such that:
  A[0] = 9  A[1] = 3  A[2] = 9
  A[3] = 3  A[4] = 9  A[5] = 7
  A[6] = 9
##### the elements at indexes 0 and 2 have value 9,
##### the elements at indexes 1 and 3 have value 3,
##### the elements at indexes 4 and 6 have value 9,
##### the element at index 5 has value 7 and is unpaired.
##### Write a function:
##### class Solution { public int solution(int[] A); }
##### that, given an array A consisting of N integers fulfilling the above conditions, returns the value of the unpaired element.
##### For example, given array A such that:
  A[0] = 9  A[1] = 3  A[2] = 9
  A[3] = 3  A[4] = 9  A[5] = 7
  A[6] = 9
##### the function should return 7, as explained in the example above.
##### Write an efficient algorithm for the following assumptions:
##### N is an odd integer within the range [1..1,000,000];
##### each element of array A is an integer within the range [1..1,000,000,000];
##### all but one of the values in A occur an even number of times.

<br>

# My Code

```javascript
function solution(A) {
    // A : given array

    // singleton case
    if(A.length == 1) {
        return A[0];
    }
    else {
        // sort array
        A.sort()

        let prevNumber = A[0]
        let count = 1

        for(let i=1;i<A.length;i++) {
            if(A[i] == prevNumber) {
                count += 1
            }
            else {
                // if count is odd
                if(count % 2) {
                    // return prevNumber
                    return prevNumber;
                }
                else { 
                    // update previous number
                    prevNumber = A[i]

                    // update count
                    count = 1
                }
            }
        }
    }

    return A[A.length - 1];
}
```

<br>

# Result
<img width="834" alt="image" src="https://user-images.githubusercontent.com/74173976/207803947-7af0c941-f750-4a92-b2eb-c15233bb47d6.png">
