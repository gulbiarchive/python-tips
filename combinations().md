# Motive
The time complexity of triple for loops can increase beyond imagination, slowing down the speed.

To solve the problem in an efficient way, I decided to use the `combinations()` function.

# What is Combination?
If you use `combinations()`, you must import `itertools` library.

| Iterator | Arguments | Results |
| --- | --- | --- |
| combinations() | p, r | r-length tuples, in sorted order, no re-peated elements |
<br>

| Examples | Results |
| --- | --- |
| combinations('ABCD', 2) | AB AC AD BC BD CD |

Return r length subsequences of elements from the input iterable. he combination tuples are emitted in lexicographic order according to the order of the input iterable. f the input iterable is sorted, the output tuples will be produced in sorted order.

# Related Problem
### BaekJoon 2798
- https://velog.io/@gulbi/Python3-BaekJoon-2798-%EB%B8%94%EB%9E%99%EC%9E%AD
## 문제

카지노에서 제일 인기 있는 게임 블랙잭의 규칙은 상당히 쉽다. 카드의 합이 21을 넘지 않는 한도 내에서, 카드의 합을 최대한 크게 만드는 게임이다. 블랙잭은 카지노마다 다양한 규정이 있다.

한국 최고의 블랙잭 고수 김정인은 새로운 블랙잭 규칙을 만들어 상근, 창영이와 게임하려고 한다.

김정인 버전의 블랙잭에서 각 카드에는 양의 정수가 쓰여 있다. 그 다음, 딜러는 N장의 카드를 모두 숫자가 보이도록 바닥에 놓는다. 그런 후에 딜러는 숫자 M을 크게 외친다.

이제 플레이어는 제한된 시간 안에 N장의 카드 중에서 3장의 카드를 골라야 한다. 블랙잭 변형 게임이기 때문에, 플레이어가 고른 카드의 합은 M을 넘지 않으면서 M과 최대한 가깝게 만들어야 한다.

N장의 카드에 써져 있는 숫자가 주어졌을 때, M을 넘지 않으면서 M에 최대한 가까운 카드 3장의 합을 구해 출력하시오.

## 입력

첫째 줄에 카드의 개수 N(3 ≤ N ≤ 100)과 M(10 ≤ M ≤ 300,000)이 주어진다. 둘째 줄에는 카드에 쓰여 있는 수가 주어지며, 이 값은 100,000을 넘지 않는 양의 정수이다.

합이 M을 넘지 않는 카드 3장을 찾을 수 있는 경우만 입력으로 주어진다.

## 출력

첫째 줄에 M을 넘지 않으면서 M에 최대한 가까운 카드 3장의 합을 출력한다.

## 예제 입력 1

```
5 21
5 6 7 8 9
```

## 예제 출력 1

```
21
```

## 예제 입력 2

```
10 500
93 181 245 214 315 36 185 138 216 295
```

## 예제 출력 2
```
497
```

## code
```python
from itertools import combinations

def solution(N, M, num):
    answer = 0
    for i in combinations(num, 3):
        if sum(i) <= M:
            answer = max(answer, sum(i))
            '''
            max(sum(i))가 아니라 max(answer, sum(i))인 이유:
            반복해서 누적되는 answer과 sum(i) 비교(answer이 계속 0이 아님)
            '''
    return answer


N, M = map(int, input().split())
num = list(map(int, input().split()))

print(solution(N, M, num))
```


### Programmers 701128
- https://velog.io/@gulbi/Python3Programmers-131705-%EC%82%BC%EC%B4%9D%EC%82%AC
### **문제 설명**

한국중학교에 다니는 학생들은 각자 정수 번호를 갖고 있습니다. 이 학교 학생 3명의 정수 번호를 더했을 때 0이 되면 3명의 학생은 삼총사라고 합니다. 예를 들어, 5명의 학생이 있고, 각각의 정수 번호가 순서대로 -2, 3, 0, 2, -5일 때, 첫 번째, 세 번째, 네 번째 학생의 정수 번호를 더하면 0이므로 세 학생은 삼총사입니다. 또한, 두 번째, 네 번째, 다섯 번째 학생의 정수 번호를 더해도 0이므로 세 학생도 삼총사입니다. 따라서 이 경우 한국중학교에서는 두 가지 방법으로 삼총사를 만들 수 있습니다.

한국중학교 학생들의 번호를 나타내는 정수 배열 `number`가 매개변수로 주어질 때, 학생들 중 삼총사를 만들 수 있는 방법의 수를 return 하도록 solution 함수를 완성하세요.

---

### 제한사항

- 3 ≤ `number`의 길이 ≤ 13
- 1,000 ≤ `number`의 각 원소 ≤ 1,000
- 서로 다른 학생의 정수 번호가 같을 수 있습니다.

---

### 입출력 예

| number | result |  |
| --- | --- | --- |
| [-2, 3, 0, 2, -5] | 2 |  |
| [-3, -2, -1, 0, 1, 2, 3] | 5 |  |
| [-1, 1, -1, 1] | 0 |  |

---

### 입출력 예 설명

**입출력 예 #1**

- 문제 예시와 같습니다.

**입출력 예 #2**

- 학생들의 정수 번호 쌍 (-3, 0, 3), (-2, 0, 2), (-1, 0, 1), (-2, -1, 3), (-3, 1, 2) 이 삼총사가 될 수 있으므로, 5를 return 합니다.

**입출력 예 #3**

- 삼총사가 될 수 있는 방법이 없습니다.

### code
```python
from itertools import combinations

def solution(number):
    answer = 0
    for i in combinations(number, 3):
        if sum(i) == 0:
            answer += 1
    return answer

'''
combinations('ABCD', 2)
AB AC AD BC BD CD 
'''
```
