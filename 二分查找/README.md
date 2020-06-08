二分查找主体模板
===

```
        int left = 0, right = nums.length - 1;
        
        while (left <= right) {
            int mid = left + ((right - left) >> 1);
            
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
```
