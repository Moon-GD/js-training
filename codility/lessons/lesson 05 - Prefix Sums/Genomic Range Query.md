# Genomic Range Query

<br>

# <a href="https://app.codility.com/programmers/lessons/5-prefix_sums/">문제</a>

<br>

##### A DNA sequence can be represented as a string consisting of the letters A, C, G and T, which correspond to the types of successive nucleotides in the sequence. Each nucleotide has an impact factor, which is an integer. Nucleotides of types A, C, G and T have impact factors of 1, 2, 3 and 4, respectively. You are going to answer several queries of the form: What is the minimal impact factor of nucleotides contained in a particular part of the given DNA sequence?
##### The DNA sequence is given as a non-empty string S = S[0]S[1]...S[N-1] consisting of N characters. There are M queries, which are given in non-empty arrays P and Q, each consisting of M integers. The K-th query (0 ≤ K < M) requires you to find the minimal impact factor of nucleotides contained in the DNA sequence between positions P[K] and Q[K] (inclusive).
##### For example, consider string S = CAGCCTA and arrays P, Q such that:
    P[0] = 2    Q[0] = 4
    P[1] = 5    Q[1] = 5
    P[2] = 0    Q[2] = 6
##### The answers to these M = 3 queries are as follows:
##### The part of the DNA between positions 2 and 4 contains nucleotides G and C (twice), whose impact factors are 3 and 2 respectively, so the answer is 2.
##### The part between positions 5 and 5 contains a single nucleotide T, whose impact factor is 4, so the answer is 4.
##### The part between positions 0 and 6 (the whole string) contains all nucleotides, in particular nucleotide A whose impact factor is 1, so the answer is 1.
##### Write a function:
##### function solution(S, P, Q);
##### that, given a non-empty string S consisting of N characters and two non-empty arrays P and Q consisting of M integers, returns an array consisting of M integers specifying the consecutive answers to all queries.
##### Result array should be returned as an array of integers.
##### For example, given the string S = CAGCCTA and arrays P, Q such that:
    P[0] = 2    Q[0] = 4
    P[1] = 5    Q[1] = 5
    P[2] = 0    Q[2] = 6
##### the function should return the values [2, 4, 1], as explained above.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [1..100,000];
##### M is an integer within the range [1..50,000];
##### each element of arrays P and Q is an integer within the range [0..N - 1];
##### P[K] ≤ Q[K], where 0 ≤ K < M;
##### string S consists only of upper-case English letters A, C, G, T.

<br>

# My Code

```javascript
function solution(S, P, Q) {
    // S : given DNA sequence
    // P, Q : query for find minimal impact factor

    // declare : list that records last indexes for A, C, G, T
    let indexList = []

    // declare : previous index info before S[i]
    // order - A, C, G, T
    let prevIndex = [-1, -1, -1, -1]

    for(let i=0;i<S.length;i++) {
        // update : prevIndex
        if(S[i] == 'A') {
            prevIndex[0] = i;
        }
        else if(S[i] == 'C') {
            prevIndex[1] = i;
        }
        else if(S[i] == 'G') {
            prevIndex[2] = i;
        }
        else {
            prevIndex[3] = i;
        }

        // add : push previous index to index list
        indexList[indexList.length] = prevIndex.slice()
    }

    // declare : list that will be returned
    let factorList = []

    for(let i=0;i<P.length;i++) {
        // declare : interval for searching
        let begin = P[i];
        let end = Q[i];

        // search index list
        for(let j=0;j<4;j++) {
            // if j th element is found between begin and end
            if(begin <= indexList[end][j] && indexList[end][j] <= end) {
                // add : push j+1 to factor list
                factorList.push(j+1);

                // break : stop searching
                break;
            }
        }
    }

    return factorList;
}

```

<br>

# Result
<img width="858" alt="image" src="https://user-images.githubusercontent.com/74173976/208873883-661b3528-0371-48ec-92d4-36210899ec93.png">

# Notice
when array is copied in JS, I have to consider whether to perform deep copy or shallow copy
