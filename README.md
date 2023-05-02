2658 Maximum Number of Fish in a Grid

class Solution:
    def findMaxFish(self, grid: List[List[int]]) -> int:
        def dfs(i,j,grid,s):
            q=[[i,j]]
            vis=set()
            vis.add((i,j))
            while(q):
                x,y=q.pop(0)
                s+=grid[x][y]
                print(s)
                for p1,q1 in [[0,1],[0,-1],[1,0],[-1,0]]:
                    t1=x+p1
                    t2=y+q1
                    if t1>=0 and t2>=0 and t1<len(grid) and t2<len(grid[0]) and grid[t1][t2]!=0:
                        if (t1,t2) not in vis:
                            q.append([t1,t2])
                            vis.add((t1,t2))
            return s
        m=0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j]!=0:
                    m=max(m,dfs(i,j,grid,0))
        return m
        
