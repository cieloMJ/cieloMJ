### 풀이 코드
```
for tc in range(1, 11):
    N = int(input())
    h= list(map(int, input().split()))
    for i in range(N):
        a= h.index(max(h))
        b= h.index(min(h))
        h[a] -= 1
        h[b] += 1
    print(f'#{tc}', max(h)-min(h))
```

최대, 최소의 인덱스를 구한 뒤, 해당 값을 +1, -1을 진행하여,
높은 곳에서 작은 곳으로 값을 이동시켰다. 
그 다음 변경된 h에서 가장 큰 것과 작은 것의 차이를 계산했다.
이 방법의 경우, for문을 돌고 min, max를 반복 사용하여 시간 복잡도가 높았다.
