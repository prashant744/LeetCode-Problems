class Solution {
public:
	int minimumAverageDifference(vector<int>& nums) {
		long long  n = nums.size(),sum = 0,total = accumulate(begin(nums),end(nums),0l);
		long long maxi = LLONG_MAX,res = 0;
		for(long long i = 0;i<n-1;i++){
			sum+=nums[i];
			long long curr = abs(sum/(i+1) - (total-sum)/(n-i-1));
			if(curr<maxi) maxi = curr,res = i;
		}

		return maxi>total/n ? n-1:res;
	}
};