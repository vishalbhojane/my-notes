Create a function `canAttendMeetings` that takes an array of meeting intervals and returns a boolean indicating whether a person can attend all meetings. The function should:
1. Handle arrays of any length, including empty arrays.
2. Work with non-negative integers representing start and end times.
3. Return true if all meetings can be attended, false otherwise.
4. Consider an empty array of meetings as attendable (return true).

## Solution

```javascript
function canAttendMeetings(intervals) {
    if (intervals.length <= 1) return true;

    intervals.sort((a, b) => a[0] - b[0]);

    for (let i = 0; i < intervals.length - 1; i++) {
        if (intervals[i][1] > intervals[i+1][0]) {
            return false;
        }
    }

    return true;
}
```

Core Logic:
1. Sort the intervals based on start time.
2. Iterate through the sorted intervals.
3. If the end time of the current meeting is greater than the start time of the next meeting, there's a conflict.
4. If no conflicts are found, all meetings can be attended.

```javascript
console.log(canAttendMeetings([[0,30],[5,10],[15,20]])); // false
console.log(canAttendMeetings([[5,8],[9,15]])); // true
console.log(canAttendMeetings([[1,2],[2,3],[3,4]])); // true
console.log(canAttendMeetings([[1,5],[5,8]])); // true
console.log(canAttendMeetings([[10,12],[12,14],[14,16]])); // true
console.log(canAttendMeetings([[1,5],[2,3]])); // false
console.log(canAttendMeetings([])); // true
console.log(canAttendMeetings([[1,2]])); // true
```

## Complexity

Time Complexity: O(n log n), where n is the number of intervals. This is due to the sorting operation, which dominates the time complexity. The subsequent linear scan is O(n).

Space Complexity: O(1) if we're allowed to modify the input array, or O(n) if we need to create a copy of the array for sorting. The space used for sorting depends on the implementation of the sort method, but typically it's O(log n) to O(n).

