+ [Valid Palindrome](#valid-palindrome)
+ [Valid Parentheses](#valid-parentheses)
+ [Group Anagrams](#group-anagrams)

## Valid Palindrome

https://leetcode.com/problems/valid-palindrome/

```cpp
private: bool isAlphaNumeric(char c) {
    return (c >= 'a' && c <= 'z') ||
            (c >= 'A' && c <= 'Z') ||
            (c >= '0' && c <= '9');
}

private:int toLower(char c) {
    return c >= 'A' && c <= 'Z' ? c + ('a' - 'A') : c;
}

public:bool isPalindrome(string s) {
    int i = 0;
    int j = s.length() - 1;
    while (i < j) {
        if (!isAlphaNumeric(s[i])) {
            i++;}
        else if (!isAlphaNumeric(s[j])){
            j--;}
        else if (toLower(s[i]) != toLower(s[j])) {
            return false;}
        else {
            i++;
            j--;
        }
    }
    return true;
}
```

## Valid Parentheses

https://leetcode.com/problems/valid-parentheses/

```cpp
 bool isValid(string s) {
        unordered_map<char, char> parentheses = {{'(',')'},{'[',']'},{'{','}'}};
        stack<char> st;
        for (char c : s){
            if (parentheses.find(c) != parentheses.end()){
                st.push(parentheses[c]);
            }
            else{
                if(st.empty() || c != st.top()){
                    return false;
                }
                st.pop();
            }
        }
        return st.empty();
    } 
```

## Group Anagrams

https://leetcode.com/problems/group-anagrams/

```cpp
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<vector<string>> res;
        unordered_map<string, vector<string>> s;
        
        for(string word : strs)
        {
            string main = word;
            sort(main.begin(), main.end());
            s[main].push_back(word);
        }
        
        for(const auto i : s)
        {
            vector<string> temp;
            for(string j : i.second)
                temp.push_back(j);
            res.push_back(temp);
        }
        return res;  
    }
```
