class Solution {
public:
    int maxLength(vector<string>& arr) {
        vector<bitset<26>> bits; 
        for (auto s : arr) {
            bitset<26> a;
            for (char c : s) a.set(c - 'a');
            if (a.count() == s.size()) bits.push_back(a);
        }
        return maxLength(bits, bitset<26>(), 0);
    }
    
    int maxLength(vector<bitset<26>>& bits, bitset<26> bs, int index) {
        int res = bs.count();
        for (int i = index; i < bits.size(); i++) 
            if (!(bits[i] & bs).any()) res = max(res, maxLength(bits, bs | bits[i], i+1));
        
        return res;
    }
};