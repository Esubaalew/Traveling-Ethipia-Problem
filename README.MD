# Traveling Ethiopia Problem

## Problem Title

Traveling Ethiopia Problem (Simplistic Version)

## Problem Statement

Ethiopia, known for its rich cultural heritage and diverse geography, has numerous cities connected by road networks. The task is to develop an AI agent that plans a tour across Ethiopia, starting from a designated city and visiting other cities based on specific constraints. The agent should implement uninformed search strategies to find paths under different conditions.

## Graph Representation

The cities are represented as nodes, and roads between them are edges. The graph is undirected and may include varying distances (costs).

### Provided Data

- **Cities:**
  ```python
  cities = ['Addis Ababa', 'Bahir Dar', 'Gondar', 'Hawassa', 'Mekelle']
  ```
- **Roads:**
  ```python
  roads = {
      'Addis Ababa': [('Bahir Dar', 510), ('Hawassa', 275)],
      'Bahir Dar': [('Addis Ababa', 510), ('Gondar', 180)],
      'Gondar': [('Bahir Dar', 180), ('Mekelle', 300)],
      'Hawassa': [('Addis Ababa', 275)],
      'Mekelle': [('Gondar', 300)]
  }
  ```

## Objectives

1. **Find a path to a target city using BFS or DFS.**
2. **Find a path visiting all cities exactly once (extended task).**
3. **Visualize the road network and the path found by the agent.**

## Constraints

- The roads may be unweighted (for BFS/DFS) or weighted (for cost-sensitive variations).
- The agent should avoid revisiting a city unless specified otherwise.

## Implementation Details

### Function Specifications

#### Path Finder:

```python
def uninformed_path_finder(cities, roads, start_city, goal_city, strategy):
    """
    Parameters:
    - cities: List of city names.
    - roads: Dictionary with city connections as {city: [(connected_city, distance)]}.
    - start_city: The city to start the journey.
    - goal_city: The destination city (for specific tasks).
    - strategy: The uninformed search strategy to use ('bfs' or 'dfs').

    Returns:
    - path: List of cities representing the path from start_city to goal_city.
    - cost: Total cost (number of steps or distance) of the path.
    """
    pass
```

#### Traverse All Cities (Extended Task):

```python
def traverse_all_cities(cities, roads, start_city, strategy):
    """
    Parameters:
    - cities: List of city names.
    - roads: Dictionary with city connections as {city: [(connected_city, distance)]}.
    - start_city: The city to start the journey.
    - strategy: The uninformed search strategy to use ('bfs' or 'dfs').

    Returns:
    - path: List of cities representing the traversal path.
    - cost: Total cost (distance) of the traversal.
    """
    pass
```

### Example Usage

#### Input:

```python
cities = ['Addis Ababa', 'Bahir Dar', 'Gondar', 'Hawassa', 'Mekelle']
roads = {
    'Addis Ababa': [('Bahir Dar', 510), ('Hawassa', 275)],
    'Bahir Dar': [('Addis Ababa', 510), ('Gondar', 180)],
    'Gondar': [('Bahir Dar', 180), ('Mekelle', 300)],
    'Hawassa': [('Addis Ababa', 275)],
    'Mekelle': [('Gondar', 300)]
}

start_city = 'Addis Ababa'
goal_city = 'Mekelle'
strategy = 'bfs'

path, cost = uninformed_path_finder(cities, roads, start_city, goal_city, strategy)
print(f"Path: {path}, Cost: {cost}")
```

#### Output:

```plaintext
Path: ['Addis Ababa', 'Bahir Dar', 'Gondar', 'Mekelle'], Cost: 990
```

### Advanced Challenges (Bonus)

1. Handle dynamic road conditions (e.g., roads becoming blocked).
2. Add the ability to find the k-shortest paths between two cities.

### Visualization

To visualize the graph:

```python
import networkx as nx
import matplotlib.pyplot as plt

def visualize_graph(roads, path=None):
    G = nx.Graph()
    for city, connections in roads.items():
        for connected_city, distance in connections:
            G.add_edge(city, connected_city, weight=distance)

    pos = nx.spring_layout(G)
    nx.draw(G, pos, with_labels=True, node_size=700, node_color="lightblue")
    labels = nx.get_edge_attributes(G, 'weight')
    nx.draw_networkx_edge_labels(G, pos, edge_labels=labels)

    if path:
        path_edges = list(zip(path, path[1:]))
        nx.draw_networkx_edges(G, pos, edgelist=path_edges, edge_color="red", width=2)

    plt.show()

# Example Visualization
visualize_graph(roads, path=['Addis Ababa', 'Bahir Dar', 'Gondar', 'Mekelle'])
```

### Example Visualization Output

A graph where nodes represent cities and edges represent roads. The path is highlighted in red.

---

## Getting Started

1. Clone this repository.
2. Install required Python libraries (e.g., NetworkX, Matplotlib).
   ```bash
   pip install networkx matplotlib
   ```
3. Run the provided examples to test the path-finding algorithms.

## License

This project is open-source and available under the MIT License.
