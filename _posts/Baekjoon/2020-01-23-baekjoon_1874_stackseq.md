---
layout: post
title: 1874번 - 스택 수열
category: Baekjoon
tags: [Baekjoon]
comments: true
---

## [1874] 스택 수열

문제 설명
- 스택은 데이터를 넣는(push) 입구와 뽑는(pop) 입구가 같아 제일 나중에 들어간 데이터가 제일 먼저 나오는 특성(LIFO, last in first out)을 가진다.
- 1부터 n까지의 수를 오름차순으로 스택에 넣었다가 뽑아 늘어놓음으로써, 하나의 수열을 만든다.
- 이 때, push와 pop 연산의 순서는 랜덤하다.
- 정수의 개수와 수열을 이루는 1부터 n까지의 정수들을 랜덤하게 하나씩 입력 받고, 어떤 순서로 push, pop 연산을 수행하는지를 출력한다.
- 수열을 만들 수 없을 경우에는 NO를 출력한다.

입력
```
8
4
3
6
8
7
5
2
1
```
```
5
1
2
5
3
4
```

출력
```
+
+
+
+
-
-
+
+
-
+
+
-
-
-
-
-
```
```
NO
```

문제 분석 및 풀이
- 경우의 수를 나누어 알고리즘을 구현할 수 있는지를 묻는 문제이다.
- 1부터 n까지의 수를 오름차순으로 담은 리스트 arr와 stack 안에 있는 수들을 담는 리스트 stack을 생성한다.
- 입력 받은 수열의 수 term과 이전 입력의 수열의 수 curr를 생성한다.
- term을 입력 받을 때에는 input 함수 대신에 sys.stdin.readline()을 사용하여 입력 받는 시간을 줄인다.
- push 또는 pop 연산의 순서를 담는 리스트 opr를 생성한다.
- term이 curr보다 큰 경우와 작은 경우로 나누어 알고리즘을 구현한다.
- term이 curr보다 큰 경우, arr에서 맨 앞의 수를 꺼내 stack에 추가하고 curr에 저장한 후, opr에 +를 추가한다.
- 위의 과정을 반복하다가 curr가 term과 같아지면, stack에서 마지막 수를 꺼내고 opr에 -를 추가한 후, 다음 입력을 받는다.
- term이 curr보다 작은 경우에는 stack에서 마지막 수를 꺼내 curr에 저장하고, opr에 -를 추가한다.
- 위의 과정을 반복하다가 curr가 term과 같아지면, 다음 입력을 받는다.
- term이 curr보다 큰 경우에 만일 term이 arr에 존재하지 않는다면 전체 루프를 빠져나온다.
- term이 curr보다 작은 경우에는 term이 stack에 존재하지 않을 때에 전체 루프를 빠져나온다.
- 또한, 입력 받을 수가 남아있으나 arr와 stack에 아무것도 존재하지 않을 때에는 stack에 *을 추가한 후, 루프를 빠져나온다.
- 최종적으로 for문을 빠져나왔을 때에 arr와 stack에 요소가 존재하면 정상적으로 수열을 만들 수 없는 경우이므로 NO를 출력한다.
- arr와 stack에 요소가 존재하지 않으면 정상적으로 수열을 만들 수 있는 경우이므로 opr에 저장된 push, pop 연산 결과를 차례대로 출력한다.

정답
```python
import sys

n = int(input())
arr = [i for i in range(1, n + 1)]
stack = []
opr = []
curr = 0

for i in range(n):
    term = int(sys.stdin.readline())

    if arr == [] and stack == []:
        stack.append('*')
        break

    if term > curr:
        if term in arr:
            while True:
                if curr == term:
                    stack.pop(-1)
                    opr.append('-')
                    break
                curr = arr.pop(0)
                stack.append(curr)
                opr.append('+')
        else:
            break
    elif term < curr:
        if term in stack:
            while True:
                curr = stack.pop(-1)
                opr.append('-')
                if curr == term:
                    break
        else:
            break

if arr == [] and stack == []:
    for i in range(len(opr)):
        print(opr[i])
else:
    print('NO')
```

추가
- 처음에는 다음과 같이 코딩하여 push, pop 연산 결과를 수를 입력 받을 때마다 즉시 출력하고, 수열을 만들 수 없는 경우가 되었을 때에 NO를 추가적으로 출력하였다.
- 문제의 출력 형식에 따르면 수열을 만들 수 없는 경우에는 NO만을 출력해야 하기 때문에 중간에 push, pop 연산 결과를 출력하는 이 방법은 출력 형식 에러를 발생시킨다.

```python
import sys

n = int(input())
arr = [i for i in range(1, n + 1)]
stack = []
curr = 0

for i in range(n):
    term = int(sys.stdin.readline())

    if term > curr:
        if term in arr:
            while True:
                if curr == term:
                    stack.pop(-1)
                    print('-')
                    break
                curr = arr.pop(0)
                stack.append(curr)
                print('+')
        else:
            print('NO')
    else:
        if term in stack:
            while True:
                curr = stack.pop(-1)
                print('-')
                if curr == term:
                    break
        else:
            print('NO')
```
