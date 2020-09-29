给你一个 m x n 的矩阵，其中的值均为非负整数，代表二维高度图每个单元的高度，请计算图中形状最多能接多少体积的雨水。

 

示例：

给出如下 3x6 的高度图:
[
  [1,4,3,1,3,2],
  [3,2,1,3,2,4],
  [2,3,3,2,3,1]
]

返回 4 。

```java
class Solution {

    private static final int[][] step={{0,1},{0,-1},{1,0},{-1,0}}; 

    public int trapRainWater(int[][] heightMap) {
        int n=heightMap.length,m=heightMap[0].length;
        boolean[][] visited=new boolean[n][m];
        Queue<Node> pq=new PriorityQueue<>((n+m)<<2,(a,b) -> a.h-b.h);
        for(int i=0;i<n;++i){
            visited[i][0]=visited[i][m-1]=true;
            pq.offer(new Node(i,0,heightMap[i][0]));
            pq.offer(new Node(i,m-1,heightMap[i][m-1]));
        }
        for(int i=0;i<m;++i){
            visited[0][i]=visited[n-1][i]=true;
            pq.offer(new Node(0,i,heightMap[0][i]));
            pq.offer(new Node(n-1,i,heightMap[n-1][i]));
        }
        int result=0;
        while(!pq.isEmpty()){
            Node node=pq.poll();
            for(int[] s:step){
                int i=node.x+s[0],j=node.y+s[1];
                if(i>=0 && i<n && j>=0 && j<m && !visited[i][j]){
                    if(heightMap[i][j]<node.h){
                        result+=node.h-heightMap[i][j];
                        pq.offer(new Node(i,j,node.h));
                    }else{
                        pq.offer(new Node(i,j,heightMap[i][j]));
                    }
                    visited[i][j]=true;
                }
            }
        }
        return result;
    }

    private class Node{
        int x,y,h;

        Node(int x,int y,int h){
            this.x=x;
            this.y=y;
            this.h=h;
        }
    }
}
```
