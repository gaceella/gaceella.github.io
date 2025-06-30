
+++
date = '2025-06-29'
title = 'Dijkstra's Algorithm'
+++

# Dijkstra's Algorithm

> “Dijkstra’s algorithm turns networks into maps — and complexity into clarity”

## What is Dijkstra's Algorithm?

**Definition:**  
Dijkstra's Algorithm is a method used to find the shortest path from one point or node (called a source) to all other points in a graph.  
We can understand this with a simple example: suppose you want to go from your home to your friend's house, and there are many roads and intersections. Dijkstra’s Algorithm helps you find the quickest route (shortest distance or time).

## Why Do We Use This Algorithm?

We use this algorithm when we need to know the shortest or most efficient path between two things like locations on a map, computers in a network, or steps in a process.

It is useful when:
- There are many paths for selection, and we want the best one.
- When we think about the time, cost, and efficiency.

### Advantages of Dijkstra’s Algorithm
- **Efficient:** Finds the shortest path fast and effectively.
- **Reliable:** Always gives the correct shortest path.
- **Works for all kinds of graphs having positive values.**
- **Simple to understand and apply on positive-weight graphs.**
- **Great for roads, networks, maps, etc.**

### Disadvantages of Dijkstra’s Algorithm
1. **No Negative Weights:**  
   Dijkstra’s Algorithm can’t handle negative distances.

2. **Slow on Large Graphs:**  
   Without optimizations, it may take too long to find the shortest path in big graphs.

3. **High Memory Usage:**  
   It needs to store all distances and paths, which can consume a lot of memory.

4. **No Path Reuse:**  
   Even if the graph hasn’t changed, it doesn’t remember previous results.

## Real-Life Applications of Dijkstra’s Algorithm
1. **Navigation Systems (e.g., Google Maps):**  
   To find the shortest route from your location to a destination.

2. **Computer Networks:**  
   To find the best path for data between servers or devices.

3. **Artificial Intelligence in Games:**  
   For characters to move in the shortest path across a game map.

4. **Robotics:**  
   For planning the most efficient movement through a space.

5. **Social Media:**  
   Finding the shortest connection between two users.

---

## Example: Simple Python Code

```python
import heapq  

def dijkstra(graph, start):  
    distances = {node: float('inf') for node in graph} 
    distances[start] = 0  
    queue = [(0, start)]

    while queue:  
        current_distance, current_node = heapq.heappop(queue)   

        if current_distance > distances[current_node]:  
            continue

        for neighbor, weight in graph[current_node]:  
            distance = current_distance + weight   

            if distance < distances[neighbor]:     
                distances[neighbor] = distance    
                heapq.heappush(queue, (distance, neighbor))    

    return distances

graph = {
    'A': [('B', 1), ('C', 4)],  
    'B': [('A', 1), ('C', 2), ('D', 5)], 
    'C': [('A', 4), ('B', 2), ('D', 1)], 
    'D': [('B', 5), ('C', 1)]  
}

print(dijkstra(graph, 'A'))
```

### Code Explanation

```python
import heapq  

def dijkstra(graph, start):  
    distances = {node: float('inf') for node in graph} 
    distances[start] = 0  
    queue = [(0, start)]
```

The `heapq` module creates a priority queue. The `dijkstra` function starts with infinite distances except the start node, which is 0.

```python
    while queue:  
        current_distance, current_node = heapq.heappop(queue)   

        if current_distance > distances[current_node]:  
            continue

        for neighbor, weight in graph[current_node]:  
            distance = current_distance + weight   

            if distance < distances[neighbor]:     
                distances[neighbor] = distance    
                heapq.heappush(queue, (distance, neighbor))    

    return distances
```

The loop continues while there are nodes in the queue. It finds and updates the shortest paths.

```python
graph = {
    'A': [('B', 1), ('C', 4)],  
    'B': [('A', 1), ('C', 2), ('D', 5)], 
    'C': [('A', 4), ('B', 2), ('D', 1)], 
    'D': [('B', 5), ('C', 1)]  
}

print(dijkstra(graph, 'A'))
```

### Graph Details:

- Node 'A': neighbors 'B' (1), 'C' (4)
- Node 'B': neighbors 'A' (1), 'C' (2), 'D' (5)
- Node 'C': neighbors 'A' (4), 'B' (2), 'D' (1)
- Node 'D': neighbors 'B' (5), 'C' (1)

---

## Important Terms in Dijkstra’s Algorithm

- **Node (Vertex):** A point in the graph.
- **Edge:** A connection between two nodes.
- **Weight (Cost):** Value representing distance, time, or cost.
- **Graph:** A collection of nodes and edges.
- **Start Node (Source):** Starting point of path-finding.
- **Visited Node:** Node with finalized shortest path.
- **Priority Queue (Min-Heap):** Queue that always gives the next shortest node.
- **Shortest Path:** The path with the minimum total weight.

---

This blog explained how Dijkstra’s algorithm works, key terms, and real-world use cases — from GPS to AI pathfinding.

**THANK YOU!**
