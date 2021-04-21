# Meeting Rooms II

> - Difficulty: Medium
> - Type: Heap/Priority Que
> - [link](https://leetcode.com/problems/meeting-rooms-ii/)

## Solution

- Data structure: min heap
- Algorithm: priority que
- Sort the array first in ascending start time
- Save the end time in the min heap
  - Rational: whenever the new meeting start time is greater than the minimum end time of the past, a room can be reused to host the new meeting
- Compare meeting start times with the minimum value in the min heap
- Pop from min heap when start time is greater than the minimum end time in the heap

```python
import heapq
class Solution:
    def minMeetingRooms(self, intervals: List[List[int]]) -> int:
        # Sort the array in ascending start time
        intervals.sort(key=lambda x: (x[0],x[1])) # nlogn
        rooms = []
        for meeting in intervals: # n
            if not rooms:
                heapq.heappush(rooms,meeting[1]) # log n
            # Compare minimum end time with new meeting's start time
            elif rooms[0] <= meeting[0]:
                heapq.heappop(rooms) # log n
                heapq.heappush(rooms,meeting[1]) # log n
            else:
                heapq.heappush(rooms,meeting[1]) # log n

        return len(rooms)
```
