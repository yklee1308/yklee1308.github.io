---
layout: post
title: 2607번 - 비슷한 단어
category: Baekjoon
tags: [Baekjoon]
comments: true
---

## [2607] 비슷한 단어

문제 설명
- 알파벳 대문자로 이루어진 두 단어가 같은 종류의 문자로 이루어져 있으면서 같은 문자가 같은 개수만큼 있을 경우, 두 단어는 같은 구성을 갖는다고 한다.
- 두 단어가 같은 구성을 갖는 경우, 또는 한 단어에서 한 문자를 더하거나, 빼거나, 교체하여 나머지 한 단어와 같은 구성을 갖는 경우에 두 단어는 서로 비슷한 단어라고 한다.
- 단어의 개수와 개수만큼의 단어들을 입력 받아 첫 번째 단어와 비슷한 단어가 몇 개인지를 출력한다.

입력
```
4
DOG
GOD
GOOD
DOLL
```

출력
```
2
```

문제 분석 및 풀이
- 문제에서 주어진 조건을 정확하게 파악하고, 경우의 수를 나누어 알고리즘을 구현할 수 있는지를 묻는 문제이다.
- 첫 번째 단어와 비교하는 단어가 같은 구성을 같는 경우, 비교하는 단어에 한 문자가 빠지거나 교체된 경우를 한 가지 경우의 수로 설정한다.
- 비교하는 단어에 한 문자가 더해진 경우와 그 외의 경우를 각각 또 다른 경우의 수로 설정한다.
- 첫 번째 단어와 비교하는 단어의 문자들을 각각 담은 리스트 std_arr와 cmp_arr를 생성한다.
- 두 단어의 길이가 같거나 첫 번째 단어의 길이가 1만큼 긴 경우, 비교하는 단어의 모든 문자들에 대하여 첫 번째 단어 내에 해당 문자가 존재할 때 std_arr에서 그 문자를 제거한다.
- 위의 과정을 반복하다가 std_arr에 요소가 단 하나만 존재하게 되면 두 단어는 비슷한 단어이므로 cnt를 1만큼 증가시킨다.
- 첫 번째 단어의 길이가 1만큼 작은 경우, 첫 번째 단어의 모든 문자들에 대하여 비교하는 단어 내에 해당 문자가 존재할 때 cmp_arr에서 그 문자를 제거한다.
- 위의 과정을 반복하다가 cmp_arr에 요소가 단 하나만 존재하게 되면 두 단어는 비슷한 단어이므로 cnt를 1만큼 증가시킨다.
- 그 외의 경우에는 cnt를 증가시키지 않고 다음 비교하는 단어로 넘어간다.
- 마지막으로 첫 번째 단어와 비슷한 단어의 개수인 cnt를 출력한다.

정답
```python
n = int(input())
arr = []
for i in range(n):
    arr.append(input())
cnt = 0

for i in range(1, len(arr)):
    std_arr = list(arr[0])
    cmp_arr = list(arr[i])

    if len(std_arr) == len(cmp_arr) or len(std_arr) - len(cmp_arr) == 1:
        for j in cmp_arr:
            if j in std_arr:
                std_arr.remove(j)
                if len(std_arr) == 1:
                    cnt += 1
    elif len(std_arr) - len(cmp_arr) == -1:
        for j in std_arr:
            if j in cmp_arr:
                cmp_arr.remove(j)
                if len(cmp_arr) == 1:
                    cnt += 1
    else:
        continue

print(cnt)
```
