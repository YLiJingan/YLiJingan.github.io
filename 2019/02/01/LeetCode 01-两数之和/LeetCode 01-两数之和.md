---
title: LeetCode 01
comments: true
tags: ['js基础','LeetCode']
---
## LeetCode 01-两数之和
### Description
给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你***不能重复利用这个数组中同样的元素***   

> 示例:        
给定 nums = [2, 7, 11, 15], target = 9    
因为 nums[0] + nums[1] = 2 + 7 = 9    
所以返回 [0, 1]

### Solution    
```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
```
#### 方法一

``` javascript
var twoSum = function(nums, target) {
    var len = nums.length;
    for(let i=0;i<len;i++){
        for(let j=i+1;j<len;j++){
            if(nums[i] + nums[j] === target){
                return [i, j];
            }
        }
    }
};
twoSum([2,7,11,15],9);
```

#### 方法二
```javascript
var twoSum = function(nums, target) {
    var len = nums.length;
    for(let i=0;i<len;i++){
        let num = target - nums[i];
        for(let j=i+1;j<len;j++){
            if(nums[j] === num){
                return [i, j];
            }
        }
    }
};
twoSum([2,7,11,15],9);
```

#### 方法三
***hash map***

```javascript
var twoSum = function(nums, target) {
    let len = nums.length;
    let hashObj = {};
    nums.forEach((ele, index) => { hashObj[ele] = index });
    for(let i=0; i<len;i++){
      let indexObj = hashObj[target-nums[i]]; 
      if(indexObj && indexObj !==i){
          return [i, indexObj];
      }
    }
    
};
twoSum([2,7,11,15],9);
```

#### 方法四
***new Map()***

```javascript
var twoSum = (nums, target) => {
    let map = new Map();
    let res = [];
    nums.forEach((e, i) => map.set(e, i));
    for(let i=0;i<nums.length;i++) {
        let j = map.get(target - nums[i]);
        if(j && j!==i) {
            res = [i,j];
            break;
        }
    }

    return res;
};
twoSum([2,7,11,15],9);
```
