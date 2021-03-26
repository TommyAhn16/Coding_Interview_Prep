# 단어 변환

> Level 3
>
> [link](https://programmers.co.kr/learn/courses/30/lessons/43163)

# Solution

- BFS 방식으로 tree 와 같은 그래프 생성
- 타깃 워드가 위치한 tree height 을 정답으로 반환

```python
def solution(begin, target, words):
    # 예외 처리
    if target not in words:
        return 0
    # 그래프 형식: {tree height: [nodes]}
    graph = {0: [begin]}
    num = 0
    visited = set(begin)
    while graph[num]:
        cand = []
        stack = graph[num][:]
        while stack:
            word = stack.pop()
            for i in range(len(word)):
                index = list(range(len(word)))
                index.remove(i)
                for w in words:
                    # child 생성해서 다음 높이에 추가
                    if all(w[j]==word[j] for j in index) and w not in visited:
                        visited.add(w)
                        cand.append(w)
                        # child 중 target 발견 하면 현재 높이 + 1 로 리턴
                        if w == target:
                            return num+1
        num += 1
        graph[num] = cand
```
