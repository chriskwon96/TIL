# carrot problem

> 영준이의 당근밭은 N개의 구역으로 나뉘어 있다. 당근을 수확한 구역 순으로 당근의 개수 C가 주어질 때, 가장 많은 당근이 나온 구역은 몇 번 째 인지와 그 구역의 당근 개수를 출력하는 프로그램을 만드시오. 단, 당근의 수가 같은 구역이 있을 때는 먼저 수확한 구역의 순서를 출력한다.
> 5<=N<=1000, 1<=C<1000
>
> 입력
> 첫 줄에 테스트케이스 개수 T가 주어진다. 다음 줄 부터 각 테스트 케이스 첫 줄에 구역의 수 N이 주어지고, 다음 줄에 각 구역의 당근의 개수 C를 의미하는 N개의 수가 주어진다.
>
> 출력
> \#테스트케이스번호, 구역의 순서와 당근의 개수를 빈칸을 두고 출력한다.

* input

```reStructuredText
3
5
948 313 785 388 930 
10
145 642 753 157 660 415 625 718 310 481 
20
379 644 716 21 608 819 321 391 227 58 294 687 764 295 412 540 494 10 414 942
```

* code

```python
T = int(input()) # test_cases
attempts = 1

while T:
    sctn = int(input()) # number of sections

    carrots = list(map(int, input().split()))

    max_v = 0

    for carrot in carrots:
        if max_v < carrot:
            max_v = carrot


    num_sctn = carrots.index(max_v)+1
    print('#{} {} {}'.format(attempts, num_sctn, max_v))
    T -= 1
    attempts +=1
```

* output

```python
#1 1 948
#2 3 753
#3 20 942
```

* +@

```python
# index 만 계산하고 그걸 이용해서 값을 불러내면 더 가벼워짐 @@@@@@@@@@@@@@@@@@@@@@@@@
```



---

# 순열

```python
for i in range(1,4):
    for j in range(1,4):
        if i != j :
            for k in range(1,4):
                if k!=i and k !=j :
                    print(i, j, k)
```

```python
1 2 3
1 3 2
2 1 3
2 3 1
3 1 2
3 2 1
```

```python
a = [1, 5, 7]

for i in range(3):
    for j in range(3):
        if i != j:
            for k in range(3):
                if k != j and k!=i :
                    print(a[i], a[j], a[k])
```

```python
1 5 7
1 7 5
5 1 7
5 7 1
7 1 5
7 5 1
```



---

# Baby_gin

> 0-9 사이의 숫자 카드에서 임의의 카드 6장을 뽑았을 때, 3장의 카드가 연속적인 번호를 갖는 경우를 run이라 하고, 3장의 카드가 동일한 번호를 갖는 경우를 triplet이라고 한다. 
>
> 그리고 6장의 카드가 run 과 triplet로만 구성된 경우를 `baby-gin`으로 부른다.

```python
nums = [4, 5, 6, 7, 7, 9]
#list(map(int, input().split()))

nums = list(input())

count = [0]*10
for num in nums:
    count[int(num)] += 1

print(count)

```

```python
456779
[0, 0, 0, 0, 1, 1, 1, 2, 0, 1]
```



---

# Bubble sort

> 인접한 두 개의 원소를 비교하며 자리를 계속 교환하는 방식 

정렬 과정

* 첫 번째 원소부터 인접한 원소끼리 계속 자리를 교환하면서 맨 마지막 자리까지 이동.
* 한 단계가 끝나면 가장 큰 원소가 마지막 자리로 정렬됨
* 시간 복잡도 = O(n^2)

```python
def bubble(x):

    for i in range(len(a)-1, 0, -1):
        for j in range(0, i):
            if a[j] > a[j+1]:
                a[j], a[j+1] = a[j+1], a[j]

    return x




a = [7, 4, 3, 2, 5, 4]

a= bubble(a)
print(a)

```

```python
[2, 3, 4, 4, 5, 7]
```



---

# Counting sort

> 항목들의 순서를 결정하기 위해 집합에 각 항목이 몇 개씩 있는지 세는 작업을 하여, 선형 시간에 정렬하는 효율적인 알고리즘

* 정수나 정수로 표현할 수 있는 자료에 대해서만 적용 가능
* 카운트들을 위한 충분한 공간을 할당하려면 집합 내의 가장 큰 정수를 알아야 한다. 
* 시간 복잡도 = O(n+k): n =length of list, k=max of int

```python

A = [0, 4, 1, 3, 1, 2, 4, 1]

final = [0]*len(A)
count = [0]*(max(A)+1)

for i in A: # make count array
    count[i] += 1


for j in range(1, len(count)): # changed count array, 누적합
    count[j] = count[j-1]+count[j]

for k in range(len(A)):
    count[A[k]] -= 1
    final[count[A[k]]] = A[k]

print(final)
```

```python
[0, 1, 1, 1, 2, 3, 4, 4]
```

---

# view

```python
# buildings = [0, 0, 3, 5, 2, 0, 0]


T = 10


for t in range(1, T+1):

    num_builds = int(input())
    buildings = list(map(int, input().split()))


    def view():
        arr = []
        arr.append(buildings[i] - buildings[i - 2])
        arr.append(buildings[i] - buildings[i - 1])
        arr.append(buildings[i] - buildings[i + 1])
        arr.append(buildings[i] - buildings[i + 2])
        return min(arr)

    total = 0

    for i in range(2, len(buildings)-1):
        if buildings[i] > buildings[i-2] and buildings[i] > buildings[i-1] and buildings[i] > buildings[i+1] and buildings[i] > buildings[i+2]:
            total += view()

    print('#{} {}'.format(t, total))

```

```python
100
0 0 225 214 82 73 241 233 179 219 135 62 36 13 6 71 179 77 67 139 31 90 9 37 93 203 150 69 19 137 28 174 32 80 64 54 18 0 158 73 173 20 0 102 107 48 50 161 246 145 225 31 0 153 185 157 44 126 153 233 0 201 83 103 191 0 45 0 131 87 97 105 97 209 157 22 0 29 132 74 2 232 44 203 0 51 0 244 212 212 89 53 50 244 207 144 72 143 0 0
```

```python
691
```

```python
# 가장 큰거만 찾아서 빼도 돼!@@@@@@@@@@@@@@@@@@@
```





---

# carrot harvesting

```python
T = int(input())


for t in range(1, T+1):
    sctn = int(input())
    carrots = list(map(int,input().split()))

    man1 = 0
    man2 = 0
    i = 0

    avg = sum(carrots) / 2

    while man1 < avg:
        man1 += carrots[i]
        i += 1
        if man1 > avg:
            break

    over = man1
    under = man1 - carrots[i - 1]

    if min(abs(over - avg), abs(under - avg)) == abs(over - avg):
        idx = i
        man1 = sum(carrots[:idx])
        man2 = sum(carrots[idx:])
    else:
        idx = i - 1
        man1 = sum(carrots[:idx])
        man2 = sum(carrots[idx:])

    print('#{} {} {}'.foramt(t, idx, abs(man1 - man2)))
```




