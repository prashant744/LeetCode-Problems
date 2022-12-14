class Solution {
public:
    int rob(vector<int>& nums) {
        vector<int> d(nums.size());
        for (int i = 0; i < nums.size(); ++i)
            d[i] = nums[i] + max(i - 2 >= 0 ? d[i - 2] : 0, i - 3 >= 0 ? d[i - 3] : 0);
        return max(d.size() >= 1 ? d.rbegin()[0] : 0, d.size() >= 2 ? d.rbegin()[1] : 0);
    }
};