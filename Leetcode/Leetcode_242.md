# Valid Anagram

> - Difficulty: Easy
> - Type: Sorting
> - [link](https://leetcode.com/problems/valid-anagram/)

## Solution

- Sort two words and check if they are equal
- Time complexity: O(n log n)

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if sorted(s) == sorted(t):
            return True
        else:
            return False
```

- Count every occurence of alphabets of two words and see if the counts are equal
- Time complexity: O(n)

```python
import collections
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if collections.Counter(s) == collections.Counter(t):
            return True
        else:
            return False
```
