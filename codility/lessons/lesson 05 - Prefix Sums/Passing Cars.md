# Passing Cars

<br>

# <a href="https://app.codility.com/programmers/lessons/5-prefix_sums/">문제</a>

<br>

##### A non-empty array A consisting of N integers is given. The consecutive elements of array A represent consecutive cars on a road.
##### Array A contains only 0s and/or 1s:
##### 0 represents a car traveling east,
##### 1 represents a car traveling west.
##### The goal is to count passing cars. We say that a pair of cars (P, Q), where 0 ≤ P < Q < N, is passing when P is traveling to the east and Q is traveling to the west.
##### For example, consider array A such that:
  A[0] = 0
  A[1] = 1
  A[2] = 0
  A[3] = 1
  A[4] = 1
##### We have five pairs of passing cars: (0, 1), (0, 3), (0, 4), (2, 3), (2, 4).
##### Write a function:
##### function solution(A);
##### that, given a non-empty array A of N integers, returns the number of pairs of passing cars.
##### The function should return −1 if the number of pairs of passing cars exceeds 1,000,000,000.
##### For example, given:
  A[0] = 0
  A[1] = 1
  A[2] = 0
  A[3] = 1
  A[4] = 1
##### the function should return 5, as explained above.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [1..100,000];
##### each element of array A is an integer that can have one of the following values: 0, 1.

<br>

# My Code

```javascript
function solution(A) {
    // A : given array

    // declare : total number of pairs of passing cars
    let total = 0;

    // declare : index of A whose value was 0
    let prevIndex = -1;

    // declare : variable that counts number of 1 between 0's
    let count = 0;

    for(let i=A.length-1;i>=0;i--) {
        if(A[i] == 1) {
            // update : count
            count += 1
        }
        else {
            // if previous index has no value  
            if(prevIndex == -1) {
                // update : A and total
                A[i] = count
                total += count
            }
            // if previous index has value
            else {
                // update : A and total using previous value of A
                A[i] = A[prevIndex] + count
                total += A[prevIndex] + count
            }

            // update : previous index and count
            prevIndex = i
            count = 0
        }

        // return (-1) : exceed upper bound
        if(total > 1000000000) {
            return -1;
        }

    }

    // return (total) : finish counting the number of pairs
    return total;
}
```

<br>

# Result
<img width="844" alt="image" src="https://user-images.githubusercontent.com/74173976/208368897-852818eb-baee-48b0-a549-a90988bff157.png">
