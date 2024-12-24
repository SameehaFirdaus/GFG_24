# GFG_24
---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Arrays
  - Hash
  - Sorting
---

# 🚀 _Day 24. Overlapping Intervals_ 🧠

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/sorting-gfg-160/problem/overlapping-intervals--170633)

## 💡 **Problem Description:**

Given an array of intervals `arr[][]`, where each interval `arr[i] = [starti, endi]` represents a range of integers, merge all overlapping intervals.  

The output should return an array of the merged intervals sorted by their starting points.

## 🔍 **Example Walkthrough:**

**Input:**  
`arr = [[1,3],[2,4],[6,8],[9,10]]`  
**Output:**  
`[[1,4],[6,8],[9,10]]`

**Explanation:**  
- `[1,3]` and `[2,4]` overlap, so they merge into `[1,4]`.  

**Input:**  
`arr = [[6,8],[1,9],[2,4],[4,7]]`  
**Output:**  
`[[1,9]]`

**Explanation:**  
- All intervals overlap with `[1,9]`, so they merge into `[1,9]`.  

### Constraints:

- $`1 ≤ arr.size() ≤ 10^5`$  
- $`0 ≤ starti ≤ endi ≤ 10^5`$  



## 🎯 **My Approach:**

1. **Sorting Intervals**:  
   - The first step is to sort the intervals by their starting points.  
   - This ensures that we can linearly process intervals and merge overlapping ones efficiently.

2. **Merging Logic**:  
   - Maintain a result list and iterate through the sorted intervals.  
   - For each interval:
     - If it overlaps with the last interval in the result, merge them by updating the end point.
     - Otherwise, add the interval to the result as it doesn't overlap with any previous intervals.  

3. **Final Output**:  
   - The resulting intervals are guaranteed to be sorted and non-overlapping.



## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** O(n log n), where `n` is the size of the array. The sorting step dominates the time complexity.  
- **Expected Auxiliary Space Complexity:** O(n), as we use additional space for storing the merged intervals.

## 📝 **Solution Code**
## Code (Python)

```python
class Solution:
    def mergeOverlap(self, intervals):
        if not intervals:
            return []

        intervals.sort(key=lambda x: x[0])
        merged = [intervals[0]]

        for interval in intervals[1:]:
            last = merged[-1]
            if interval[0] <= last[1]:
                last[1] = max(last[1], interval[1])
            else:
                merged.append(interval)

        return merged
```
