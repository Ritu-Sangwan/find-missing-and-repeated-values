# find-missing-and-repeated-values
You are given a 0-indexed 2D integer matrix grid of size n * n with values in the range [1, n2]. Each integer appears exactly once except a which appears twice and b which is missing. The task is to find the repeating and missing numbers a and b.  Return a 0-indexed integer array ans of size 2 where ans[0] equals to a and ans[1] equals to b.   

Example:
Input: grid = [[9,1,7],[8,9,2],[3,4,6]]
Output: [9,5]
Explanation: Number 9 is repeated and number 5 is missing so the answer is [9,5].
 

SOLUTION -->


class Solution {
public:
    vector<int> findMissingAndRepeatedValues(vector<vector<int>>& grid) {
        
        unordered_set<int>s;
        vector<int>ans;
        int a ,b;
        int n = grid.size();
        int expectsum =0 ,actualsum=0;
        for(int i =0;i<n;i++){
            for(int j =0;j<n;j++){
               actualsum+=grid[i][j];
                if(s.find(grid[i][j])!=s.end()){
                     a=grid[i][j];
                    ans.push_back(a);
                }
                s.insert(grid[i][j]);
            }
        }
        expectsum = (n*n)*(n*n+1)/2;
        b = expectsum +a-actualsum;
        ans.push_back(b);
        return ans;
    }
};
