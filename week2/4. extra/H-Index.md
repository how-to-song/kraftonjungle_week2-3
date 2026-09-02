H-index란?
연구자가 발표한 논문 중 각각 최소  h회 이상 인용된 논문이 최소 h편 이상이 되도록 하는 h의 최댓값
`[3, 0 , 6, 1, 5]`이라면 총 5편의 논문을 썼고 각각 3번, 0번, 6번, 1번, 5번 인용되었다.
여기서 h-index의 후보
0: 최소 0회 이상 인용된 논문이 5편
1: 최소 1회 이상 인용된 논문이 4편
3: 최소 3회 이상 인용된 논문이 3편
5: 최소 5회 이상 인용된 논문이 2편 (X)
=> H-Index는 3

```python
class Solution:

    def hIndex(self, citations: List[int]) -> int:
        citations.sort()
        n = len(citations)
        result = 0

        for i in range(n):
            if citations[i] >= n-i:
                result = n-i
                break
                
        return result
```

코드 구현
받아온 배열을 정렬
정렬된 배열의 크기에서 해당 인덱스를 뺀 값(n-i)는 해당 인덱스의 값(`citations[i]`)보다 인용된 횟수가 같거나 더 큰 것들의 개수와 해당 인덱스의 값을 비교해서 인용된 횟수가 작거나 같을 때 인용된 횟수 반환