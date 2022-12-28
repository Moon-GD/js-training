# Brackets

<br>

# <a href="https://app.codility.com/programmers/lessons/7-stacks_and_queues/">문제</a>

<br>

##### A string S consisting of N characters is considered to be properly nested if any of the following conditions is true:
##### S is empty;
##### S has the form "(U)" or "[U]" or "{U}" where U is a properly nested string;
##### S has the form "VW" where V and W are properly nested strings.
##### For example, the string "{[()()]}" is properly nested but "([)()]" is not.
##### Write a function:
##### function solution(S);
##### that, given a string S consisting of N characters, returns 1 if S is properly nested and 0 otherwise.
##### For example, given S = "{[()()]}", the function should return 1 and given S = "([)()]", the function should return 0, as explained above.
##### Write an efficient algorithm for the following assumptions:
##### N is an integer within the range [0..200,000];
##### string S is made only of the following characters: "(", "{", "[", "]", "}" and/or ")".

<br>

# My Code

```javascript
class Stack {
    constructor() {
        this.array = [];
    }

    push(number) {
        this.array.push(number);
    }

    pop() {
        return this.array.pop()
    }

    lastElement() {
        return this.array[this.array.length - 1];
    }
}

function checkPair(lastElement, newElement) {
    if(lastElement == '(' && newElement == ')') {
        return true;
    }
    else if(lastElement == ')' && newElement == '(') {
        return true;
    }
    else if(lastElement == '[' && newElement == ']') {
        return true;
    }
    else if(lastElement == ']' && newElement == '[') {
        return true;
    }
    else if(lastElement == '{' && newElement == '}') {
        return true;
    }
    else if(lastElement == '}' && newElement == '{') {
        return true;
    }
    else {
        return false;
    }
}

function solution(S) {
    // create : stack
    let stack = new Stack();

    // initialize : stack
    stack.push(S[0]);

    for(let i=1;i<S.length;i++) {
        let lastElement = stack.lastElement();

        // if S[i] & last element are paired
        if(checkPair(lastElement, S[i])) {
            stack.pop();
        }
        // if no matching case -> push to stack
        else {
            stack.push(S[i]);
        }
    }

    // return 0 : there exists some char in stack
    if(stack.array.length) {
        return 0;
    }
    // return 1 : stack is cleared
    else {
        return 1;
    }
}
```

<br>

# Result
<img width="865" alt="image" src="https://user-images.githubusercontent.com/74173976/209777119-292dfc82-9276-44dd-9357-f4b190aeed51.png">
