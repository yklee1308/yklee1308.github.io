---
layout: post
title: 10250번 - ACM 호텔
category: Baekjoon
tags: [Baekjoon]
comments: true
---

## [10250] ACM 호텔

문제 설명
<center>
<figure>
<img src="/assets/img_posts/Baekjoon/2020-01-19-baekjoon_10250_acmhotel/2020-01-19-baekjoon_10250_acmhotel_1.png" alt="views">
<figcaption></figcaption>
</figure>
</center>
- 위의 그림은 문제에서 가정하는 직사각형 모양의 호텔의 예시이다.
- 호텔의 정문은 엘리베이터 바로 앞에 위치하고, 정문에서 엘리베이터까지의 거리는 무시한다.
- 모든 인접한 두 방 사이의 거리는 같고, 모든 방은 호텔의 정면 쪽에만 있다.
- 손님이 엘리베이터를 타고 이동하는 거리는 무시한다고 가정할 때, 손님이 걷는 거리가 짧은 방부터, 같은 거리일 때는 낮은 층의 방부터 배정한다.
- 방의 번호는 YXX 또는 YYXX 형태로 표시하고, XX는 엘리베이터에서부터 세었을 때의 번호를 의미한다.
- 테스트의 개수와 호텔의 층 수, 각 층의 방 수, 몇 번째 손님인지를 입력 받아 손님이 배정 받는 방의 번호를 출력한다.

입력
```
2
6 12 10
30 50 72
```

출력
```
402
1203
```

문제 분석 및 풀이
- 문제에서 주어진 조건을 정확하게 파악하고, 경우의 수를 나누어 알고리즘을 구현할 수 있는지를 묻는 문제이다.
- 맨 위층에 방을 배정 받는 경우와 아닌 경우로 나누어 알고리즘을 구현한다.
- 호텔 방의 개수를 초과하는 손님들이 숙박하지 않는 이상 각 층의 방 수는 큰 의미가 없다.

정답
```python
t = int(input())

for i in range(t):
    h, w, n = map(int, input().split())

    if n % h != 0:
        print(((n % h) * 100) + ((n // h) + 1))
    else:
        print((h * 100) + (n // h))
```
