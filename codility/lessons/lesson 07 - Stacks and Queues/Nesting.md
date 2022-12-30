# Nesting

<br>

# <a href="https://app.codility.com/programmers/lessons/7-stacks_and_queues/">문제</a>

<br>

##### A string S consisting of N characters is called properly nested if:
##### S is empty;
##### S has the form "(U)" where U is a properly nested string;
##### S has the form "VW" where V and W are properly nested strings.
##### For example, string "(()(())())" is properly nested but string "())" isn't.
##### Write a function:
##### function solution(S);
##### that, given a string S consisting of N characters, returns 1 if string S is properly nested and 0 otherwise.
##### For example, given S = "(()(())())", the function should return 1 and given S = "())", the function should return 0, as explained above.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [0..1,000,000];
##### string S is made only of the characters "(" and/or ")".

<br>

# My Code

```javascript
function solution(S) {
    // return 0 : S is empty
    if(S.length == 0) {
        return 1;
    }
    else {
        // initialize : push first element on stack
        let stack = [S[0]];

        for(let i=1;i<S.length;i++) {
            // S[i] == '('
            if(S[i] == '(') {
                stack.push(S[i]);
            }
            // S[i] == ')'
            else {
                // if pairs are matched
                if(stack[stack.length - 1] == '(') {
                    // delete last element of stack
                    stack.pop();
                }
                // if pairs are not matched
                else {
                    // add S[i] to stack
                    stack.push(S[i]);
                }
            }
        }

        // return 0 : stack is not empty
        if(stack.length) {
            return 0;
        }
        // return 1 : stack is empty
        else {
            return 1;
        }
    }
}
```

<br>

# Result
<img width="836" alt="image" src="https://user-images.githubusercontent.com/74173976/210052725-fcb8ee2d-1cbc-4eff-a28c-18ef40de5b00.png">
