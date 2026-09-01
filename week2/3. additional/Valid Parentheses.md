https://neetcode.io/problems/validate-parentheses/question?list=blind75


```python
class Solution:

    def isValid(self, s: str) -> bool:
        stack = []
        is_valid = True
        
        for i in s:
            if i == ")":
                if len(stack) != 0 and stack[-1] == "(":
                    stack.pop()
                    continue
                else:
                    is_valid = False
                    break

            if i == "}":
                if len(stack) != 0 and stack[-1] == "{":
                    stack.pop()
                    continue
                else:
                    is_valid = False
                    break

            if i == "]":
                if len(stack) != 0 and stack[-1] == "[":
                    stack.pop()
                    continue
                else:
                    is_valid = False
                    break
                    
            stack.append(i)
        return is_valid and len(stack) == 0
```

```python
pairs = {")": "(", "}": "{", "]": "["}

for ch in s:
    if ch in pairs:                     # 닫는 괄호
        if not stack or stack.pop() != pairs[ch]:
            return False
    else:                               # 여는 괄호
        stack.append(ch)

return not stack

```