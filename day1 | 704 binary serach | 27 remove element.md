#day1 | 704 binary serach | 27 remove element.md

```python
print{"iloveu"}
```
# 704. [Binary Search](https://leetcode.com/problems/binary-search/submissions/)

This problem is finding a number in a list that is in ascending order. In my opinion, the best way to do is using binary search.

```python3

class Solution:
    def search(self, nums: List[int], target: int) -> int:
        length = len(nums)
        middle = -1
        left = 0
        right = length - 1
        while right >= left:
            middle = (left + right) // 2
            if nums[middle] < target:
                left = middle + 1
            elif nums[middle] > target:
                right = middle - 1
            else: 
                return middle
        return -1
```
update
[solution from bilibili](https://www.bilibili.com/video/BV1fA4y1o715/?vd_source=1116eeca3dc2f3ea8dc1046e123a33cd)

```python3
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left,right = 0, len(nums) - 1
        while right >= left:
            middle = (left + right) // 2
            if nums[middle] < target:
                left = middle + 1
            elif nums[middle] > target:
                right = middle - 1
            else: 
                return middle
        return -1
```
review:**unique and ordered is the key point**

# 27.  [Remove Element](https://leetcode.com/problems/remove-element/)

This problem requires removing a specific value from the list and updating the list in place. It doesn't concern itself with the length of the list. Initially, I think we can employ two pointers – a fast pointer to search for unmatched numbers and replace them in the space of the slow pointer.
solution:
```python3
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        fp = 0 #fast pointer
        sp = 0 #slow pointer
        length = len(nums)
        while fp < length:
            if nums[fp] != val:
                nums[sp] = nums[fp]
                sp+=1
            fp+=1
        return sp
```

[solution from bilibil](https://www.bilibili.com/video/BV12A4y1Z7LP/?spm_id_from=333.788&vd_source=1116eeca3dc2f3ea8dc1046e123a33cd)
reveiw: I have tried to use slow pointer to search but it cant cause we can make sure fast pointer can give a correct number.
