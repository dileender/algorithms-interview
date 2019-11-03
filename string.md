+ [Valid Palindrome](#valid-palindrome)
+ [Valid Parentheses](#valid-parentheses)
+ [Group Anagrams](#group-anagrams)
+ [Palindromic Substrings](#palindromic-substrings)
+ [Reverse String](#reverse-string)

## Valid Palindrome

https://leetcode.com/problems/valid-palindrome/

```cpp
bool isAlphaNumeric(char c)
{
    return (c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z') || (c >= '0' && c <= '9');
}

int toLower(char c)
{
    return c >= 'A' && c <= 'Z' ? c + ('a' - 'A') : c;
}

bool isPalindrome(string s)
{
    int i = 0;
    int j = s.length() - 1;
    while (i < j) {
        if (!isAlphaNumeric(s[i])) {
            i++;
        }
        else if (!isAlphaNumeric(s[j])) {
            j--;
        }
        else if (toLower(s[i]) != toLower(s[j])) {
            return false;
        }
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
bool isValid(string s)
{
    unordered_map<char, char> parentheses = { { '(', ')' }, { '[', ']' }, { '{', '}' } };
    stack<char> st;
    for (char c : s) {
        if (parentheses.find(c) != parentheses.end()) {
            st.push(parentheses[c]);
        }
        else {
            if (st.empty() || c != st.top()) {
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
vector<vector<string> > groupAnagrams(vector<string>& strs)
{
    vector<vector<string> > res;
    unordered_map<string, vector<string> > s;

    for (string word : strs) {
        string main = word;
        sort(main.begin(), main.end());
        s[main].push_back(word);
    }

    for (const auto i : s) {
        vector<string> temp;
        for (string j : i.second)
            temp.push_back(j);
        res.push_back(temp);
    }
    return res;
}
```

## Palindromic Substrings

https://leetcode.com/problems/palindromic-substrings/

```cpp
int countSubstrings(string s)
{
    int n = s.size();
    int res = 0;
    for (int i = 0; i < n; i++) {
        palindromic(s, i, i, res);
        palindromic(s, i, i + 1, res);
    }
    return res;
}

void palindromic(string s, int left, int right, int& res)
{
    while (left >= 0 && right < s.size() && s[left] == s[right]) {
        res++;
        left--;
        right++;
    }
}
```

## Reverse String

https://leetcode.com/problems/reverse-string/

```cpp
void reverseString(vector<char>& s)
{
    int i = 0;
    int j = s.size() - 1;
    while (i < j) {
        char tmp = s[i];
        s[i] = s[j];
        s[j] = tmp;
        i++;
        j--;
    }
}
```
