/*
	11、盛最多水的容器
*/


/*双指针：定义头尾指针，各自向中间移动*/
class Solution {
    public int maxArea(int[] height) {

        int maxArea = 0;
        int l = 0;
        int r = height.length - 1;
        
        while (l < r) {
            maxArea = Math.max(maxArea, Math.min(height[l], height[r]) * (r - l));
            if (height[l] < height[r]) {
                l++;
            } else {
                r--;
            }
        }

        return maxArea;
    }
}