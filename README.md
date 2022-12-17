# Leetcode-Problems
#### 94. Binary Tree Inorder Traversal

Given the root of a binary tree, return the inorder traversal of its nodes' values.\
Example 1:\
![image](https://user-images.githubusercontent.com/59637279/208133879-e55de709-b40d-4a66-bf61-760217720090.png)

Input: root = [1,null,2,3]
Output: [1,3,2] \
Example 2:

Input: root = []
Output: [] \
Example 3:

Input: root = [1]
Output: [1]
 

Constraints:

The number of nodes in the tree is in the range [0, 100].
-100 <= Node.val <= 100

```
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var inorderTraversal = function(root) {
   if(!root) {
       return [];
   }
   const left_values = inorderTraversal(root.left);
   const right_values = inorderTraversal(root.right);

   return[...left_values,root.val,...right_values];
};
```
#### 724. Find Pivot Index
Given an array of integers nums, calculate the pivot index of this array.

The pivot index is the index where the sum of all the numbers strictly to the left of the index is equal to the sum of all the numbers strictly to the index's right.

If the index is on the left edge of the array, then the left sum is 0 because there are no elements to the left. This also applies to the right edge of the array.

Return the leftmost pivot index. If no such index exists, return -1.

Example 1:
```
Input: nums = [1,7,3,6,5,6]
Output: 3
Explanation:
The pivot index is 3.
Left sum = nums[0] + nums[1] + nums[2] = 1 + 7 + 3 = 11
Right sum = nums[4] + nums[5] = 5 + 6 = 11
```
Example 2:
```
Input: nums = [1,2,3]
Output: -1
Explanation:
There is no index that satisfies the conditions in the problem statement.
```
Example 3:
```
Input: nums = [2,1,-1]
Output: 0
Explanation:
The pivot index is 0.
Left sum = 0 (no elements to the left of index 0)
Right sum = nums[1] + nums[2] = 1 + -1 = 0
```
##### Solution
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var pivotIndex = function(nums) {
    let sum = nums.reduce((prev,current)=>prev +current,0);
    let leftSum=0;
    for(let i=0;i<nums.length;i++)
    {
        if(sum-nums[i]==(2*leftSum)){
            return i;
        }
        else{
            leftSum +=nums[i];
        }
    }
    return -1;
};
```
