---
layout: post
title: 함수
category: Baekjoon
tags: [Baekjoon]
comments: true
---

## [15596] 정수 N개의 합

문제 설명
- 정수들이 저장되어 있는 리스트를 인자로 받아 정수들의 합을 구하는 함수를 작성한다.

입력
```
```

출력
```
```

문제 분석 및 풀이
- 인자를 받아 연산 후 결과를 반환할 수 있는 함수를 작성할 수 있는지를 묻는 문제이다.

정답
```python
def solve(a):
    ans = 0
    for i in a:
        ans += i
    return ans
```

---

## [4673] 셀프 넘버

문제 설명
- 양의 정수 n에 대하여 자기 자신과 각 자릿수들을 더하는 함수 d(n)을 정의한다.
- n을 d(n)의 생성자라고 정의한다.
- 이 때, 생성자가 없는 숫자을 셀프 넘버라고 한다.
- 10,000보다 작거나 같은 셀프 넘버를 한 줄에 하나씩 오름차순으로 출력한다.

입력
```
```

출력
```
1
3
5
7
9
20
31
42
53
64
 |
 |       <-- a lot more numbers
 |
9903
9914
9925
9927
9938
9949
9960
9971
9982
9993
```

문제 분석 및 풀이
- 여러 종류의 자료형과 함수들을 사용하여 문제에서 원하는 알고리즘을 구현할 수 있는지를 묻는 문제이다.
- `[i for i in range(첫 수, (끝 수 - 1)]`을 사용하여 1부터 끝 수까지의 숫자를 데이터로 갖는 리스트를 생성한다.
- 위의 방법으로 1 ~ 10,000의 숫자를 데이터로 갖는 리스트 num을 생성한다.
- 셀프 넘버가 아닌 수들을 담을 빈 리스트 other_num을 생성한다.
- 1 ~ 10,000의 수들에 대한 함숫값들을 append 함수를 사용하여 other_num에 추가한다.
- `set(객체)` 함수를 사용하여 리스트 자료형을 집합 자료형으로 전환하여 other_num의 중복되는 요소들을 제거한다.
- num에서 other_num을 뺀 차집합으로 셀프 넘버들의 집합 self_num을 생성한다. (리스트로의 변환 필요)
- sort 함수를 사용하여 self_num을 오름차순으로 정렬한다.

정답
```python
num = [i for i in range(1, 10001)]
other_num = []
for i in num:
    other_num.append(i + (i // 1000) + ((i % 1000) // 100) + ((i % 100) // 10) + (i % 10))
self_num = list(set(num) - set(other_num))
self_num.sort()
for i in self_num:
    print(i)
```

추가
- 처음에는 다음과 같이 코딩하여 1 ~ 10,000의 각 수에 대하여 자신보다 작은 수들에 대한 모든 함숫값들과 일일이 비교하였다.
- 이 방법은 연산량이 매우 많아지기 때문에 시간 초과 에러를 발생시킨다.
```python
for i in range(1, 10001):
    for j in range(1, i + 1):
        if i != j:
            if i == j + (j // 1000) + ((j % 1000) // 100) + ((j % 100) // 10) + (j % 10):
                break
        else:
            print(i)
```

---

## [1065] 한수

문제 설명
- 양의 정수의 자릿수가 등차수열을 이룰 때, 그 수를 한수라고 한다.
- 숫자를 입력 받아 1보다 크거나 같고, 입력 받은 수보다 작거나 같은 한수의 개수를 출력한다.

입력
```
110
```
```
1
```
```
210
```
```
1000
```

출력
```
99
```
```
1
```
```
105
```
```
144
```

문제 분석 및 풀이
- 주어진 조건들을 정확히 파악하여 문제에서 원하는 알고리즘을 구현할 수 있는지를 묻는 문제이다.
- 수가 100보다 작을 경우에 그 수는 항상 한수이다.
- 수가 100보다 크거나 같고 1000보다 작을 경우에 그 수는 (백의 자릿수 - 십의 자릿수)와 (십의 자릿수 - 일의 자릿수)가 같을 때에 한수이다.

정답
```python
n = int(input())
cnt = 0
for i in range(1, n + 1):
    if i < 100 or (i // 100) - ((i % 100) // 10) == ((i % 100) // 10) - (i % 10):
        cnt += 1
print(cnt)
```