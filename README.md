# algo_study_memo
오늘은 공부를 했는가?


# acmicpc.net
#### 2018.02.19
[1406 - 에디터](https://www.acmicpc.net/problem/1406) : 커서를 기준으로 좌우에 스택을 두었다.

[10799 - 쇠막대기](https://www.acmicpc.net/problem/10799) : 스택의 크기를 이용해서 계산했다.

[1158 - 조세퍼스 문제](https://www.acmicpc.net/problem/1158) : 덱을 이용하여 앞글자를 뒤로 옮기며 순환하게 하고 처리했다.

#### 2018.02.20
[1463 - 1로 만들기](https://www.acmicpc.net/problem/1463) : 2로 나누어진다면 min(D[N-1], D[N/2]), 3으로 나누어진다면 min(D[n-1], D[N/3]) 으로 계산했다.

[11726 - 2xn 타일링](https://www.acmicpc.net/problem/11726) : 첫번째가 가로로 놓여질지 세로로 놓여질지로 구분했다.<br> D[N] = D[N - 1] + D[N - 2]

[11727 - 2xn 타일링 2](https://www.acmicpc.net/problem/11727) : 첫번째가 가로로 놓여질지 세로로 놓여질지로 구분했다. 가로의 경우 2x2 짜리일 때도 추가해줬다.<br> D[N] = D[N - 1] + D[N - 2] * 2

[9095 - 1, 2, 3 더하기](https://www.acmicpc.net/problem/9095) : N을 합으로 나타낼 때, 첫 번째 항이 1, 2, 3 인경우로 나눠서 모두 더해줬다.<br> D[N] = D[N - 1] + D[N - 2] + D[N - 3]

[11052 - 붕어빵 판매하기](https://www.acmicpc.net/problem/11052) : 1 ~ N 개를 팔 때 얻을 수 있는 최대 수익을 모두 구해줘야 했다. O(n<sup>2</sup>).<br> for(i = 1;i <= N;i++) { for(j=1; j<=i; j++) P[i] = max(P[i], P[j] + P[i-j])}

#### 2018.02.21
[2193 - 이친수](https://www.acmicpc.net/problem/2193) : 숫자가 맨 끝이 0으로 끝나는 경우의 수를 Z, 1로 끝나는 경우의 수를 W라고 하면 <br> Z<sub>i</sub> = Z<sub>i-1</sub> + W<sub>i-1</sub>, W<sub>i</sub> = Z<sub>i-1</sub>를 만족하는 것을 이용했다.

[10844 - 쉬운 계단 수](https://www.acmicpc.net/problem/10844) : N번째 값에 L이 나올 경우의 수는 N - 1번째 값에 L - 1이 있거나 L + 1일 경우로 생각하고 풀었다.
```python
for i in range(2, N + 1):
    D[i] = [0] * 10
    for j in range(0, 10):
        if 0 <= j - 1:
            D[i][j - 1] += D[i - 1][j] % mod
        if j + 1 <= 9:
            D[i][j + 1] += D[i - 1][j] % mod
```

[11057 - 오르막 수](https://www.acmicpc.net/problem/11057) : 두 가지 풀이법이 가능했다. Binomial coefficient(9 + N, 9)의 값을 구해주는 것. 또는 앞에 나온 숫자를 기반으로 뒤에 무슨 숫자가 나올 수 있는지로 계속 더해줬다.
```python
for i in range(2, N + 1):
    D[i] = [0] * 10
    for j in range(0, 10):
        for k in range(j, 10):
            D[i][k] += D[i - 1][j]
```

[9465 - 스티커](https://www.acmicpc.net/problem/9465) : 스티커를 때는 상태를 구분했다. 세로 1줄을 기준으로 아무것도 때지 않는 경우, 위에만 때는 경우, 아래만 때는 경우 총 3가지 경우다.
```python
for i in range(1, N):
    D[i][0] = max(D[i - 1][0], D[i - 1][1], D[i - 1][2])
    D[i][1] = max(D[i - 1][0], D[i - 1][2]) + A[0][i]
    D[i][2] = max(D[i - 1][0], D[i - 1][1]) + A[1][i]
```

#### 2018.02.23

[2156 - 포도주 시식](https://www.acmicpc.net/problem/2156) : 앞서 스티커에서 상태를 이용했듯이 이 문제도 상태를 이용하려 했다. N번째 열에서 포도주를 마시는게 몇 번 연속되게 되는가? 로 상태를 잡고 0번 연속, 1번 연속, 2번 연속으로 경우를 나눴다.
```python
for i in range(1, N):
    D[i][0] = max(D[i - 1][0], D[i - 1][1], D[i - 1][2])
    D[i][1] = D[i - 1][0] + A[i]
    D[i][2] = D[i - 1][1] + A[i]
```

[11053 - 가장 긴 증가하는 부분 수열](https://www.acmicpc.net/problem/11053) : D[N]에는 최대로 가질 수 있는 수열의 길이를 담았다. 이전의 값들과 비교하여 이어질 수 있다면 최대값과 이어지는 느낌으로 해싸.
```python
for i in range(0, N):
    D[i] = 1
    for j in range(0, i):
        if A[j] < A[i] and D[j] + 1 > D[i]:
            D[i] = D[j] + 1
```
