704. 二分查找
https://leetcode.cn/problems/binary-search/description/
给定一个 n 个元素有序的（升序）整型数组 nums 和一个目标值 target  ，写一个函数搜索 nums 中的 target，如果目标值存在返回下标，否则返回 -1。
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int n;
        n = nums.size();
        size_t begin = 0,end = n-1;
    while(end - begin >= 0){
        if (target < nums[begin] || target > nums[end])
            return -1;
        if (target == nums[begin])
            return begin;
        if (target == nums[end])
            return end;
        if (target == nums[(begin+end)/2])
            return (begin+end)/2;
        if (target < nums[(begin+end)/2]){
            end = (begin+end)/2+1;
            begin += 1;
        }
        if (target > nums[(begin+end)/2]){
            begin = (begin+end)/2+1;
            end -= 1;
        }
    }
    return -1;
    }
};

27. 移除元素
给你一个数组 nums 和一个值 val，你需要 原地 移除所有数值等于 val 的元素，并返回移除后数组的新长度。

不要使用额外的数组空间，你必须仅使用 O(1) 额外空间并 原地 修改输入数组。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
    int len = 0,i = 0;
    if (nums.size() != 0){
        for(int *p = &nums[0] + nums.size()-1,*q = &nums[0]+nums.size()-1;
            p - q < nums.size() -i; q--){
            if(*q == val){
                *q = *p;
                *p = 0;
                p--;
                i++;
            }
            cout << i;
            len = p - q + 1;
        }
    }
    return len;
    }
};
