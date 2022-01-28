# HackerRank Python collections
Solutions for HackerRank Python collections module

## Company Logo in Python

A newly opened multinational brand has decided to base their company logo on the three most common characters in the company name. They are now trying out various combinations of company names and logos based on this condition. Given a string , which is the company name in lowercase letters, your task is to find the top three most common characters in the string.

Print the three most common characters along with their occurrence count.
Sort in descending order of occurrence count.
If the occurrence count is the same, sort the characters in alphabetical order.
For example, according to the conditions described above, would have it's logo with the letters .

### Input Format

A single line of input containing the string .

### Output Format

Print the three most common characters along with their occurrence count each on a separate line.
Sort output in descending order of occurrence count.
If the occurrence count is the same, sort the characters in alphabetical order.

### Sample Input 0
```python
aabbbccde
```
### Sample Output 0
```python
b 3
a 2
c 2
```
### Explanation 0
aabbbccde

Here, b occurs  times. It is printed first.
Both a and c occur  times. So, a is printed in the second line and c in the third line because a comes before c in the alphabet.

### Note: The string  has at least  distinct characters.

### Solution

```python

#!/bin/python3

import math
import os
import random
import re
import sys
from collections import Counter


if __name__ == '__main__':
    s = sorted(input().strip())
    logo = Counter(s).most_common(3)
    for character, count in logo:
        print(character, count)
    
```

## Piling Up! in Python

There is a horizontal row of  cubes. The length of each cube is given. You need to create a new vertical pile of cubes. The new pile should follow these directions: if ***cube[i]*** is on top of ***cube[j]*** then ***sideLength[j] >= sideLength[i]***. When stacking the cubes, you can only pick up either the leftmost or the rightmost cube each time. Print Yes if it is possible to stack the cubes. Otherwise, print No.

### Input Format

The first line contains a single integer , the number of test cases.
For each test case, there are  lines.
The first line of each test case contains , the number of cubes.
The second line contains  space separated integers, denoting the sideLengths of each cube in that order.

### Output Format

For each test case, output a single line containing either Yes or No.

### Sample Input
``` python
STDIN        Function
-----        --------
2            T = 2
6            blocks[] size n = 6
4 3 2 1 3 4  blocks = [4, 3, 2, 1, 3, 4]
3            blocks[] size n = 3
1 3 2        blocks = [1, 3, 2]
```

### Sample Output
``` python
Yes
No
```
### Solution
```  python
from collections import deque

t = int(input())
for _ in range(t):
    n = int(input())
    blocks = deque(map(int, input().split()))
    flag = True
    
    if blocks[0] >= blocks[-1]:
        cube = blocks.popleft()
    else:
        cube = blocks.pop()
    while blocks:
        if len(blocks) == 1:
            if blocks[0] <= cube:
                cube = blocks.pop()
                break
            else:
                flag = False
                break
        else:
            if cube >= blocks[0] and cube >= blocks[-1]:
                if blocks[0] <= blocks[-1]:
                    cube = blocks.pop()
                else:
                    cube = blocks.popleft()
            else:
                flag = False
                break

    if flag :
        print('Yes')
    else: 
        print('No')
```

