# text
#include <cstdio>
using namespace std;
 
    int array[9][9];
    bool isIn(int n,int x,int y,int m){
        for(int i=0;i<m;i++){
            if(array[x][i]==n||array[i][y]==n)
                return false;
        }
        if(m==9) {
            for (int i = (x / 3) * 3; i < (x / 3 + 1) * 3; i++) {
                for (int j = (y / 3) * 3; j < (y / 3 + 1) * 3; j++) {
                    if (array[i][j] == n)
                        return false;
                }
            }
        }
        if (m==4){
            for (int i = (x / 2) * 2; i < (x / 2 + 1) * 2; i++) {
                for (int j = (y / 2) * 2; j < (y / 2 + 1) * 2; j++) {
                    if (array[i][j] == n)
                        return false;
                }
            }
        }
        if(m==6) {
            for (int i = (x / 2) * 2; i < (x / 2 + 1) * 2; i++) {
                for (int j = (y / 3) * 3; j < (y / 3 + 1) * 3; j++) {
                    if (array[i][j] == n)
                        return false;
                }
            }
        }
        if(m==8) {
            for (int i = (x / 4) * 4; i < (x / 4 + 1) * 4; i++) {
                for (int j = (y / 2) * 2; j < (y / 2 + 1) * 2; j++) {
                    if (array[i][j] == n)
                        return false;
                }
            }
        }
        return true;
    }

    bool dfs(int x,int m){
        int i,j;
        i = x/m;j = x%m;
        if(x==m*m){
            return true;
        }
        if(array[i][j]!=0) return dfs(x+1,m);
        for(int n=1;n<=m;n++){
            if(isIn(n,i,j,m)){
                array[i][j] = n;
                if(dfs(x+1,m)) return true;
                array[i][j] = 0;
            }
        }
        return false;
    }
    int main(){
		int m = 6;//指定宫数
    	for(int i=0; i<m; i++)
        	for(int j=0; j<m; j++)
            	scanf("%d",&array[i][j]);
    	dfs(0,m);
    	for(int i=0; i<m; i++){
        	for(int j=0; j<m; j++)
            	printf("%d ",array[i][j]);
        	printf("\n");
    	}
    	return 0;
    }
