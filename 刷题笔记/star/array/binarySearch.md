// TODO
# 考虑二分法

```text
Given an array of integers nums which is sorted in ascending order, and an integer target, 
write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.  
```

```C
int search(int* nums, int numsSize, int target){

}
```
we have nums[] and size of array
eg:nums = [-1,0,3,5,9,12],size = 6, target = 9.  
pick up nums with 2 parts,part1 and part2
each part has its own left and right boarders.

if target is bigger than the right board of part1  
  choose the part2 and apart part2 with 2 parts again
  
which means ...
```C
int search(int* nums, int numsSize, int target){

  int part2leftIndex = numsSize/2;
  int part1rightIndex = part2leftIndex - 1;
  //part 1 index -> 0 ~ numsSize/2-1
  //part 2 index -> numsSize/2 ~ numsSize-1

  if(target > part1rightIndex){
     numsSize = numsSize-1 - numsSize/2;
     part2leftIndex = part1rightIndex + numsSize/2;
     part1rightIndex = part2leftIndex - 1;
     
  }else if(target < part1rightIndex){
    //apart part1 into 2 parts
    numsSize = numsSize/2;
     part2leftIndex = part1rightIndex - numsSize/2;
     part1rightIndex = part2leftIndex - 1;
     
  }else{
    return part1rightIndex;
  }
  return -1;

}
```
