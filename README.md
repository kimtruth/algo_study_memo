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


