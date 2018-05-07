旋转数组
 

Rotate an array of n elements to the right by k steps.

For example, with n = 7 and k = 3, the array [1,2,3,4,5,6,7] is rotated to [5,6,7,1,2,3,4].

Note:
Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.

[show hint]

Hint:
Could you do it in-place with O(1) extra space?
Credits:
Special thanks to @Freezen for adding this problem and creating all test cases.

 

新题抢先刷，这道题标为Easy，应该不是很难，我们先来看一种O(n)的空间复杂度的方法，我们复制一个和nums一样的数组，然后利用映射关系i -> (i+k)%n来交换数字。代码如下：

 

解法一：


class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        vector<int> t = nums;
        for (int i = 0; i < nums.size(); ++i) {
            nums[(i + k) % nums.size()] = t[i];
        }
    }
};

 

由于提示中要求我们空间复杂度为O(1)，所以我们不能用辅助数组，上面的思想还是可以使用的，但是写法就复杂的多，而且需要用到很多的辅助变量，我们用题目中的例子来展示下面这种算法的nums的变化过程：

1 2 3 4 5 6 7 
1 2 3 1 5 6 7
1 2 3 1 5 6 4
1 2 7 1 5 6 4
1 2 7 1 5 3 4
1 6 7 1 5 3 4
1 6 7 1 2 3 4
5 6 7 1 2 3 4

 

解法二：

复制代码
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        if (nums.empty() || (k %= nums.size()) == 0) return;
        int n = nums.size(), start = 0, i = 0, cur = nums[i], cnt = 0;
        while (cnt++ < n) {
            i = (i + k) % n;
            int t = nums[i];
            nums[i] = cur;
            if (i == start) {
                ++start; ++i;
                cur = nums[i];
            } else {
                cur = t;
            }
        }
    }
};

 

这道题其实还有种类似翻转字符的方法，思路是先把前n-k个数字翻转一下，再把后k个数字翻转一下，最后再把整个数组翻转一下：

1 2 3 4 5 6 7 
4 3 2 1 5 6 7 
4 3 2 1 7 6 5
5 6 7 1 2 3 4

 

解法三：


class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        if (nums.empty() || (k %= nums.size()) == 0) return;
        int n = nums.size();
        reverse(nums.begin(), nums.begin() + n - k);
        reverse(nums.begin() + n - k, nums.end());
        reverse(nums.begin(), nums.end());
    }
};
