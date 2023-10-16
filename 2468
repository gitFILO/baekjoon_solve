n = int(input())
# 2차원 배열을 생성하고 초기화
matrix = []
dx = [0,0,-1,1]
dy = [1,-1,0,0] # 상하좌우

for i in range(n):
    row = list(map(int, input().split()))
    matrix.append(row)


flooded = []
for i in range(n):
    row = [False] * n
    flooded.append(row)


cur_rain = 0

sanctuary = 0

while True:
    cur_rain += 1 # 비가 온다 -> 높이 1 올라감
    all_flooded = True
    # 물이 차고 난 뒤에 flooded 를 갱신한다
    for i in range(n):
        for j in range(n):
            if matrix[i][j] <= cur_rain: #물에 잠김
                flooded[i][j] = True
            else: # 물에 안잠긴 곳이 존재
                all_flooded = False
    if all_flooded: #만약 모두 물에 잠긴 상태라면, 더이상 할 이유 없음
        break # while문 종료
    if cur_rain == 100: # 아무 곳도 물에 잠기지 않음 -> 즉, 안식처는 딱 1개
        sanctuary = 1
        break



    # sanctuary 갱신하기
    visited = []
    cur_sanctuary = 0
    for i in range(n):
        row = [False] * n
        visited.append(row)

    q= []
    for i in range(n):
        for j in range(n):
            if (not flooded[i][j]) and (not visited[i][j]): # 만약 물에 잠기지 않았고, 방문한 적도 없다면 -> 새로운 안식처
                cur_sanctuary += 1
                visited[i][j] = True  # 방금 방문함
                q.append([i,j])
                while q:
                    cur_x,cur_y = q.pop()
                    visited[cur_x][cur_y] = True # 방금 방문함
                    for j in range(4): #상하좌우
                        if (0 <= cur_x + dx[j] < n and 0 <= cur_y + dy[j] < n) and (not visited[cur_x+dx[j]][cur_y+dy[j]]) and (not flooded[cur_x+dx[j]][cur_y+dy[j]]):
                            #만약 방문하지 않은 곳이면서 물에 잠기지 않은 곳이 있다면
                            q.append([cur_x+dx[j], cur_y+dy[j]])

    if cur_sanctuary >= sanctuary:
        sanctuary= cur_sanctuary

if sanctuary == 0:
    sanctuary = 1
print(sanctuary)


