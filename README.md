# path-the-minimum-effort
Path With Minimum Effort is a grid pathfinding problem where we need to move from the top-left cell to the bottom-right cell. The effort of a path is the maximum height difference between consecutive cells. The goal is to find the path with the minimum possible effort.
# Path With Minimum Effort

## LeetCode 1631

### Problem

Find a path from the top-left corner of a height grid to the bottom-right corner where the **maximum height difference between consecutive cells is minimized**.

### Approach

The grid can be treated as a graph:

* Each cell is a node.
* Adjacent cells are connected by edges.
* The edge weight is the absolute difference between their heights.

We use a **modified Dijkstra's algorithm**.

Instead of adding edge weights like normal Dijkstra:

```text
newDistance = currentDistance + edgeWeight
```

we calculate:

```text
newEffort = max(currentEffort, edgeWeight)
```

A min-priority queue is used to always process the cell with the smallest current effort.

### Algorithm

1. Start from `(0,0)` with effort `0`.
2. Store the minimum effort required to reach every cell.
3. Take the cell with the smallest effort from the priority queue.
4. Check its four neighboring cells.
5. Calculate the height difference.
6. Calculate the new effort using the maximum of the current effort and height difference.
7. Update the neighbor if the new effort is smaller.
8. Continue until the destination is reached.
9. Return the minimum effort.

### Example

**Input:**

```text
[[1,2,2],
 [3,8,2],
 [5,3,5]]
```

**Output:**

```text
2
```

One optimal path is:

```text
1 → 3 → 5 → 3 → 5
```

The maximum height difference is `2`.

### Complexity

**Time Complexity:**

```text
O(R × C × log(R × C))
```

**Space Complexity:**

```text
O(R × C)
```

where `R` is the number of rows and `C` is the number of columns.

### Technologies

* C++
* Dijkstra's Algorithm
* Priority Queue
* Graph
* Matrix/Grid

### Key Learning

This problem demonstrates how Dijkstra's algorithm can be modified for a **minimum-bottleneck path**, where we minimize the largest edge cost rather than the sum of all edge costs.
