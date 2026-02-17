# Grid-Based Blind Search Algorithms Visualization

A comprehensive implementation of six fundamental uninformed search algorithms with real-time visualization in a grid-based environment.

## Overview

This project implements and visualizes six classic blind search strategies:

- **Breadth-First Search (BFS)**
- **Depth-First Search (DFS)**
- **Uniform Cost Search (UCS)**
- **Depth-Limited Search (DLS)**
- **Iterative Deepening DFS (IDDFS)**
- **Bidirectional Search**

Each algorithm is implemented with step-by-step visualization showing the exploration process, frontier nodes, visited nodes, and final path in a customizable grid world with obstacles.

## Features

- **Real-time Visualization**: Watch algorithms explore the grid step-by-step
- **Animated Search Process**: See frontier expansion and node visitation in real-time
- **Performance Metrics**: Compare path length, cost, and nodes explored
- **Customizable Grid**: Configure grid size, obstacles, start, and target positions
- **Diagonal Movement**: Support for both orthogonal and diagonal moves
- **Cost Analysis**: Track and compare search costs across algorithms
- **Side-by-side Comparison**: Visual comparison of all algorithms

## Prerequisites

- Python 3.7 or higher
- Jupyter Notebook or JupyterLab

## Installation

### Step 1: Clone the Repository

```bash
git clone https://github.com/yourusername/grid-search-algorithms.git
cd grid-search-algorithms
```

### Step 2: Create Virtual Environment (Recommended)

```bash
# On Windows
python -m venv venv
venv\Scripts\activate

# On macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install numpy matplotlib jupyter
```

Or install from requirements file:

```bash
pip install -r requirements.txt
```

### Step 4: Launch Jupyter Notebook

```bash
jupyter notebook
```

Then open `AI_A1_Grid_Based.ipynb` in your browser.

## Dependencies

Create a `requirements.txt` file with:

```
numpy>=1.21.0
matplotlib>=3.4.0
jupyter>=1.0.0
ipython>=7.26.0
```

##  Usage

### Basic Usage

1. **Import and Initialize**:

```python
# The notebook automatically creates a default 8x8 grid
grid_world = GridWorld(rows=8, cols=8)
```

2. **Run Individual Algorithms**:

```python
# Breadth-First Search
bfs_path, bfs_cost, bfs_nodes = bfs_search(grid_world, animate=True)

# Depth-First Search
dfs_path, dfs_cost, dfs_nodes = dfs_search(grid_world, animate=True)

# Uniform Cost Search
ucs_path, ucs_cost, ucs_nodes = ucs_search(grid_world, animate=True)

# Depth-Limited Search (limit=10)
dls_path, dls_cost, dls_nodes = dls_search(grid_world, depth_limit=10, animate=True)

# Iterative Deepening DFS
iddfs_path, iddfs_cost, iddfs_nodes = iddfs_search(grid_world, animate=True)

# Bidirectional Search
bidir_path, bidir_cost, bidir_nodes = bidirectional_search(grid_world, animate=True)
```

3. **Compare All Algorithms**:
   The notebook includes a comparison section that runs all algorithms and displays results side-by-side.

### Custom Grid Configuration

```python
# Create custom grid
custom_grid = GridWorld(rows=20, cols=20)

# Change start and target positions
custom_grid.start = (2, 2)
custom_grid.target = (17, 17)

# Reset and add custom walls
custom_grid.reset_grid()

# Add walls (create obstacles)
for i in range(5, 15):
    custom_grid.grid[i, 8] = custom_grid.WALL

# Update start and target on grid
custom_grid.grid[custom_grid.start[0], custom_grid.start[1]] = custom_grid.START
custom_grid.grid[custom_grid.target[0], custom_grid.target[1]] = custom_grid.TARGET

# Visualize
custom_grid.visualize("My Custom Grid")
```

### Understanding the Visualization

The visualization uses color coding:

- **Green**: Start position
- **Red**: Target position
- **Black**: Walls/Obstacles
- **Orange**: Frontier (nodes to be explored)
- **Light Blue**: Visited nodes
- **Yellow**: Final path
- **White**: Empty/Unexplored cells

## Grid Configuration

The default grid is 8×8 with predefined obstacles that create an interesting pathfinding challenge:

```
Start: (1, 1)
Target: (6, 6)
```

The grid includes vertical and horizontal walls that force algorithms to find alternative routes.

## Algorithm Comparison

| Algorithm     | Completeness | Optimality | Time Complexity  | Space Complexity |
| ------------- | ------------ | ---------- | ---------------- | ---------------- |
| BFS           | Yes          | Yes\*      | O(b^d)           | O(b^d)           |
| DFS           | No\*\*       | No         | O(b^m)           | O(bm)            |
| UCS           | Yes          | Yes        | O(b^(1+⌊C\*/ε⌋)) | O(b^(1+⌊C\*/ε⌋)) |
| DLS           | No           | No         | O(b^l)           | O(bl)            |
| IDDFS         | Yes          | Yes\*      | O(b^d)           | O(bd)            |
| Bidirectional | Yes          | Yes\*      | O(b^(d/2))       | O(b^(d/2))       |

\* When all step costs are equal  
\*\* In infinite spaces or with cycles

Where:

- b = branching factor
- d = depth of shallowest solution
- m = maximum depth
- l = depth limit
- C\* = cost of optimal solution
- ε = minimum step cost

## Running the Full Notebook

Execute all cells in order:

1. **Setup and Imports**: Initializes required libraries
2. **Grid World Class**: Defines the environment
3. **Search Algorithms**: Implements all six algorithms
4. **Run All Algorithms**: Executes and compares all methods
5. **Comparison Visualization**: Side-by-side results
6. **Custom Grid** (optional): Create your own configurations

## Code Structure

```
grid-search-algorithms/
├── AI_A1_Grid_Based.ipynb    # Main Jupyter notebook
├── README.md                  # This file
├── requirements.txt           # Python dependencies
└── report.md                  # Detailed technical report
```

##  Features Breakdown

### GridWorld Class

- Grid initialization with configurable size
- Obstacle/wall placement
- Neighbor generation (including diagonal moves)
- Cost calculation (1.0 for orthogonal, 1.414 for diagonal)
- Visualization with multiple display modes

### Search Algorithms

Each algorithm includes:

- Complete implementation following textbook pseudocode
- Real-time visualization capability
- Performance metrics tracking
- Path reconstruction
- Step-by-step animation

## Troubleshooting

### Common Issues

1. **Matplotlib not displaying**:

   ```python
   %matplotlib inline  # Add this at the top of notebook
   ```

2. **Animation not working**:
   - Ensure you're running in Jupyter Notebook (not JupyterLab in some cases)
   - Try reducing animation speed

3. **Import errors**:

   ```bash
   pip install --upgrade numpy matplotlib jupyter
   ```

4. **Grid not visible**:
   - Check figure size parameters
   - Ensure cell output is not collapsed

## Contributing

Contributions are welcome! Feel free to:

- Add new search algorithms
- Improve visualization
- Optimize performance
- Add new grid configurations
- Enhance documentation

## License

This project is available for educational purposes. Feel free to use and modify for learning and teaching.

##  Authors

- Hussain Ashraf
- Naina Awan

## Acknowledgments

- Based on AI search algorithms from "Artificial Intelligence: A Modern Approach" by Russell & Norvig
- Visualization inspired by pathfinding algorithm demonstrations
- Grid-based environment design following classic AI problem representations

## Additional Resources

- [AI Search Algorithms Explained](https://en.wikipedia.org/wiki/Search_algorithm)
- [Pathfinding Visualizations](https://qiao.github.io/PathFinding.js/visual/)
- [Python Matplotlib Documentation](https://matplotlib.org/)

## Contact

For questions or suggestions, please open an issue on GitHub.

---

**Note**: This implementation is designed for educational purposes to understand the behavior and characteristics of different uninformed search strategies. For production pathfinding, consider using A\* or other informed search algorithms.
