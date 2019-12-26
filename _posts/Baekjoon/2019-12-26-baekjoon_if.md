---
layout: post
title: if문
category: Baekjoon
tags: [Baekjoon]
comments: true
---

## [1330] 두 수 비교하기

문제 설명
- 두 수를 입력 받는다.
- A가 B보다 큰 경우에는 >를, A가 B보다 작은 경우에는 <를, A와 B가 같은 경우에는 ==를 출력한다.

입력
```
1 2
```
```
10 2
```
```
5 5
```

출력
```
<
```
```
>
```
```
==
```

문제 분석 및 풀이
- if, elif, else를 사용하여 다양한 조건에 따라 데이터를 처리할 수 있는지를 묻는 문제이다.

정답
```python
a, b = map(int, input().split())
if a > b:
    print('>')
elif a < b:
    print('<')
else:
    print('==')
```

---

## [9498] 시험 성적

문제 설명
- 시험 성적을 입력 받는다.
- 90 ~ 100점은 A를, 80 ~ 89점은 B를, 70 ~ 79점은 C를, 60 ~ 69점은 D를, 나머지는 F를 출력한다.

입력
```
100
```

출력
```
A
```

문제 분석 및 풀이
- elif를 여러 번 사용하여 조건이 많을 때에 데이터를 처리할 수 있는지를 묻는 문제이다.

정답
```python
score = int(input())
if 90 <= score <= 100:
    print('A')
elif 80 <= score < 90:
    print('B')
elif 70 <= score < 80:
    print('C')
elif 60 <= score < 70:
    print('D')
else:
    print('F')
```

---

## [2753] 윤년

문제 설명
- 연도를 입력 받는다.
- 윤년은 연도가 4의 배수이면서, 100의 배수가 아닐 때 또는 400의 배수일 때이다.
- 연도가 윤년이면 1을, 아니면 0을 출력한다.

입력
```
2000
```

출력
```
1
```

문제 분석 및 풀이
- if문에서 한 줄에 복수의 조건을 사용할 수 있는지를 묻는 문제이다.
- 복수의 조건을 모두 만족시킬 때에만 True를 반환하고자 할 경우에는 `and`를 사용한다.
- 복수의 조건 중 하나만 만족시켜도 True를 반환하고자 할 경우에는 `or`을 사용한다.

정답
```python
year = int(input())
if (year % 4 == 0 and year % 100 != 0) or year % 400 == 0:
    print(1)
else:
    print(0)
```

---

## [2884] 알람 시계

문제 설명
- 시와 분을 입력 받는다.
- 45분 앞서는 시간으로 바꾸어 출력한다.
- 24시간 표현을 사용한다.

입력
```
10 10
```

출력
```
9 25
```

문제 분석 및 풀이
- if문을 사용하여 문제에서 원하는 바를 효과적으로 구현할 수 있는지를 묻는 문제이다.
- 입력 분이 45분보다 클 때에는 간단하게 45분을 빼주면 되나, 45분보다 작을 때에는 시에서 1시간을 차감하고 15분을 더해준다.
- 0시에서 1시간을 차감하면 23시가 된다.

정답
```python
h, m = map(int, input().split())
if m >= 45:
    m -= 45
elif h == 0:
    h = 23
    m += 15
else:
    h -= 1
    m += 15
print(h, m)
```

---

## [10817] 세수

문제 설명
- 세 수를 입력 받아 두 번째로 큰 수를 출력한다.

입력
```
20 30 10
```
```
30 30 10
```
```
40 40 40
```
```
20 10 10
```

출력
```
20
```
```
30
```
```
40
```
```
10
```

문제 분석 및 풀이
- if문을 사용하여 알고리즘을 효과적으로 구현할 수 있는지를 묻는 문제이다.
- Bubble Sort 알고리즘을 구현하여 세 수를 오름차순으로 정렬한다.
- Bubble Sort
-- 맨 끝에서부터 하나씩 앞의 수와 비교하면서 앞의 수가 더 큰 경우 두 수를 교환한다.
-- 그 결과, 가장 큰 수가 맨 뒤로 이동하게 된다.
-- 맨 뒤에 있는 수를 제외하고 위의 과정을 반복하면 두 번째로 큰 수가 맨 뒤에서 두 번째로 이동하게 된다.
-- 위의 과정을 (전체 수의 개수 - 1)번 반복하면 오름차순으로 정렬된다.
- 중간에 있는 값을 출력한다.

정답
```python
a, b, c = map(int, input().split())
if a > b:
    a, b = b, a
if b > c:
    b, c = c, b
if a > b:
    a, b = b, a
print(b)
```

추가
- 다음과 같이 sort 함수를 사용하면 더 편리하다.
```python
a, b, c = map(int, input().split())
asc = [a, b, c]
asc.sort()
print(asc[1])
```