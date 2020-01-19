---
layout: post
title: 5212번 - 지구 온난화
category: Baekjoon
tags: [Baekjoon]
comments: true
---

## [5212] 지구 온난화

문제 설명
- 직사각형 모양의 다도해 지도의 세로와 가로 길이를 입력 받는다.
- 현재 다도해 지도를 입력 받는다.
- 땅은 X로 표기하고, 바다는 .으로 표기한다.
- 50년이 지나면, 인접한 세 칸 또는 네 칸에 바다가 있는 땅은 모두 잠긴다.
- 50년 후의 지도를 모든 섬을 포함하는 가장 작은 직사각형 모양으로 출력한다.

입력
```
3 10
..........
..XXX.XXX.
XXX.......
```

출력
```
.XX...X
XX.....
```

문제 분석 및 풀이
- 모든 경우의 수에 대하여 검사를 수행할 수 있는지를 묻는 문제이다.
- 현재 다도해 지도를 가지고 검사를 진행할 경우, 8가지의 경우의 수를 고려해야 한다.
- 그러나, 지도의 바깥 부분이 모두 바다이기 때문에 상하좌우로 .을 하나씩 패딩하면 경우의 수가 한 가지로 줄어들어 문제가 훨씬 간단해진다.
- 현재 다도해 지도를 담은 2차원 리스트 dado_map을 생성하고, dado_map에 상하좌우로 .을 하나씩 패딩하여 ext_map을 생성한다.
- ext_map의 요소들에 하나씩 접근하여 요소의 인접한 세 칸 이상이 바다일 경우, dado_map에서의 같은 위치의 요소를 .으로 변경 또는 유지한다.
- 50년 후 dado_map의 땅의 세로, 가로 위치를 각각 리스트 r_loc과 c_loc에 저장한다.
- dado_map에서 세로, 가로 위치의 최솟값에서 최댓값 사이에 있는 요소들만 출력한다.

정답
```python
r, c = map(int, input().split())
dado_map, ext_map = [], []
r_loc, c_loc = [], []

ext_map.append('.' * (c + 2))
for i in range(r):
    dado_map.append(input())
    ext_map.append('.')
    ext_map[i + 1] += dado_map[i]
    ext_map[i + 1] += '.'
ext_map.append('.' * (c + 2))

for i in range(1, r + 1):
    for j in range(1, c + 1):
        if (int(ext_map[i][j - 1] == '.') + int(ext_map[i][j + 1] == '.') +
                int(ext_map[i - 1][j] == '.') + int(ext_map[i + 1][j] == '.') >= 3):
            dado_map[i - 1] = dado_map[i - 1][:(j - 1)] + '.' + dado_map[i - 1][j:]
        else:
            continue

for i in range(r):
    for j in range(c):
        if dado_map[i][j] == 'X':
            r_loc.append(i)
            c_loc.append(j)

for i in range(min(r_loc), max(r_loc) + 1):
    for j in range(min(c_loc), max(c_loc) + 1):
        print(dado_map[i][j], end='')
    print(end='\n')
```
