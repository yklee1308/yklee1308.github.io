---
layout: post
title: 문자열
category: Baekjoon
tags: [Baekjoon]
comments: true
---

## [11654] 아스키 코드

문제 설명
- 알파벳 소문자, 대문자, 숫자 0 ~ 9 중의 하나를 입력 받고, 글자의 아스키 코드 값을 출력한다.

입력
```
A
```
```
C
```
```
0
```
```
9
```
```
a
```
```
z
```

출력
```
65
```
```
67
```
```
48
```
```
57
```
```
97
```
```
122
```

문제 분석 및 풀이
- 문자와 아스키 코드 값의 관계에 대해 이해하고 있는지를 묻는 문제이다.
- ord 함수를 사용하여 문자에 대한 아스키 코드 값을 구한다.

정답
```python
ltr = input()
print(ord(ltr))
```

---

## [11720] 숫자의 합

문제 설명
- 숫자의 개수와 개수만큼의 숫자들을 공백 없이 입력 받고, 모든 숫자의 합을 구하여 출력한다.

입력
```
1
1
```
```
5
54321
```
```
25
7000000000000000000000000
```
```
11
10987654321
```

출력
```
1
```
```
15
```
```
7
```
```
46
```

문제 분석 및 풀이
- 문자열 자료형을 리스트 자료형으로 전환하여 데이터를 처리할 수 있는지를 묻는 문제이다.
- 파이썬에서는 입력 받는 숫자의 개수에 상관 없이 랜덤한 개수의 숫자들을 입력 받을 수 있다.

정답
```python
n = int(input())
text = input()
arr = list(map(int, list(text)))
print(sum(arr))
```

---

## [10809] 알파벳 찾기

문제 설명
- 알파벳 소문자로만 이루어진 단어를 입력 받는다.
- 각각의 알파벳에 대하여 알파벳이 단어에 포함되어 있는 경우, 처음 등장하는 위치를 출력한다.
- 알파벳이 단어에 포함되어 있지 않은 경우에는 -1을 출력한다.

입력
```
baekjoon
```

출력
```
1 0 -1 -1 2 -1 -1 -1 -1 4 3 -1 -1 7 5 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1 -1
```

문제 분석 및 풀이
- 문자열 자료형을 리스트 자료형으로 전환하고, 아스키 코드 값을 사용하여 데이터를 처리할 수 있는지를 묻는 문제이다.
- if문의 조건에 in을 사용하여 찾고자 하는 숫자가 리스트 안에 존재하는지 확인한다.

정답
```python
s = input()
arr = list(map(ord, list(s)))
ab = ord('a')
for i in range(26):
    if ab in arr:
        print(arr.index(ab), end='')
    else:
        print(-1, end='')
    if i < 25:
        print(end=' ')
    ab += 1
```

---

## [2675] 문자열 반복

문제 설명
- 테스트의 개수를 입력 받는다.
- 반복 횟수와 문자열을 입력 받고, 각 문자를 입력 받은 수만큼 반복하여 새 문자열을 만들어 출력한다.

입력
```
2
3 ABC
5 /HTP
```

출력
```
AAABBBCCC
/////HHHHHTTTTTPPPPP
```

문제 분석 및 풀이
- 두 개 이상의 다른 자료형을 문자열 자료형으로 입력 받아 원하는 자료형으로 전환을 할 수 있는지를 묻는 문제이다.
- 두 개 이상의 다른 자료형을 공백으로 구분하여 입력 받고자 할 때에는 input().split()으로 먼저 입력을 받은 후에 자료형 변환을 한다.

정답
```python
t = int(input())
for i in range(t):
    r, s = input().split()
    r = int(r)
    arr = list(s)
    for j in arr:
        print(j * r, end='')
    print(' ')
```

---

## [1157] 단어 공부

문제 설명
- 알파벳 대소문자로 이루어진 단어를 입력 받고, 가장 많이 사용된 알파벳을 대문자로 출력한다.
- 가장 많이 사용된 알파벳이 여러 개 존재하는 경우에는 ?를 출력한다.
- 대문자와 소문자는 구분하지 않는다.

입력
```
Mississipi
```
```
zZa
```
```
z
```
```
baaa
```

출력
```
?
```
```
Z
```
```
Z
```
```
A
```

문제 분석 및 풀이
- 문자열 자료형을 리스트 자료형으로 전환하고, 아스키 코드 값을 사용하여 문제에서 원하는 알고리즘을 구현할 수 있는지를 묻는 문제이다.
- 알파벳 대문자의 아스키 코드 값은 소문자의 아스키 코드 값보다 32만큼 작다.
- set 함수를 사용하여 단어 내의 중복된 문자들을 제거한 리스트 dedupe를 생성한다.
- 단어가 하나의 문자로 이루어진 경우, 그 문자를 출력한다.
- 단어가 여러 개의 문자로 이루어진 경우에는 각 문자의 개수들을 담는 리스트 cnt를 생성한다.
- 문자 개수의 최댓값이 하나일 때에는 최댓값에 해당하는 문자를 출력하고, 두 개 이상일 때에는 ?를 출력한다.

정답
```python
word = input()
arr = list(map(ord, list(word)))
for i in range(len(arr)):
    if arr[i] >= ord('a'):
        arr[i] -= 32
dedupe = list(set(arr))
if len(dedupe) == 1:
    print(chr(dedupe[0]))
else:
    cnt = []
    for i in dedupe:
        cnt.append(arr.count(i))
    if cnt.count(max(cnt)) == 1:
        print(chr(dedupe[cnt.index(max(cnt))]))
    else:
        print('?')
```

추가
- 다음과 같이 upper 함수를 사용하여 소문자를 대문자로 변경하면 더 편리하다.
- upper 함수는 대소문자로 영구적으로 변경하지 않으므로 변경한 결과를 변수에 다시 저장한다.
```python
word = input()
word = word.upper()
arr = list(map(ord, list(word)))
dedupe = list(set(arr))
if len(dedupe) == 1:
    print(chr(dedupe[0]))
else:
    cnt = []
    for i in dedupe:
        cnt.append(arr.count(i))
    if cnt.count(max(cnt)) == 1:
        print(chr(dedupe[cnt.index(max(cnt))]))
    else:
        print('?')
```

---

## [1152] 단어의 개수

문제 설명
- 알파벳 대소문자와 띄어쓰기로 이루어진 문자열을 입력 받고, 문자열 내의 단어의 개수를 출력한다.
- 단어는 띄어쓰기 하나로 구분한다.

입력
```
The Curious Case of Benjamin Button
```
```
 Mazatneunde Wae Teullyeoyo
```
```
Teullinika Teullyeotzi
```

출력
```
6
```
```
3
```
```
2
```

문제 분석 및 풀이
- 문자열 자료형을 리스트 자료형으로 전환하고, 찾고자하는 요소의 개수를 셀 수 있는지를 묻는 문제이다.
- 문자열의 왼쪽이나 오른쪽에 공백이 존재하는 경우, 각 경우에 대하여 cnt를 1만큼 감소시킨다.

정답
```python
text = input()
arr = list(text)
cnt = arr.count(' ') + 1
if arr[0] == ' ':
    cnt -= 1
if arr[len(arr) - 1] == ' ':
    cnt -= 1
print(cnt)
```

추가
- 다음과 같이 strip 함수를 사용하여 문자열 양쪽에 존재하는 공백을 제거하면 더 편리하다.
- strip 함수는 공백을 영구적으로 제거하지 않으므로 제거한 결과를 변수에 다시 저장한다.
- 공백을 입력 받을 경우에는 마지막에 cnt를 0으로 초기화한다.
```python
text = input()
text = text.strip()
arr = list(text)
cnt = arr.count(' ') + 1
if text == '':
    cnt = 0
print(cnt)
```

---

## [2908] 상수

문제 설명
- 서로 다른 두 세 자리 수를 입력 받는다.
- 두 수를 거꾸로 뒤집은 후, 더 큰 수를 출력한다.

입력
```
734 893
```

출력
```
437
```

문제 분석 및 풀이
- 리스트 자료형을 문자열 자료형으로 전환할 수 있는지를 묻는 문제이다.
- reverse 함수를 사용하여 리스트 내 요소들을 역순으로 뒤집는다.
- 새로운 문자열을 생성하여 리스트 내의 문자 요소들을 + 연산을 통해 이어붙인다.

정답
```python
a, b = map(list, input().split())
a.reverse()
b.reverse()
a_rev, b_rev = '', ''
for i in range(3):
    a_rev += a[i]
    b_rev += b[i]
if a_rev > b_rev:
    print(a_rev)
else:
    print(b_rev)
```

---

## [5622] 다이얼

문제 설명
- 알파벳으로 이루어진 단어를 입력 받는다.
<center>
<figure>
<img src="/assets/img_posts/Baekjoon/2020-01-16-baekjoon_str/2020-01-16-baekjoon_str_1.png" alt="views">
<figcaption></figcaption>
</figure>
</center>
- 각 알파벳에 해당하는 숫자는 다이얼 전화기에 적혀 있다.
- 각 숫자를 입력하는 데에는 (수 + 1)초가 걸린다.
- 단어에 해당하는 숫자들을 모두 입력하는 데에 걸리는 시간을 출력한다.

입력
```
UNUCIC
```

출력
```
36
```

문제 풀이 및 설명
- 문자열 자료형을 리스트 자료형으로 전환하고, 다양한 경우에 따라 데이터를 처리할 수 있는지를 묻는 문제이다.

정답
```python
word = input()
arr = list(word)
time = 0
for i in arr:
    if i == 'A' or i == 'B' or i == 'C':
        time += 3
    elif i == 'D' or i == 'E' or i == 'F':
        time += 4
    elif i == 'G' or i == 'H' or i == 'I':
        time += 5
    elif i == 'J' or i == 'K' or i == 'L':
        time += 6
    elif i == 'M' or i == 'N' or i == 'O':
        time += 7
    elif i == 'P' or i == 'Q' or i == 'R' or i == 'S':
        time += 8
    elif i == 'T' or i == 'U' or i == 'V':
        time += 9
    elif i == 'W' or i == 'X' or i == 'Y' or i == 'Z':
        time += 10
print(time)
```
---

## [2941] 크로아티아 알파벳

문제 설명
- 크로아티아 알파벳으로 이루어진 단어를 입력 받고, 단어가 몇 개의 크로아티아 알파벳으로 이루어져 있는지를 출력한다.
- c=, c-, dz=, d-, lj, nj, s=, z=는 한 알파벳으로 취급한다.
- 앞서 언급한 알파벳들을 제외한 나머지는 한 글자씩 알파벳으로 취급한다.

입력
```
ljes=njak
```
```
ddz=z=
```
```
nljj
```
```
c=c=
```

출력
```
6
```
```
3
```
```
3
```
```
3
```

문제 풀이 및 설명
- 문자열 자료형을 리스트 자료형으로 전환하고, 복잡하고 다양한 경우에 따라 데이터를 처리할 수 있는지를 묻는 문제이다.
- 두 글자 이상의 크로아티아 알파벳들은 맨 뒷글자부터 접근할 때에 고려할 경우의 수가 적어지므로 단어의 맨 끝에서부터 접근한다.
- 리스트 내의 요소들을 맨 끝에서부터 접근하기 위해 `range(끝 요소의 위치, (첫 요소의 위치 - 1), -1)`을 사용한다.
- 두 글자의 알파벳인 경우에는 cnt를 1만큼 증가시키고, 세 글자의 알파벳인 경우에는 2만큼 증가시킨다.
- 단어의 전체 글자 수에서 cnt를 빼 크로아티아 알파벳의 개수를 구한다.

정답
```python
word = input()
arr = list(word)
cnt = 0
for i in range(len(arr) - 1, 0, -1):
    if arr[i] == '=':
        if arr[i - 1] == 'c' or arr[i - 1] == 's':
            cnt += 1
        elif arr[i - 1] == 'z':
            cnt += 1
            if i > 1 and arr[i - 2] == 'd':
                cnt += 1
    elif arr[i] == '-' and (arr[i - 1] == 'c' or arr[i - 1] == 'd'):
        cnt += 1
    elif arr[i] == 'j' and (arr[i - 1] == 'l' or arr[i - 1] == 'n'):
        cnt += 1
print(len(arr) - cnt)
```

추가
- 다음과 같이 replace 함수를 사용하면 더 간단하다.
- 두 글자 이상의 크로아티아 알파벳들을 요소로 갖는 리스트 hrv를 생성한다.
- for문 안에 in을 사용하여 리스트 내의 알파벳이 단어에 존재하는지 확인한다.
- 단어 안에 리스트 내의 알파벳이 존재할 경우, 알파벳을 *로 바꾼다.
- replace 함수는 문자열을 영구적으로 변경하지 않으므로 변경한 결과를 변수에 다시 저장한다.
```python
word = input()
hrv = ['c=', 'c-', 'dz=', 'd-', 'lj', 'nj', 's=', 'z=']
for i in hrv:
    if i in word:
        word = word.replace(i, '*')
print(len(word))
```

---

## [1316] 그룹 단어 체커

문제 설명
- 단어에 존재하는 모든 문자에 대하여 각 문자가 모두 연속해서 나타나는 경우, 그 단어를 그룹 단어라고 한다.
- 단어의 개수와 개수만큼의 단어를 입력 받고, 그룹 단어의 개수를 출력한다.

입력
```
3
happy
new
year
```
```
4
aba
abab
abcabc
a
```

출력
```
3
```
```
1
```

문제 분석 및 풀이
- 문자열 자료형을 리스트 자료형으로 전환하고, 이중 for문을 사용하여 문제에서 원하는 알고리즘을 구현할 수 있는지를 묻는 문제이다.
- 이 문제에서는 그룹 단어를 찾는 조건이 그 반대에 비해 비교적 까다로우므로 반례를 찾는 알고리즘을 구현하는 것이 더 좋다고 생각한다.
- 입력 받은 단어의 글자들을 요소로 갖는 리스트 arr를 생성한 후, arr를 복사하고 리스트 내의 요소들을 역순으로 뒤집어 리스트 rev를 생성한다.
- `리스트[:]`을 사용하여 리스트를 복사한다.
- set 함수를 사용하여 단어 내의 중복된 문자들을 제거한 리스트 dedupe를 생성한다.
- remove 함수를 사용하여 dedupe의 요소들 중에서 arr 내에 하나만 존재하는 글자들을 제거한다.
- arr 내에 두 개 이상 존재하는 글자에 대하여 문자열 내 해당 글자의 첫 위치와 끝 위치를 찾는다.
- index 함수를 arr과 rev에 사용하여 첫 위치와 끝 위치를 찾는다.
- 해당 글자의 첫 위치와 끝 위치 사이에 해당 글자와 다른 글자가 존재할 경우, cnt를 1만큼 증가시키고 이중 for문을 빠져나간다.
- 변수가 True인지 False인지를 확인할 때에는 == 대신에 `is`를 사용한다.
- 입력 받은 단어의 개수에서 cnt를 빼 그룹 단어의 개수를 구한다.

정답
```python
n = int(input())
cnt = 0
for i in range(n):
    word = input()
    arr = list(word)
    rev = arr[:]
    rev.reverse()
    dedupe = list(set(arr))
    for j in dedupe:
        if arr.count(j) == 1:
            dedupe.remove(j)
    for j in dedupe:
        stay = True
        for m in range(arr.index(j), (len(arr) - rev.index(j)) - 2):
            if arr[m] != arr[m + 1]:
                cnt += 1
                stay = False
                break
        if stay is False:
            break
print(n - cnt)
```
