# Car Fleet

> - Difficulty: Medium
> - Type: Sorting
> - [link](https://leetcode.com/problems/car-fleet/)

## Solution

- Sort cars by position
- Calculate time needed for each car to arrive at the target
- Starting from the car closest to the target(lead), check if its arrival time is earlier than the one following it
- If lead car arrival time is earier than the one following it, no car will ever catch up to the lead car and it will therefore form a fleet of its own
- If not, it could form a fleet when the cars behind it catches up. Pass the lead car's arrival time to the times list to see if it every gets caught up

```python
class Solution:
    def carFleet(self, target: int, position: List[int], speed: List[int]) -> int:
        cars = sorted(zip(position,speed))
        times = [(target-p)/s for p,s in cars]
        fleet = 0

        while len(times) > 1:
            lead = times.pop()
            if lead < times[-1]:
                fleet += 1
            else:
                times[-1] = lead
        return fleet + len(times)
```
