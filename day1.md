resources

```python
print{"iloveu"}
```
# 704. Binary Search

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
```
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
