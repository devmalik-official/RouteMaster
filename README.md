# RouteMaster

## 1. What it does
RouteMaster is a lightweight BFS pathfinding visualizer: paste a grid + start/target JSON, compute the shortest route (if reachable), and see the grid and path rendered with step numbers.

## 2. How to run it
Open `index.html` in a browser — no install needed.

## 3. How the algorithm works
It uses **Breadth-First Search (BFS)** on a 2D grid, exploring neighbors in layers (up/down/left/right). Each queued node stores a **parent pointer**, so when the target is reached, the path is reconstructed by walking parents from target back to start and then reversing the list. Time complexity is \(O(N \times M)\) for an \(N \times M\) grid (each cell is visited at most once).

## 4. Input JSON format (with example)
- `grid`: 2D array where `1` = obstacle, `0` = open (other values are treated as open by the visualizer)
- `start`: `[row, col]`
- `targets`: array of targets; the app currently uses `targets[0]`

Example:
```json
{"grid":[[0,0,1],[1,0,1],[0,2,0]],"start":[0,0],"targets":[[2,1]]}
```

## 5. Output JSON format
The app outputs an object with:
- `total_steps`: integer number of moves (\(path.length - 1\))
- `path`: array of `[row, col]` positions from start to target (inclusive)
- `target_reached`: boolean indicating whether a path was found
- `execution_time_ms`: integer elapsed milliseconds for the computation

## 6. Screenshot
Screenshot: (add image here)
