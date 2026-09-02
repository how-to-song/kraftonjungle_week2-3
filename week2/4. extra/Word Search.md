https://leetcode.com/problems/word-search/description/?envType=study-plan-v2&envId=top-interview-150

2차원 배열을 모두 돌면서 백트래킹

문자열의 길이와 k가 같으면 모두 맞았다 => True
배열 밖으로 나갔거나 `board[i][j]`와 `word[k]`가 다르면 => False
==> 여기서 `board[i][j]`가 `word[k]`는 같다

현재 `board[i][j]`를 `temp`에 저장하고
`board[i][j] = "#"`으로 바꿈
=> why? 모든 방향을 탐색할거니까 이전 방향으로는 가지 못하게 알파벳과 관련 없는 문자로 변경

```python
for di, dj in dirs:
	if search(i+di, j+dj, k+1):
		board[i][j] = temp
		return True
		
board[i][j] = temp
return False
```
모든 방향을 탐색하면서 모든 문자가 맞는다면 True, search에서 False여서 모든 for문을 돌았다면 False반환

```python
class Solution:

    def exist(self, board: List[List[str]], word: str) -> bool:
        n = len(board)
        m = len(board[0])

        for i in range(n):
            for j in range(m):
                dirs = [(0,1), (0,-1), (1,0), (-1,0)]

                def search(i, j, k):
                    if k == len(word):
                        return True
                        
                    if (i < 0 or i >= n or j < 0 or j >= m) or board[i][j] != word[k]:
                        return False

                    temp = board[i][j]
                    board[i][j] = "#"

                    for di, dj in dirs:
                        if search(i+di, j+dj, k+1):
                            board[i][j] = temp
                            return True

                    board[i][j] = temp
                    return False
                    
                if search(i, j, 0):
                    return True
                    
        return False
```
