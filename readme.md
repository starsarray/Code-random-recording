[toc]

***

# 数组

### 数组理论基础

- **数组是存放在连续内存空间上的相同类型数据的集合**

- **数组的元素是不能删的，只能覆盖**

- 在C++中二维数组是连续分布的

- Java是没有指针的，二维数组可能是第一个维度连续

### 二分查找

使用前提：**有序数组**中**无重复元素**

- 时间复杂度：O(log n)
- 空间复杂度：O(1)

1.[left,right]左闭右闭

```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1  # 定义target在左闭右闭的区间里，[left, right]
		while left<=right:
            middle = (left+right)//2
            if nums[middle]>=target:right = middle-1 # 相等右指针则会向左平移，保证索引最小
            else:left = middle+1
        return left  # 返回应插入的最小索引
```

2.[left,right)左闭右开

```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums)  # 定义target在左闭右开的区间里，即：[left, right)
        while left < right:  # 因为left == right的时候，在[left, right)是无效的空间，所以使用 <
            middle = (left+right)//2
            if nums[middle]>=target:right = middle # 相等右指针则会向左平移，保证索引最小
            else:left = middle+1
        return left  # 或者 right 返回该插入的最小索引
```

3.(left,right)左开右开

```py
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        left, right = -1, len(nums)  # 定义target在左闭右开的区间里，即：[left, right)
        while left+1 < right: 
            middle = (left+right)//2
            if nums[middle]>=target:right = middle # 相等右指针则会向左平移，保证索引最小
            else:left = middle
        return right  # 返回该插入的最小索引
```

4.库函数写法

```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        return bisect_left(nums, target)
```

***

### 移除元素

### 有序数组的平方

### 长度最小的子数组

