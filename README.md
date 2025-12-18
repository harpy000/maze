# Maze Pathfinding with A* Algorithm
## Interactive Web-Based Implementation

A comprehensive web-based implementation of the A* pathfinding algorithm for solving maze navigation problems with real-time interactive visualization and performance analysis.

---

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Getting Started](#getting-started)
4. [How to Use](#how-to-use)
5. [Algorithm Explanation](#algorithm-explanation)
6. [Understanding Results](#understanding-results)
7. [Performance Metrics](#performance-metrics)
8. [Configuration Options](#configuration-options)
9. [Visual Legend](#visual-legend)
10. [Technical Details](#technical-details)
11. [Examples and Test Cases](#examples-and-test-cases)
12. [Troubleshooting](#troubleshooting)
13. [For Academic Use](#for-academic-use)
14. [Browser Support](#browser-support)

---

## Overview

This project implements the A* (A-star) pathfinding algorithm as an interactive web application. It demonstrates intelligent maze navigation through real-time visualization, allowing users to generate random mazes, watch the algorithm solve them, and analyze performance metrics.

**Technology Stack:**
- HTML5 for structure
- CSS3 for styling
- JavaScript (ES6+) for logic and interactivity
- HTML5 Canvas for visualization

**Key Highlights:**
- Single-file implementation (no dependencies)
- Works offline in any modern browser
- Real-time visual feedback
- Configurable maze difficulty
- Comprehensive performance analysis
- Exportable results

---

## Features

### Core Functionality

**A* Algorithm Implementation**
- Complete pathfinding with priority queue
- Manhattan distance heuristic
- Guaranteed optimal solutions
- Efficient node exploration

**Interactive Maze Generation**
- Three size options: 10x10, 20x20, 30x30
- Adjustable obstacle density: 20%, 30%, 40%
- Random generation with guaranteed solvability checks
- Configurable start and goal positions

**Real-Time Visualization**
- HTML5 Canvas rendering
- Color-coded path and exploration
- Clear visual distinction between elements
- Dynamic cell sizing based on maze dimensions

**Performance Analysis**
- Path length measurement
- Node exploration counting
- Execution time tracking
- Efficiency ratio calculation

**Data Export**
- Download complete results
- Text file format for documentation
- Includes ASCII representation
- Ready for report integration

### Visualization Features

**Graphical Display:**
- Black squares: Walls (impassable obstacles)
- White squares: Open paths (walkable cells)
- Green square: Start position
- Red square: Goal position
- Yellow squares: Solution path (optimal route)
- Light blue squares: Explored nodes (examined but not on path)

**Text Output:**
- ASCII maze representation
- Character-based visualization
- Copy-paste ready for reports
- Terminal-style display

---

## Getting Started

### Prerequisites

**Required:**
- Modern web browser (Chrome, Firefox, Safari, or Edge)
- No installation needed
- No internet connection required after initial load

**Recommended:**
- Screen resolution 1024x768 or higher
- JavaScript enabled
- Pop-ups allowed (for file download)

### Installation

**Step 1: Get the File**

Save the HTML file as `astar_maze.html` or any name you prefer.

**Step 2: Open the File**

Method 1: Double-click the HTML file
Method 2: Right-click and select "Open with" then choose your browser
Method 3: Drag and drop the file into an open browser window

**Step 3: Start Using**

The application loads immediately with a default maze ready to solve.

---

## How to Use

### Basic Workflow

**1. Configure Maze Settings**

Select your desired maze parameters:
- Maze Size: Choose from Easy (10x10), Medium (20x20), or Hard (30x30)
- Obstacle Density: Choose Low (20%), Medium (30%), or High (40%)

**2. Generate Maze**

Click "Generate New Maze" button to create a random maze with your settings.

The maze automatically:
- Places random obstacles based on density
- Sets start position (top-left area)
- Sets goal position (bottom-right area)
- Ensures start and goal are not blocked

**3. Run Algorithm**

Click "Run A* Algorithm" button to execute the pathfinding.

The algorithm:
- Explores the maze intelligently
- Finds the shortest path
- Updates visualization in real-time
- Displays performance metrics

**4. View Results**

Check the results panel for:
- Path Found status (Yes/No)
- Path Length (number of steps)
- Nodes Explored (cells examined)
- Time Taken (execution duration)
- Efficiency Ratio (search effectiveness)

**5. Download Results (Optional)**

Click "Download Results" to save:
- Complete configuration details
- All performance metrics
- ASCII maze representation
- Text file format for easy documentation

### Quick Start Example

1. Open `astar_maze.html` in your browser
2. Click "Run A* Algorithm" (uses default 20x20 maze)
3. Observe the yellow path connecting green start to red goal
4. Check the statistics in the results panel
5. Click "Download Results" if you need to save the data

---

## Algorithm Explanation

### What is A*?

A* (pronounced "A-star") is an informed search algorithm that finds the shortest path between two points. It combines the benefits of:
- Dijkstra's algorithm (guarantees shortest path)
- Greedy Best-First Search (uses heuristic for speed)

### The Algorithm Formula

```
f(n) = g(n) + h(n)

Where:
  f(n) = Total estimated cost from start to goal through node n
  g(n) = Actual cost from start to current node n
  h(n) = Estimated cost from node n to goal (heuristic)
```

### How It Works

**Step 1: Initialize**
- Place start node in open set
- Set g-score of start to 0
- Calculate f-score for start using heuristic

**Step 2: Main Loop**
- Select node with lowest f-score from open set
- If this node is the goal, path is found
- Otherwise, mark node as explored (closed set)
- Examine all neighbors

**Step 3: Neighbor Processing**
- For each walkable neighbor:
- Calculate tentative g-score (current g-score + 1)
- If this is better than previous g-score:
  - Update parent pointer
  - Update g-score and f-score
  - Add to open set

**Step 4: Termination**
- If goal reached: reconstruct path by following parent pointers
- If open set empty: no path exists

### Manhattan Distance Heuristic

The heuristic function estimates distance from current position to goal:

```javascript
h(current, goal) = |current.x - goal.x| + |current.y - goal.y|
```

**Why Manhattan Distance?**
- Admissible: Never overestimates actual cost
- Consistent: Satisfies triangle inequality
- Perfect for 4-directional grid movement
- Simple and computationally efficient

**Example:**
If current position is (5, 3) and goal is (8, 7):
```
h = |5 - 8| + |3 - 7| = 3 + 4 = 7
```
This means the minimum possible distance is 7 steps.

### Why A* is Intelligent

**Compared to Uninformed Search:**
- BFS explores equally in all directions (slow)
- DFS may find suboptimal paths (not optimal)
- A* explores toward the goal first (fast and optimal)

**Key Advantages:**
- Guaranteed to find shortest path
- Explores fewer nodes than BFS
- Uses memory efficiently
- Adapts to problem structure

---

## Understanding Results

### Results Panel Explained

**Path Found: Yes/No**

Indicates whether a valid route exists between start and goal.
- "Yes": Algorithm successfully found a path
- "No": Goal is unreachable (completely surrounded by walls)

**Path Length: [Number]**

Total number of steps in the solution path.
- Includes start and goal positions
- Lower values indicate more direct routes
- A* guarantees this is the shortest possible path

**Nodes Explored: [Number]**

Total number of cells examined during the search.
- Includes all cells in closed set
- Does not include cells that were never reached
- Indicates algorithm efficiency

**Time Taken: [Number] ms**

Execution duration in milliseconds.
- Measures pure algorithm runtime
- Excludes visualization rendering time
- Typical ranges:
  - 10x10 maze: 1-10ms
  - 20x20 maze: 5-20ms
  - 30x30 maze: 15-50ms

**Efficiency: [Percentage]**

Ratio of path length to nodes explored.
```
Efficiency = (Path Length / Nodes Explored) × 100%
```

Interpretation:
- 50%+: Excellent (very direct search)
- 30-50%: Good (efficient exploration)
- 20-30%: Fair (moderate wandering)
- <20%: Poor (many dead ends explored)

### Reading the Visualization

**Canvas Display:**
- Look for the yellow path connecting green (start) to red (goal)
- Light blue areas show where A* explored
- Notice how exploration tends toward the goal
- Observe how walls channel the search

**ASCII Output:**
```
S . . # . . . . . .
* * . # . . # . . .
. * * # . . # . . .
. . * * * . # . . .
. . . . * . # . . .
. # . . * . . . . .
. # . . * * * * . .
. . . . . . . * . .
. . # . . . . * * G
. . # . . . . . . .
```

Legend:
- S = Start position
- G = Goal position
- asterisk = Solution path
- # = Wall
- . = Open space

---

## Performance Metrics

### What the Numbers Mean

**Example Results:**

```
Path Length: 38
Nodes Explored: 156
Time Taken: 8.45 ms
Efficiency: 24.4%
```

**Analysis:**
- Shortest path requires 38 steps
- A* examined 156 cells total (including path)
- Solved in 8.45 milliseconds
- About 1 in 4 explored cells was on the final path
- This is good performance for a moderately complex maze

### Typical Performance by Difficulty

**Easy Maze (10x10, 20% obstacles):**
- Path Length: 15-25 steps
- Nodes Explored: 30-60 cells
- Time: 1-5ms
- Efficiency: 35-50%

**Medium Maze (20x20, 30% obstacles):**
- Path Length: 30-45 steps
- Nodes Explored: 100-200 cells
- Time: 5-15ms
- Efficiency: 20-35%

**Hard Maze (30x30, 40% obstacles):**
- Path Length: 50-75 steps
- Nodes Explored: 250-500 cells
- Time: 15-40ms
- Efficiency: 15-25%

### Factors Affecting Performance

**Maze Size:**
- Larger mazes = more cells to explore
- Exponential growth in search space
- Linear increase in path length

**Obstacle Density:**
- More walls = more complex navigation
- Forces longer detours
- Reduces efficiency ratio
- May result in no path

**Maze Layout:**
- Open areas allow direct paths
- Corridors channel exploration
- Dead ends waste exploration effort
- Walls near goal increase difficulty

---

## Configuration Options

### Available Settings

**Maze Size Selection:**

Easy (10×10):
- Quick generation and solving
- Good for understanding algorithm basics
- Low computational requirements
- Ideal for demonstrations

Medium (20×20):
- Balanced complexity
- Shows algorithm intelligence clearly
- Reasonable exploration patterns
- Default recommended setting

Hard (30×30):
- Challenging pathfinding
- Demonstrates scalability
- Extensive exploration visible
- Maximum supported size

**Obstacle Density Selection:**

Low (20%):
- Fewer walls, more open spaces
- Easier paths, higher efficiency
- Good for showing optimal behavior
- Quick solutions

Medium (30%):
- Balanced obstacle placement
- Realistic complexity
- Demonstrates heuristic value
- Default recommended setting

High (40%):
- Many walls, complex navigation
- Difficult pathfinding scenarios
- Lower efficiency expected
- Tests algorithm robustness

### Customization Tips

**For Educational Demonstrations:**
- Start with Easy maze, Low density
- Show how A* explores toward goal
- Progress to harder difficulties
- Compare efficiency across settings

**For Performance Testing:**
- Use Medium or Hard with High density
- Run multiple times to see variation
- Compare path lengths and exploration
- Document efficiency trends

**For Report Screenshots:**
- Use Medium maze (20x20) for visibility
- Medium density (30%) for balance
- Clear visualization at this size
- Professional appearance

---

## Visual Legend

### Canvas Color Coding

| Color | Element | Meaning |
|-------|---------|---------|
| Black | Wall | Impassable obstacle, cannot traverse |
| White | Open Path | Walkable cell, can be part of route |
| Green | Start | Beginning position, always clear |
| Red | Goal | Target position, destination |
| Yellow/Gold | Solution | Optimal path found by A* |
| Light Blue | Explored | Examined by algorithm, not on final path |

### ASCII Character Coding

| Symbol | Element | Meaning |
|--------|---------|---------|
| S | Start | Beginning position |
| G | Goal | Target destination |
| asterisk | Path | Part of solution |
| # | Wall | Impassable obstacle |
| . | Open | Walkable space |
| · | Explored | Checked but not used (if shown) |

---

## Technical Details

### Implementation Details

**Programming Language:**
- JavaScript ES6+ features
- Arrow functions for concise code
- Classes for object-oriented structure
- Map and Set for efficient data storage

**Data Structures:**

Priority Queue:
```javascript
class PriorityQueue {
  items = [];
  enqueue(item, priority) { /* min-heap ordering */ }
  dequeue() { /* returns lowest priority item */ }
}
```

Grid Representation:
```javascript
maze = [
  [0, 1, 0, 0],  // 0 = walkable, 1 = wall
  [0, 0, 0, 1],
  [1, 0, 0, 0],
  [0, 0, 1, 0]
];
```

**Algorithm Complexity:**

Time Complexity: O(b^d)
- b = branching factor (typically 4 for grid)
- d = depth of solution

Space Complexity: O(b^d)
- Stores nodes in open and closed sets
- Path reconstruction storage

In practice:
- Much better than worst case due to heuristic
- Typically explores 20-40% of total cells
- Exponentially faster than uninformed search

### Browser Requirements

**Minimum Browser Versions:**
- Google Chrome 80+
- Mozilla Firefox 75+
- Apple Safari 13+
- Microsoft Edge 80+
- Opera 67+

**Required Features:**
- ES6 JavaScript support (classes, arrow functions, Map, Set)
- HTML5 Canvas API
- CSS3 styling
- Blob and download APIs

**Not Required:**
- Internet connection (runs offline)
- Special plugins or extensions
- Server-side processing
- Additional libraries or frameworks

### File Structure

The entire application is contained in a single HTML file:

```html
<!DOCTYPE html>
<html>
  <head>
    <style>/* CSS styling */</style>
  </head>
  <body>
    <!-- HTML structure -->
    <script>/* JavaScript logic */</script>
  </body>
</html>
```

**Advantages:**
- Easy to share (single file)
- No dependencies to manage
- Works offline immediately
- Simple to submit and grade
- Portable across systems

---

## Examples and Test Cases

### Recommended Test Sequence

**Test 1: Easy Maze**

Configuration:
- Size: 10×10
- Density: 20%

Purpose:
- Verify basic functionality
- Show algorithm efficiency
- Quick solution demonstration

Expected Results:
- Path found: Yes
- Path length: 15-20 steps
- High efficiency (40%+)
- Fast execution (<5ms)

**Test 2: Medium Maze**

Configuration:
- Size: 20×20
- Density: 30%

Purpose:
- Balanced complexity demonstration
- Typical use case
- Clear visualization

Expected Results:
- Path found: Yes
- Path length: 30-45 steps
- Moderate efficiency (25-35%)
- Reasonable execution (5-15ms)

**Test 3: Hard Maze**

Configuration:
- Size: 30×30
- Density: 40%

Purpose:
- Stress test
- Show scalability
- Demonstrate robustness

Expected Results:
- Path found: Yes (usually)
- Path length: 50-75 steps
- Lower efficiency (15-25%)
- Longer execution (15-40ms)

### Comparative Analysis Example

Run all three tests and create comparison table:

| Test | Size | Density | Path | Explored | Time | Efficiency |
|------|------|---------|------|----------|------|------------|
| Easy | 10×10 | 20% | 18 | 42 | 2.3ms | 42.9% |
| Med | 20×20 | 30% | 38 | 156 | 8.5ms | 24.4% |
| Hard | 30×30 | 40% | 62 | 387 | 28.7ms | 16.0% |

Observations:
- Path length increases with maze size
- Exploration grows faster than path length
- Efficiency decreases with complexity
- Time scales reasonably with problem size

---

## Troubleshooting

### Common Issues and Solutions

**Problem: Page appears blank or controls don't show**

Solutions:
- Ensure JavaScript is enabled in browser
- Try a different browser (Chrome recommended)
- Check browser console for errors (F12)
- Verify HTML file is complete and not corrupted

**Problem: "Run A* Algorithm" does nothing**

Solutions:
- First click "Generate New Maze"
- Check if browser is blocking scripts
- Refresh the page and try again
- Look for error messages in console

**Problem: Maze visualization is too small/large**

Solutions:
- Canvas size adjusts automatically to maze dimensions
- Try different maze sizes from dropdown
- Zoom browser view (Ctrl/Cmd + or -)
- Check screen resolution (minimum 1024×768)

**Problem: "Download Results" button not working**

Solutions:
- Allow pop-ups for this page
- Try right-click and "Save As" on downloaded file
- Check browser download settings
- Ensure algorithm has been run first

**Problem: Algorithm says "No path found" on every maze**

Solutions:
- This can happen with high obstacle density
- Generate several mazes (randomness varies)
- Try lower obstacle density (20%)
- This is actually correct behavior if truly no path

**Problem: Performance seems slow**

Solutions:
- This is normal for 30×30 mazes with high density
- Algorithm is working correctly if it completes
- Consider using smaller maze size
- Close other browser tabs to free resources

---

## For Academic Use

### Using This Project in Reports

**What to Include:**

1. Problem Statement
- Maze pathfinding challenge
- Need for optimal and efficient solution
- Real-world applications

2. Algorithm Description
- A* search algorithm explanation
- Manhattan distance heuristic
- Why these choices were made

3. Implementation Details
- Web-based approach justification
- Data structures used
- Key algorithm steps

4. Test Results
- Three difficulty levels tested
- Performance metrics table
- Screenshots of visualization

5. Analysis
- How results demonstrate algorithm effectiveness
- Efficiency trends across difficulties
- Comparison to theoretical expectations

6. Conclusion
- A* successfully finds optimal paths
- Performance scales reasonably
- Web implementation is effective

### Creating Your Report

**Section 1: Introduction (0.5-1 page)**
```
Pathfinding algorithms are fundamental to many applications
including GPS navigation, game AI, and robotics. This project
implements the A* search algorithm...
```

**Section 2: Methodology (1-2 pages)**
```
The A* algorithm was chosen because it guarantees optimal
solutions while maintaining efficiency through heuristic
guidance. The Manhattan distance heuristic was selected...
```

**Section 3: Implementation (1 page)**
```
The system was implemented using HTML5, CSS3, and JavaScript
to provide an interactive, platform-independent solution.
The core data structures include...
```

**Section 4: Results (1-2 pages)**
Include:
- Screenshots of all three test mazes
- Performance metrics table
- ASCII representations
- Downloaded results files

**Section 5: Analysis (1-2 pages)**
```
The results demonstrate that A* successfully finds optimal
paths in all solvable mazes. As maze complexity increases,
we observe that...
```

**Section 6: Conclusion (0.5 page)**
```
This project successfully demonstrates the A* pathfinding
algorithm through an interactive web application. The results
validate the algorithm's optimality and efficiency...
```

### Citing This Work

```
A* Maze Pathfinding - Web Implementation
Author: [Your Name]
Date: December 2025
Technology: HTML5, CSS3, JavaScript ES6
Algorithm: A* Search with Manhattan Distance Heuristic
File: astar_maze.html
```

---

## Browser Support

### Tested Browsers

**Fully Supported:**
- Google Chrome 90+ (Recommended)
- Mozilla Firefox 88+
- Microsoft Edge 90+
- Apple Safari 14+
- Opera 76+

**Mobile Support:**
- iOS Safari 14+
- Chrome Mobile 90+
- Firefox Mobile 88+

**Note:** Works best on desktop/laptop for optimal viewing experience.

---

## Additional Information

### File Size

The complete application is approximately 15-20 KB, making it:
- Quick to load
- Easy to email
- Fast to download
- Minimal storage requirement

### Offline Capability

Once loaded, the application:
- Requires no internet connection
- Stores no data remotely
- Processes everything client-side
- Maintains full functionality offline

### Privacy

The application:
- Runs entirely in your browser
- Sends no data to external servers
- Stores nothing permanently
- Collects no user information

---

## Getting Help

If you encounter issues not covered in troubleshooting:

1. Check browser console for errors (F12)
2. Verify browser version meets requirements
3. Try in a different browser
4. Ensure JavaScript is enabled
5. Review the code comments for implementation details

---

## Acknowledgments

- A* algorithm: Hart, Nilsson, and Raphael (1968)
- Manhattan distance heuristic for grid-based pathfinding
- HTML5 Canvas API for visualization
- JavaScript ES6 for modern implementation

---
   
**Author:** SATURN team 
