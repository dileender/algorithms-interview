+ [Two Sum](#two-sum)
+ [3Sum](#3sum)

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

## 3Sum

https://leetcode.com/problems/3sum/

```cpp
 vector<vector<int>> threeSum(vector<int>& nums) {
      int size = nums.size();
      vector<vector<int>> res;
     	if (size < 3)
	      	return res;
     	sort(nums.begin(), nums.end());
     	for (int i = 0; i < size-2; i++)	{
		      int a = nums[i];
	      	if(a > 0) break;
	      	if (i > 0 && nums[i] == nums[i - 1])
		     	continue;
		    for(int j = i + 1, k = size - 1; j < k;){
		     	int b = nums[j];
		     	int c = nums[k];
		     	if(a + b + c == 0) {
				      res.push_back(vector<int>({a,b,c}));
			      	while(j < k && nums[++j] == b) ;
			      	while(j < k && nums[--k] == c) ;
			     }
			     else if(a + b + c > 0){
				      k--;
			     }
		    	 else {
                 j++;
               }
		  }
	}
	return total;
    }
```
