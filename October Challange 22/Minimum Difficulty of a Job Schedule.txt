class Solution {
public:
    int dp[305][12];
    int minSum(vector<int>&a, int d ,int i,int n){
        if(d==0){
            if(i==n)  return 0;
            else return 1e9;
        }
        if(i==n)  return 1e9;
        if(dp[i][d]!=-1)  return dp[i][d];
        int ans=1e9;
        //Get the maximum element from the segment 
        int ma=a[i];
        for(int j=i;j<n;j++){
            ma=max(ma,a[j]);
            ans=min(ans,minSum(a,d-1,j+1,n)+ma);
        }
        return dp[i][d]=ans;
    }
    int minDifficulty(vector<int>&a, int d) {
        int n=a.size();
        memset(dp,-1,sizeof dp);
        int ans=minSum(a,d,0,n);
        return ans==1e9?-1:ans;
        
    }
};