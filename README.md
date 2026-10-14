# SLE-4: Final Viva & Architecture Decision Record (ADR)

## Project Information

- **Course:** 02AML204 – Introduction to Artificial Intelligence
- **PRN:** 25UAM124
- **Student Name:** Soham Nanaso Patil
- **Division:** B
- **Project:** AI-Based Maze and Route-Finding System
- **Repository:** [SLE_4](https://github.com/SohamP27/SLE_4)

## 1. Project Overview

This project focuses on developing and analyzing an AI-based route-finding system using Breadth-First Search (BFS) and Depth-First Search (DFS).

The project progresses through three stages:

- **SLE-1:** Implementation of BFS and DFS route-finding algorithms.
- **SLE-2:** Empirical performance analysis of BFS and DFS on graphs containing 5, 10, and 16 nodes.
- **SLE-3:** System architecture documentation using the C4 model.
- **SLE-4:** Preparation of an Architecture Decision Record (ADR) based on implementation, profiling results, and architecture design.

## 2. Objectives

- Implement BFS and DFS for finding routes in graphs.
- Compare the algorithms using execution time, nodes expanded, and path length.
- Select a suitable default search algorithm based on experimental evidence.
- Design a modular search system with a swappable Frontier component.
- Document the architectural decision and its trade-offs.

## 3. Algorithms Used

### Breadth-First Search (BFS)

BFS explores nodes level by level using a queue. For an unweighted graph, it guarantees a shortest path in terms of the number of edges.

**Advantages:**
- Guarantees the shortest path in an unweighted graph.
- Produces predictable results.
- Suitable for unweighted route-finding problems.

**Limitation:**
- May require more memory because it stores nodes in a queue.

### Depth-First Search (DFS)

DFS explores one branch as deeply as possible before backtracking. It uses a stack or recursive traversal.

**Advantages:**
- Can reach a goal quickly on some graphs.
- May use less memory in certain search spaces.

**Limitations:**
- Does not guarantee the shortest path.
- Performance depends on graph structure and neighbour order.

## 4. SLE-2 Performance Analysis

BFS and DFS were tested on graphs containing 5, 10, and 16 nodes. Execution time was measured using `time.perf_counter_ns()`, and a node counter was used to record search activity. Each search was repeated 5,000 times.

An important result from the 16-node graph was:

| Metric | BFS | DFS |
|---|---:|---:|
| Path length | 4 edges | 14 edges |
| Execution time | 3.657 µs | 4.577 µs |
| Nodes expanded | 16 | 15 |

The measurements show that DFS was not consistently faster. It was faster on the 10-node graph but slower on the 16-node graph.

BFS produced a significantly shorter route on the 16-node graph, making it the preferred default for this unweighted route-finding system.

*Note: Execution times are the reported profiling results and may vary across machines and runs.*

## 5. Architecture Overview

The system follows a modular design based on the C4 architecture documented in SLE-3.

The main components are:

- **Input:** Receives the graph, start node, and goal node.
- **Search Engine:** Executes BFS or DFS.
- **Frontier:** Stores nodes waiting to be explored; implemented as a queue for BFS and a stack for DFS.
- **Visited Set:** Tracks visited nodes to avoid repeated exploration.
- **Profiler:** Measures execution time and nodes expanded.
- **Output:** Reports the discovered route and performance information.

The Frontier is swappable, allowing the system to switch between BFS and DFS without redesigning the other major components.

## 6. Architecture Decision Record (ADR)

**Decision:** Use BFS as the default route-finding algorithm while keeping the Frontier component interchangeable.

**Status:** Accepted  
**Date:** 11 October 2026

### Alternatives Considered

1. **DFS:** May be faster in some cases but does not guarantee the shortest path.
2. **Greedy Best-First Search:** Requires heuristic information that is not available in the tested graphs.
3. **A\* Search:** Could be considered in a future extension, but the current unweighted graphs do not provide useful heuristic information.

### Consequences

**Positive:**
- Guarantees shortest paths for unweighted graphs.
- Provides predictable route quality.
- Preserves flexibility to use DFS or add another search strategy.

**Trade-offs:**
- BFS may consume more memory on wide graphs.
- DFS can be faster for certain graph structures.
- If edges have different costs, a cost-aware algorithm such as Dijkstra's algorithm may be more appropriate.

## 7. Complexity Analysis

For graph traversal using adjacency lists:

- **BFS Time Complexity:** O(V + E)
- **DFS Time Complexity:** O(V + E)

Here, `V` represents the number of vertices and `E` represents the number of edges.

BFS queue memory can grow with the width of the search frontier, while DFS generally stores the current traversal path and pending branches.

## 8. Tools and Technologies

- Python
- Breadth-First Search (BFS)
- Depth-First Search (DFS)
- `time.perf_counter_ns()` for performance measurement
- Git and GitHub
- C4 architecture model
- AI-assisted documentation using Claude

## 9. Learning Outcomes

Through this project, I learned:

- How BFS and DFS explore graphs differently.
- How to compare algorithms using experimental measurements.
- Why execution speed alone is not enough to select an algorithm.
- How modular architecture makes components interchangeable.
- How to document design choices, alternatives, and trade-offs using an ADR.

## 10. Future Scope

- Extend the system to larger graphs and maze environments.
- Add Dijkstra's algorithm for graphs with different edge costs.
- Introduce A* with an appropriate heuristic when the problem provides useful information.
- Improve performance visualization and automated benchmarking.

## 11. Conclusion

The project demonstrates that algorithm selection should consider solution quality, execution time, memory usage, and system requirements. Based on the reported profiling results and the need for shortest routes in unweighted graphs, BFS was selected as the default algorithm. Keeping the Frontier interchangeable preserves the modularity of the system and allows future extensions.

## 12. References

- SLE-1 implementation and documentation
- SLE-2 Profiling Report, 23 September 2026
- SLE-3 C4 Architecture, 7 October 2026
- SLE-4 Architecture Decision Record, 11 October 2026
- [GitHub Repository](https://github.com/SohamP27/SLE_4)
