

## 1. Two Sum

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& a, int x) {
        unordered_map<int, int> ids; // indexs
        int n = a.size();
        vector<int> ans {-1, -1};
        for (int i = 0; i < n; i++) {
            if (ids.count(x - a[i])) {
                ans = {ids[x - a[i]], i};
            }
            ids[a[i]] = i;
        }
        return ans;
    }
};
```


## 3. Longest Substring Without Repeating Characters

```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int n = s.size();
        int ans = 0;
        unordered_map<char, int> cnt;
        for (int i = 0, j = 0; i < n; i++) {
            cnt[s[i] - 'a']++;
            while (cnt[s[i] - 'a'] > 1) {
                cnt[s[j++] - 'a']--;
            }
            ans = max(ans, i - j + 1);
        }
        return ans;
    }
};
```