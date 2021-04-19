# Robot Bounded In Circle

> - Difficulty: Medium
> - Type: Logic
> - [link](https://leetcode.com/problems/robot-bounded-in-circle/submissions/)

## Solution

- Key concept: to result in a limit circle, the cordinate should have returned to the initial start point (0,0) or must have changed direction after 1 cycle of instructions.

```python
class Solution:
    def isRobotBounded(self, instructions: str) -> bool:
        direction = ["N","E","S","W"]
        action =[[0,1],[1,0],[0,-1],[-1,0]]
        # Function to determine next cordinate and direction
        def get_cord_dir(cur_cord,cur_dir,instruct):
            i = direction.index(cur_dir)
            if instruct == "R":
                i = (i+1)%len(direction)
            elif instruct == "L":
                i -= 1
            elif instruct == "G":
                cur_cord[0] += action[i][0]
                cur_cord[1] += action[i][1]
            cur_dir = direction[i]
            return cur_cord,cur_dir

        instructions = list(instructions)
        cur_cord = [0,0]
        cur_dir = "N"

        # Run 1 cycle of instructions
        for inst in instructions:
            cur_cord,cur_dir = get_cord_dir(cur_cord,cur_dir,inst)

        # If the cordinate is back at [0,0] or direction is not at north after 1 cycle,
        # Repeating the instruction would result in a circle
        return cur_cord == [0,0] or cur_dir != "N"


```
