# Game of Life

## Code:
```
function createGrid(cols, rows) {
  return Array.from({ length: cols }, () => Array(rows).fill().map(() => floor(random(2))));
}

let grid;
const cellSize = 5;

function setup() {
  createCanvas(1400, 1400);
  grid = createGrid(width / cellSize, height / cellSize);
}

function draw() {
  background(0);
  grid = grid.map((col, x) => col.map((cell, y) => {
    let neighbors = countNeighbors(x, y);
    return cell ? (neighbors === 2 || neighbors === 3 ? 1 : 0) : (neighbors === 3 ? 1 : 0);
  }));
  renderGrid();
}

function renderGrid() {
  grid.forEach((col, x) => col.forEach((cell, y) => {
    if (cell) {
      fill(255);
      stroke(0);
      rect(x * cellSize, y * cellSize, cellSize - 1, cellSize - 1);
    }
  }));
}

function countNeighbors(x, y) {
  return [-1, 0, 1].reduce((sum, dx) => sum + [-1, 0, 1].reduce((s, dy) => 
    s + (dx || dy ? grid[(x + dx + grid.length) % grid.length][(y + dy + grid[0].length) % grid[0].length] : 0), 0), 0);
}
```

## p5 Sketch Link:
[[https://editor.p5js.org/rsutter/full/llwXjHgxG](https://editor.p5js.org/rsutter/full/S1lUH2hNO)](https://editor.p5js.org/rsutter/full/Fpxa2KSYn)
