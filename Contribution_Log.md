# Contribution Log – SLE-4

## Project Information

- **Student Name:** Soham Nanaso Patil
- **PRN:** 25UAM124
- **Course:** 02AML204 – Introduction to Artificial Intelligence
- **Division:** B
- **Project:** AI-Based Maze and Route-Finding System

## 1. Project Contribution Summary

My contribution to SLE-4 was to document and justify the default search algorithm using evidence from the earlier stages of the project.

The work connects the BFS and DFS implementation from SLE-1, the empirical profiling from SLE-2, and the C4 system architecture from SLE-3.

## 2. Stage-Wise Contribution

### SLE-1: Algorithm Implementation

- Implemented BFS and DFS route-finding algorithms.
- Worked with graph traversal and route reconstruction.
- Prepared the initial project README and AI contribution documentation.

### SLE-2: Empirical Performance Analysis

- Tested BFS and DFS on graphs containing 5, 10, and 16 nodes.
- Used `time.perf_counter_ns()` to measure execution time.
- Repeated each search 5,000 times.
- Recorded nodes expanded and path length.
- Compared the results to understand the trade-offs between BFS and DFS.

### SLE-3: System Architecture

- Documented the system using the C4 architecture model.
- Identified the main components, including Input, Search Engine, Frontier, Visited Set, Profiler, and Output.
- Identified the Frontier as the component that changes between BFS and DFS.
- Documented how a modular design supports interchangeable search strategies.

### SLE-4: Architecture Decision Record

- Reviewed the profiling results from SLE-2.
- Connected the experimental evidence to the architecture described in SLE-3.
- Compared BFS, DFS, Greedy Best-First Search, and A*.
- Selected BFS as the default algorithm because it guarantees the shortest path in an unweighted graph.
- Documented the benefits, limitations, alternatives, and future extensions of the decision.
- Prepared the final ADR and viva preparation notes.

## 3. Key Experimental Evidence

The 16-node graph produced the following reported results:

| Metric | BFS | DFS |
|---|---:|---:|
| Path length | 4 edges | 14 edges |
| Execution time | 3.657 µs | 4.577 µs |
| Nodes expanded | 16 | 15 |

These results supported the decision to prioritize shortest-path quality rather than selecting an algorithm based only on execution speed.

## 4. AI Tool Contribution

**AI tool used:** Claude (Anthropic)

AI assistance was used for drafting and organizing the ADR wording and documentation based on the existing profiling results and architecture design.

### My Own Work

- BFS and DFS implementation in SLE-1 and SLE-2.
- Performance profiling and collection of the reported measurements.
- C4 architecture work in SLE-3.
- Review of the ADR against the existing code, profiling results, and architecture.

AI was used as a documentation aid; the reported experimental results came from the earlier project work.

## 5. Final Learning Outcomes

- Understood why BFS guarantees a shortest path in an unweighted graph.
- Learned that DFS execution speed depends on graph structure and neighbour order.
- Practiced evidence-based algorithm selection.
- Understood the value of a swappable Frontier component.
- Learned to document architecture decisions and their trade-offs.

## 6. Conclusion

SLE-4 brought together the implementation, profiling, and architecture work from the previous stages. The final decision was to use BFS by default while keeping the Frontier interchangeable so that DFS and future search strategies can remain available.

