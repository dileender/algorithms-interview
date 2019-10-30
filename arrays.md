+ [Two Sum](#two-sum)

## Two Sum

https://leetcode.com/problems/two-sum/

```cpp
 vector<int> twoSum(vector<int> & nums, int target) {
    unordered_map<int, int> hash_table;
        
    for (int i = 0; i < nums.size(); ++i){
        int res = target - nums[i];
        if (hash_table.find(res) != hash_table.end())
        return vector<int> { 
            hash_table[target - nums[i]], i }; 
          hash_table.insert(pair<int, int>(nums[i], i));
         }
     return vector<int>();    
    }
```
