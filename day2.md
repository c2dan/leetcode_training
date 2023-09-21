
# day2 | 977. Squares of a Sorted Array,

## [977.  Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)
This array is ascending and  some part of it may smaller than 0. we can use 2 pointer to comparing the sqaure of the negative number and the square of the positive number. 

```python3

class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        left = 0
        right = len(nums) - 1
        result = [0] * len(nums)  # 创建一个与原数组相同长度的结果数组

        while left <= right:
            square_left = nums[left] * nums[left]
            square_right = nums[right] * nums[right]

            if square_left > square_right:
                result[right - left] = square_left  # 存储平方值在结果数组中
                left += 1
            else:
                result[right - left] = square_right  # 存储平方值在结果数组中
                right -= 1

        return result
```
I tried to change the nums itself, but it cant work
```python3
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        left = 0
        right = len(nums) - 1
        while left <= right:
            square_left = nums[left] * nums[left]
            square_right = nums[right] * nums[right]
            if (square_left) > (square_right):
                nums[left] = nums[right]
                nums[right] = square_left
                right-=1
            else:
                nums[right] = square_right
                right-=1
        return nums
 ```
 this function cant work on [-5,-3,-2,-1], cause it will change the ascending order when switch some of them.


 ## [209.  Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)

this is an advance problem
 
...not finish yet


## [59.  Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/)

not dificult but test the edge condition
