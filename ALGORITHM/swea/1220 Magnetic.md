### 풀이
```
for tc in range(1, 11):
    n = int(input()) # 왜 주는 거임,,,?
    table = [list(map(int, input().split())) for _ in range(100)]

    cnt = 0

    # 세로로 읽기
    for nums in zip(*table):
        chk = 0
        for num in nums:
            if num == 1:
                chk = 1
            elif num == 2 and chk == 1:
                cnt += 1
                chk = 0
    print(f'#{tc} {cnt}')
```

우선 zip을 사용하여 세로로 값을 읽어온 뒤, 
교착 상태를 확인하기 위해서 chk로 1 뒤에 2가 오는 건지 확인함
1이 나온 뒤 2가 나오는 경우 cnt를 1개 올려준 뒤 교착 상태 확인 부분을 초기화함
