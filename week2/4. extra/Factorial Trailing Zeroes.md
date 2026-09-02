n!의 맨 뒤에 있는 0의 개수를 반환
```python
class Solution:
    def trailingZeroes(self, n: int) -> int:
        count = 0
        while n > 0:
            n = n // 5
            count += n

        return count
```
항상 2가 5보다 더 많이 들어가기 때문에 5의 개수만 세면 맨 뒤에 붙는 0의 개수를 알 수 있다.

5! = 1
10! = 2
15! = 3
20! = 4
25! = 6 => 25는 5^2이므로 5가 2번 들어간다.