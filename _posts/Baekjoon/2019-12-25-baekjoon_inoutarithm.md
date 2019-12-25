---
layout: post
title: 입출력과 사칙연산
category: Baekjoon
tags: [Baekjoon]
comments: true
---

## [2557] Hello World

문제 설명
- Hello World! 라는 문자열을 출력한다.

입력
'''
'''

출력
'''
Hello World!
'''

문제 분석 및 풀이
- print 함수를 사용할 수 있는지를 묻는 문제이다.

정답
'''python
print('Hello World!')
'''

---

## [10718] We love kriii

문제 설명
- 강한친구 대한육군 이라는 문자열을 두 줄에 걸쳐 반복하여 출력한다.

입력
'''
'''

출력
'''
강한친구 대한육군
강한친구 대한육군
'''

문제 분석 및 풀이
- print 함수를 사용하여 개행을 할 수 있는지를 묻는 문제이다.
- '\n'을 사용하여 개행한다.
- 여러 가지 풀이들이 있겠지만 개행을 하는 방법이 가장 간단하다고 생각한다.

정답
'''python
print('강한친구 대한육군\n강한친구 대한육군')
'''

---

## [10171] 고양이

문제 설명
- 문제에서 주어진 고양이 모양의 문자열을 출력한다.

입력
'''
'''

출력
'''
\    /\
 )  ( ')
(  /  )
 \(__)|
'''

문제 분석 및 풀이
- print 함수를 사용하여 \와 '를 출력할 수 있는지를 묻는 문제이다.
- '\'를 문자 앞에 붙인다.
- '를 3개 사용하여 개행된 문자열을 입력으로 받는다.
- 다음과 같이 코딩하는 것이 시각적으로 가장 깔끔하다고 생각한다.

정답
'''python
print('''\\    /\\
 )  ( \')
(  /  )
 \\(__)|''')
'''

---

## [10172] 개

문제 설명
- 문제에서 주어진 개 모양의 문자열을 출력한다.

입력
'''
'''

출력
'''
|\_/|
|q p|   /}
( 0 )"""\
|"^"`    |
||_/=\\__|
'''

문제 분석 및 풀이
- print 함수를 사용하여 \를 출력할 수 있는지를 묻는 문제이다.
- 이전 문제와 같은 방법으로 풀면 된다.

정답
'''python
print('''|\\_/|
|q p|   /}
( 0 )"""\\
|"^"`    |
||_/=\\\\__|''')
'''

---

## [1000] A+B

문제 설명
- 두 정수를 입력 받아 (입력 정수1 + 입력 정수2)를 출력한다.

입력
'''
1 2
'''

출력
'''
3
'''

문제 분석 및 풀이
- input 함수를 사용하여 사용자로부터 숫자를 다중으로 입력 받고, + 연산 후 출력할 수 있는지를 묻는 문제이다.
- 다중으로 데이터를 입력하고자 할 때에는 'map(자료형, input.split())'을 사용한다.

정답
'''python
a, b = map(int, input().split())
print(a + b)
'''

---

## [1001] A-B

문제 설명
- 두 정수를 입력 받아 (입력 정수1 - 입력 정수2)를 출력한다.

입력
'''
3 2
'''

출력
'''
1
'''

문제 분석 및 풀이
- input 함수를 사용하여 사용자로부터 숫자를 다중으로 입력 받고, - 연산 후 출력할 수 있는지를 묻는 문제이다.
- 이전 문제와 같은 방법으로 풀면 된다.

정답
'''python
a, b = map(int, input().split())
print(a - b)
'''

---

## [10998] AxB

문제 설명
- 두 정수를 입력 받아 (입력 정수1 x 입력 정수2)를 출력한다.

입력
'''
1 2
'''
'''
3 4
'''

출력
'''
2
'''
'''
12
'''

문제 분석 및 풀이
- input 함수를 사용하여 사용자로부터 숫자를 다중으로 입력 받고, * 연산 후 출력할 수 있는지를 묻는 문제이다.
- 이전 문제와 같은 방법으로 풀면 된다.

정답
'''python
a, b = map(int, input().split())
print(a * b)
'''

---

## [1008] A/B

문제 설명
- 두 정수를 입력 받아 (입력 정수1 / 입력 정수2)를 출력한다.

입력
'''
1 3
'''
'''
4 5
'''

출력
'''
0.33333333333333333333333333333333
'''
'''
0.8
'''

문제 분석 및 풀이
- input 함수를 사용하여 사용자로부터 숫자를 다중으로 입력 받고, / 연산 후 출력할 수 있는지를 묻는 문제이다.
- 이전 문제와 같은 방법으로 풀면 된다.

정답
'''python
a, b = map(int, input().split())
print(a / b)
'''

---

## [10869] 사칙연산

문제 설명
- 두 정수를 입력 받아 (입력 정수1 +, -, x, //, % 입력 정수2)를 출력한다.

입력
'''
7 3
'''

출력
'''
10
4
21
2
1
'''

문제 분석 및 풀이
- input 함수를 사용하여 사용자로부터 숫자를 다중으로 입력 받고, +, -, x, //, % 연산 후 출력할 수 있는지를 묻는 문제이다.
- 이전 문제와 같은 방법으로 풀면 된다.

정답
'''python
a, b = map(int, input().split())
print(a + b)
print(a - b)
print(a * b)
print(a // b)
print(a % b)
'''

---

## [10430] 나머지

문제 설명
- 세 정수를 입력 받아 문제에서 주어진 나머지를 비교하는 연산의 결과들을 출력한다.

입력
'''
5 8 4
'''

출력
'''
1
1
0
0
'''

문제 분석 및 풀이
- input 함수를 사용하여 사용자로부터 숫자를 다중으로 입력 받고, 문제에서 주어진 연산 후 출력할 수 있는지를 묻는 문제이다.
- 이전 문제와 같은 방법으로 풀면 된다.

정답
'''python
a, b, c = map(int, input().split())
print((a + b) % c)
print(((a % c) + (b % c)) % c)
print((a * b) % c)
print(((a % c) * (b % c)) % c)
'''

---

## [2588] 곱셈

문제 설명
- 세 정수를 입력 받는다.
<center>
<figure>
<img src="/assets/img_posts/Baekjoon/2019-12-25-baekjoon_inoutarithm/2019-12-25-baekjoon_inoutarithm_1.png" alt="views">
<figcaption></figcaption>
</figure>
</center>
- (3), (4), (5), (6) 위치에 들어갈 값을 구한다.

입력
'''
472
385
'''

출력
'''
2360
3776
1416
181720
'''

문제 분석 및 풀이
- input 함수를 사용하여 사용자로부터 숫자를 개별적으로 입력 받고, 문제에서 원하는 값을 구한 후 출력할 수 있는지를 묻는 문제이다.
- 개별적으로 데이터를 입력하고자 할 때에는 변수들을 각각 선언해준다.
- (3), (4), (5) 값을 사용하여 (6) 값을 구하므로 모두 변수로 지정해준다.
- 10, 100으로 나눈 몫, 나머지를 적절히 사용하여 (2) 값의 각 자릿수에 접근한다.

정답
'''python
a, b = int(input()), int(input())
c = a * (b % 10)
d = a * ((b // 10) % 10)
e = a * (b // 100)
f = c + (d * 10) + (e * 100)
print(c)
print(d)
print(e)
print(f)
'''