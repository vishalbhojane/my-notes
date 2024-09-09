[920](https://www.lintcode.com/problem/920/)

Given an array of meeting time intervals consisting of start and end times `[(s1,e1),(s2,e2),...] (si < ei)`, determine if a person could attend all meetings.

**Example 1**

```
Input: intervals = [(0,30),(5,10),(15,20)]
Output: false
Explanation: 
(0,30), (5,10) and (0,30),(15,20) will conflict
```

**Example 2**

```
Input: intervals = [(5,8),(9,15)]
Output: true
Explanation: 
Two times will not conflict 
```

```js
function canAttendMeetings(intervals){
  intervals.sort((a,b) => a[0] - b[0])
  
  for(let i = 0; i < intervals.length - 1; i++){
    // end time of current meeting and start time of next meeting
    if(intervals[i][1] > intervals[i+1][0]){
      return false
    }
  }
  return true
}
```