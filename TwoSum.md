## Two Sum Problem:
Given an array of integers, return indices of the two numbers such that they add up to a specific target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
>    Given nums = [2, 7, 11, 15], target = 9,
>    Because nums[0] + nums[1] = 2 + 7 = 9,
>    return [0, 1].

## Python Solution
```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        # if the value does not exist, Store the element in this map 
        mapOfPrevElements = {} # element : index
        # iterate over the indices of the nums list from zero to length  of the list
        for i in range(0, len(nums)):
                # find the difference between target and the number
                difference = target - nums[i]
                # Check if the difference is present in the map of previously add elements
                if difference in mapOfPrevElements:
                    # if it does, get it's index (or value) and the index of the current element (i)
                    print("The difference",difference,"with element",nums[i],"and target",target,"is in the list at position" , mapOfPrevElements.get(difference))
                    return [mapOfPrevElements.get(difference), i]
                else:
                    # else, add the element and it's index to the map
                    print(nums[i] , " key is added to index(value)", i)
                    mapOfPrevElements[nums[i]] = i
```

## Java Solution
```java
class Solution {
    public int[] twoSum(int[] nums, int target) { //we're given a list of int, and and int target
        Map<Integer, Integer> mapOfPreviousElements = new HashMap<>(); // creating int:int hashmap to add the element and it's index
        
        for (int i = 0; i < nums.length; i++) { // loop over the length of list from 0 stored in i  
            int difference = target - nums[i]; // find difference between target and the current element
            
            if (mapOfPreviousElements.containsKey(difference)) { //if the difference is present in the mapOfPreviousElements
                return new int[]{ mapOfPreviousElements.get(difference), i }; // return the index of the difference element in the map(which is a value) and index of current element
            }
            mapOfPreviousElements.put(nums[i], i); // else put the current element in map with element as key and it's index as value
        }
        return new int[0]; // Since the condition says exactly one solution, this return will never be reached 
    }
}
```