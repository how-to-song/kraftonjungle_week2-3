https://neetcode.io/problems/reverse-a-linked-list/question?list=blind75
```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if head is None:
            return None

        current = head
        prev = None
        while current is not None:
            next_temp = current.next
            current.next = prev
            prev = current
            current = next_temp

        return prev
```

Tip! 연결리스트의 next를 이전 값으로 옮긴다.

`if head is None: return None` 현재 head가 None이면 None 반환

`current = head` 위치를 옮기면서 .next를 바꿀 current node
`prev = None` .next에 위치를 대입할 이전 노드

```
while current is not None: # 현재가 None이면 prev가 맨 마지막이라서
	next_temp = current.next # 다음 노드로 이동할 위치 저장
	current.next = prev # 현재의 다음 노드를 이전 노드로 이동
	prev = current # 변경 후, 이전노드를 현재노드로 이동
	current = next_temp # 현재노드를 다음 노드로 이동 (이전노드는 이미 옮김)
```

`return prev` 현재노드는 None이고 이전노드가 제일 처음이라서 prev 반환