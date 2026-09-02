https://leetcode.com/problems/candy/description/?envType=study-plan-v2&envId=top-interview-150

```python
class Solution:
    def candy(self, ratings: List[int]) -> int:
        n = len(ratings)
        arr = [1] * n

        for i in range(1, n):
            if ratings[i - 1] < ratings[i]:
                arr[i] = arr[i-1] + 1

        for i in range(n-2, -1, -1):
            if ratings[i] > ratings[i+1]:
                arr[i] = max(arr[i], arr[i+1]+1)

        return sum(arr)
```

1로 초기화한 배열 arr
첫번째로 ratings배열을 처음부터 돌면서 오른쪽이 더 큰 지만 비교하여 해당 인덱스 arr에 이전 인덱스 arr값 +1
두번째로 ratings배열을 뒤에서부터 돌면서 왼쪽이 더 큰 지만 비교하여 해당 인덱스 arr에 이전 인덱스 arr값 +1 => 여기서 기존 arr값과 비교하여 더 큰 것을 넣는다.
why? 인접한 값들이 양 옆에 있는 값 두 개보다 크다면 배열 2번 도니까 +1,+1이 되는데 최소를 구해야 되서 더 크거나 같은 것만 넣는다.