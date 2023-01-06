# Question

You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return an integer that represents the value of the expression.

**Note that:**

* The valid operators are '+', '-', '*', and '/'.
* Each operand may be an integer or another expression.
* The division between two integers always truncates toward zero.
* There will not be any division by zero.
* The input represents a valid arithmetic expression in a reverse polish notation.
* The answer and all the intermediate calculations can be represented in a 32-bit integer.

**Example 1:**

>Input: tokens = ["2","1","+","3","*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9`

**Example 3:**

>Input: tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
Output: 22
Explanation: ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22

**Solution**
****

```c++
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<int> s;
        for(string x:tokens){
            if(x=="+"){
                int a=s.top(); //2
                s.pop();
                int b=s.top(); //3
                //a+b=2+3
                s.pop();
                s.push(a+b);
            }else if(x=="*"){
                int a=s.top(); //2
                s.pop();
                int b=s.top(); //3
                //a*b=2*3
                s.pop();
                s.push(a*b);
            }else if(x=="-"){
                int a=s.top(); //2
                s.pop();
                int b=s.top(); //3
                //b-a=3-2
                s.pop();
                s.push(b-a);
            }else if(x=="/"){
                int a=s.top(); //2
                s.pop();
                int b=s.top(); //3
                //b/a=3/2
                s.pop();
                s.push(b/a);
            }
            else s.push(stoi(x));
        }
        return s.top();
    }
};



```
**Sample Input**
>tokens =
["2","1","+","3","*"]

**Sample Output**
>9
