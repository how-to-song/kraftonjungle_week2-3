https://neetcode.io/problems/linked-list-cycle-detection/question?list=blind75

다른사람이 푼거
```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        fast = slow = head

        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next

            if slow == fast:
                return True
        return False
```
`slow`와 `fast` 포인터 2개를 두어 사이클이 있다면 언젠가는 만난다.
검사 기준에 `fast`만 있는 이유
=> `slow`는 `fast`가 지나온 노드만 밟기 때문에 `slow`를 확인할 필요는 없다.
=> `fast`, `fast.next`를 확인하니까 `fast = fast.next.next`를 한다.


내가 푼거
```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        cycle_set = set()
        is_cycle = False
        if head is None:
            return is_cycle
        
        while head.next is not None:
            if head.val in cycle_set:
                is_cycle = True
                break
            else:
                cycle_set.add(head.val)
            head = head.next
        return is_cycle
```