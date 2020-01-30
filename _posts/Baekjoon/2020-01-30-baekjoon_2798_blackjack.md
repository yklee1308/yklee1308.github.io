---
layout: post
title: 2798번 - 블랙잭
category: Baekjoon
tags: [Baekjoon]
comments: true
---

## [2798] 블랙잭

문제 설명
- 카드의 개수와 카드에 적힌 숫자들 중 세 수의 합의 한도를 입력 받는다.
- 카드의 개수만큼 수들을 입력 받아 한도를 넘지 않으면서 한도에 가장 가까운 세 수의 합을 구하여 출력한다.

입력
```
5 21
5 6 7 8 9
```

출력
```
21
```

문제 분석 및 풀이
- 다중 for문 안의 인덱스들을 적절하게 활용하여 모든 경우의 수를 검사할 수 있는지를 묻는 문제이다.
- 세 수의 합들을 저장할 리스트 arr_total을 생성한다.
- 안쪽 for문의 인덱스를 바깥쪽 for문의 인덱스보다 큰 수로 설정하여 숫자들이 서로 중복되지 않도록 세 수를 뽑는다.
- 세 수의 합 num_total이 한도보다 작을 경우에만 그 값을 리스트에 추가한다.
- arr_total 내의 요소들 중에서 최댓값을 출력한다.

정답
```python
n, m = map(int, input().split())
arr = list(map(int, input().split()))
arr_total = []

for i in range(len(arr) - 2):
    for j in range(i + 1, len(arr) - 1):
        for p in range(j + 1, len(arr)):
            num_total = arr[i] + arr[j] + arr[p]

            if num_total <= m:
                arr_total.append(num_total)

print(max(arr_total))
```
