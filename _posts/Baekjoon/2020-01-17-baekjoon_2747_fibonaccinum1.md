---
layout: post
title: \[2747\] 피보나치 수
category: Baekjoon
tags: [Baekjoon]
comments: true
---

## [2747] 피보나치 수

문제 설명
- n번째 피보나치 수는 (n - 2)번째 피보나치 수와 (n - 1)번째 피보나치 수의 합이다.
- 0번째 피보나치 수는 0이고, 1번째 피보나치 수는 1이다.
- 자연수 n을 입력 받아 n번째 피보나치 수를 출력한다.

입력
```
10
```

출력
```
55
```

문제 분석 및 풀이
- 리스트를 사용하여 피보나치 함수를 구현할 수 있는지를 묻는 문제이다.
- 피보나치 함수의 인자로 자연수를 받는다.
- 0번째와 1번째 피보나치 수를 요소로 갖는 피보나치 리스트를 생성한다.
- 0을 입력으로 받으면 리스트의 0번째 요소를 출력하고, 1을 입력으로 받으면 1번째 요소를 반환한다.
- 2 이상의 자연수를 입력으로 받을 경우에는 2번째부터 입력 받은 자연수 번째까지의 피보나치 수들을 차례대로 계산하여 피보나치 리스트에 추가한다.
- 마지막으로 리스트의 마지막 요소인 n번째 피보나치 수를 반환한다.

정답
```python
n = int(input())

def fibonacci(num):
    fib = [0, 1]

    if num == 0:
        return fib[0]
    elif num == 1:
        return fib[1]
    else:
        for i in range(2, num + 1):
            fib.append(fib[i - 2] + fib[i - 1])
        return fib[num]

print(fibonacci(n))
```

추가
- 재귀함수(Recursive function)를 사용하여 피보나치 함수를 구현하는 방법도 있다.
- 이 방법은 연산량이 매우 많아지기 때문에 시간 초과 에러를 발생시킨다.
```python
n = int(input())

def fibonacci(num):
    if num == 0:
        return 0
    elif num == 1:
        return 1
    else:
        return fibonacci(num - 2) + fibonacci(num - 1)

print(fibonacci(n))
```
