https://neetcode.io/problems/rotate-matrix/question?list=blind75

절반 뒤집고 위에서 부터 절반 삼각형의 위치를 반대로 바꾸면 90도 회전
```python
def rotate(self, matrix: List[List[int]]) -> None:
    n = len(matrix)

    for i in range(n):
        for j in range(n // 2):
            matrix[i][j], matrix[i][n-j-1] = matrix[i][n-j-1], matrix[i][j]

    for i in range(n):
        for j in range(n - 1 - i):
            matrix[i][j], matrix[n-j-1][n-i-1] = matrix[n-j-1][n-i-1], matrix[i][j]
```
첫번째 반복문: j의 절반만큼만 반복문을 돌아 배열의 중앙을 기준으로 대칭 변경
두번째 반복문: 배열의 위에서부터 반대쪽 대각선을 기준으로 대칭 변경