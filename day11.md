# day11 150. 逆波兰表达式求值 |

# [150. 逆波兰表达式求值]([https://leetcode.cn/problems/evaluate-reverse-polish-notation/description/])
后缀表达式，只需要搞清楚定义就能做出来
```cpp
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        std::stack<int> sl;
        for(auto it: tokens) {
            if (it != "+" && it != "-" && it != "*" && it != "/") {
                sl.push(stoi(it));
            } else{
                int num1 = sl.top();
                sl.pop();
                int num2 = sl.top();
                sl.pop();
                if (it == "+") sl.push(num2 + num1);
                if (it == "-") sl.push(num2 - num1);
                if (it == "*") sl.push(num2 * num1);
                if (it == "/") sl.push(num2 / num1);
            }
        }
        return sl.top();
    }
};
```
