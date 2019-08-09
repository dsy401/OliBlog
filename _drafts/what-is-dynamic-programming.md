---
layout: post_layout
title: What is dynamic programming
date: 2019-06-12 06:12:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

### What is dynamic programming?

Dynamic programming is a branch of operations research and a mathematical method to optimize the decision process. Transforming the multi-stage process into a series of single-stage problems, using the relationship between the stages, solving one by one, created a new method to solve such process optimization problems - dynamic programming.

Using dynamic planning features:

1. Find the optimal solution to a problem.

2. Big problems can be broken down into sub-problems, sub-questions and overlapping sub-problems.

3. The optimal solution of the overall problem depends on the optimal solution of the subproblem (state transition equation).

4. Analyze the problem from top to bottom and solve the problem from the bottom up.

5. Discuss the underlying boundary problem.

The most important three concepts of dynamic programming are: 1. Optimal substructure 2. Boundary 3. State transition equation.

### <br>Walking the stairs Problem

There are ten steps, going from top to bottom, only one or two steps at a time. How many ways to go?

1. Optimal Substructure: Let's consider the final step to the tenth step. The final step must go to the eighth or ninth. It is not difficult to get f(10) = f(9)+f(8). f(9) = f(8)+f(7)
2. Boundary: f(1) = 1, f(2) = 2
3. State transition: f(n) = f(n-1) + f(n-2)

Solution 1:

```python
def get_count(n):
    if n == 1:return 1
    if n == 2:return 2
    else:
        return get_count(n-1)+get_count(n-2)
print(get_count(10))
```
the code is easy and useful

Obviously this is a full binary tree with a height of N-1. Therefore, the total number of nodes is 2^N-1, and the time complexity is O(2^N). It’s horrible to watch.

```python
def get_count(n):
    if n == 1:return 1
    elif n == 2 :return 2
    else:
        l = [1,2]
        for i in range(3,n):
            l[0],l[1] = l[1],l[0]+l[1]
        return l[0]+l[1]
```
