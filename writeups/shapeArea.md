# shapeArea
Found on CodeSignal.

### Description
Below we will define an n-interesting polygon. Your task is to find the area of a polygon for a given n.

A 1-interesting polygon is just a square with a side of length 1. An n-interesting polygon is obtained by taking the n - 1-interesting polygon and appending 1-interesting polygons to its rim, side by side. You can see the 1-, 2-, 3- and 4-interesting polygons in the picture below.
![](/assets/area.png)

Example

    For n = 2, the output should be
    solution(n) = 5;
    For n = 3, the output should be
    solution(n) = 13.

Input/Output

    [execution time limit] 4 seconds (py3)

    [input] integer n

    Guaranteed constraints:
    1 ≤ n < 104.

    [output] integer

    The area of the n-interesting polygon.

### Solution
The solution is some function ƒ. If you count the areas for the first few values of n, you notice that the area is changing at a rate of 4x, thus making the derivative of the function `f'(x) = 4*x + c`
```
ƒ(1) = 1
ƒ(2) = 5
ƒ(3) = 13
ƒ(4) = 25

ƒ'(x) = 4*x + c
```

ƒ is found by taking the integral of that function.
```
∫ 4x+c dx = 2x**2 - c*x + c'
```
Now I just need to find the values of `c` and `c'` where the function is true.
```
ƒ(1) =  1 = 2*(1)**2 - c*(1) + c' =  2 - c*(1) + c'
ƒ(2) =  5 = 2*(2)**2 - c*(2) + c' =  4 - c*(1) + c'
ƒ(3) = 13 = 2*(3)**2 - c*(3) + c' =  9 - c*(1) + c'
ƒ(4) = 25 = 2*(4)**2 - c*(4) + c' = 16 - c*(1) + c'
```
I found that the answer was for `c = 2` and `c' = 1`

```Python
def solution(n):
    return 2*n**2 - 2*n + 1
```