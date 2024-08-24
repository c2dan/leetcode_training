
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

```cpp
class Solution {
public:
    int minSubArrayLen(int target, vector<int>& nums) {
        // slide window
        int left = 0;
        int count = 0;
        int length = 99999999;
        for (int right = 0;right<nums.size() ; right++) {
            count+=nums[right];
            while(count >= target) {
                length = length < right - left + 1 ? length: right-left +1;
                count-=nums[left++];
            }
        }
        return length == 99999999 ? 0 : length;
    }
};

```
...not finish yet


## [59.  Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/)

it it not dificult but testing the condideration of edge condition 
```python3
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        cur_col, cur_row = 0, 0
        matrix = [[0] * n for _ in range(n)]
        count = 1

        while n > 0:
            if n > 1:
                # 从左到右
                for i in range(cur_col, cur_col + n - 1):
                    matrix[cur_row][i] = count
                    count += 1

                # 从上到下
                for i in range(cur_row, cur_row + n - 1):
                    matrix[i][cur_col + n - 1] = count
                    count += 1

                # 从右到左
                for i in range(cur_col + n - 1, cur_col, -1):
                    matrix[cur_row + n - 1][i] = count
                    count += 1

                # 从下到上
                for i in range(cur_row + n - 1, cur_row, -1):
                    matrix[i][cur_col] = count
                    count += 1

            # 如果矩阵大小为奇数，填充中心元素
            if n == 1:
                matrix[cur_row][cur_col] = count
            cur_row+=1
            cur_col+=1
            n -= 2

        return matrix
```
