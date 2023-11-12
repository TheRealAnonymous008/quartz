* The goal of these puzzles is to connect two cells using line segments. 
* To distinguish from [[Loop Drawing Puzzles]], the bridges do not have to form a continuous loop.
* Also included are sliding puzzles since this can be thought of as drawing a bridge from the block's source to its destination.

### Arrow Maze
* *Goal*: Find a path through the grid visiting every cell once.
* *Constraint*: The path starts from the cell numbered $1$.
* *Constraint*: The path can travel only in the direction of the arrow, but it can travel any number of cells.

### Arrow Web
* *Goal*: Shade some of the arrows.
* *Constraint*: Each shaded arrow in the grid points to exactly one shaded arrow.

### Four Winds
* *Goal*: Draw orthogonal lines on each white cell.
* *Constraint*: Numbers in the black cells represent the total number of white cells occupied by the lines from that number.
* *Constraint*: Lines cannot enter other black cells.
* *Constraint*: Lines cannot intersect.

### Hashiwokakero / Hashi
* *Goal*: Connect all islands by drawing a series of bridges between islands.
* *Constraint*: Bridges must begin and end at distinct islands, travelling a straight line in between.
* *Constraint*: Bridges cannot cross other bridges or other islands.
* *Constraint*: Bridges travel straight orthogonally (no diagonal movements).
* *Constraint*: At most two bridges connect a pair of islands.
* *Constraint*: The number of bridges connected to each island must match the clue given on that island.
* *Constraint*: The bridges must connect the islands into a single connected group.

### Hebi-Ichigo
* *Goal*: Place the numbers 1-5 in the grid.
* *Constraint*: Numbers form a chain of five cells connected orthogonally. Chains are called snakes. The $1$ and $5$ are the head and tail respectively.
* *Constraint*: Snakes cannot touch orthogonally.
* *Constraint*: Snakes cannot appear in front of the head of another snake. The snake’s eyes are located on a side of the head (cell with number 1), opposite from the side its body (cell with number 2) is connected to. A snake looks in the direction of its eyes until a black cell or the edge of the grid is reached.
* *Constraint*: Numbers in black cells shows the value of the nearest number in the direction of the arrow. This number must appear before any black cells.
* *Constraint*: A black cell with a zero means there is no snake in the direction of the arrow until the next black cell or the edge of the grid.

### Hiroimono
* *Goal*: Move along the grid lines and collect the stones (circles) on the grid.
- *Constraint*: Start at any stone.
- *Constraint*: When a stone is encountered, it is picked up.
- *Constraint*: When a stone is picked up, the direction can be changed.
- *Constraint*: No backtracking. You cannot reverse direction.
- *Constraint*: All stones must be collected.

### Hukuwall
* *Goal*: Draw horizontal or vertical lines in every empty cell.
* *Constraint*: Letters stand for numbers distinct from each other. Same letters get the same number. Different letters get different numbers. The number corresponding to each letter is to be determined by the solver.
* *Constraint*: Numbers indicate the total length of the line at the end of the edges of this cell.
* *Constraint*: A line cannot connect two lettered cells.
* *Constraint*: The number of line directions coming out of the same letter are different.

### Ichimaga
* *Goal*: Connect all circles with orthogonal lines.
* *Constraint*: The number of lines connected to the circle matches the digit of the circle.
* *Constraint*: At least one line connects to empty circles
* *Constraint* Lines cannot cross.
* *Constraint*: Lines may change direction no more than once.
* *Variant*: **Crossing Ichimaga** - the lines may cross other lines. Lines cannot change direction at the point of intersection.
* *Variant*: **Magnetic Ichimaga** - the circles with the same digits cannot be connected.

### Kaero
* *Goal*: Move some of the letters orthogonally.
* *Constraint*: All letters in a region must be the same.
* *Constraint*: Letters cannot cross the tracks of other letters or move over other letters.

### Kohi Gyunyu
* *Goal*: Connect circles with orthogonal lines.
* *Constraint*: Connected circles form a group.
* *Constraint*: Each group contains at least one gray circle and equal amounts of white and black circles.
* *Constraint*: Lines must not cross other lines.
* *Constraint*: Black and White circles cannot be directly connected.

### Korekutokonekuto
* *Goal*: Connect all the white cells with orthogonal lines.
* *Constraint*: Lines do not cross or touch black circles
* *Constraint*: If a number is given, the number of lines connected to the white circle must match the digit in the circle.

### Line Segment
* *Goal*: Draw line segments on the grid
* *Constraint*: Line segments pass through 3 or 4 consecutive cells, either orthogonally or diagonally.
* *Constraint*: Cells are visited exactly once.
* *Constraint*: Letters indicate the line segment's orientation (H = Horizontal, V = Vertical, D = Diagonal)

### Mintonette
* *Goal*:  Connect circles in pairs using orthogonal lines.
* *Constraint* Lines cannot touch or cross themselves or each other.
* *Constraint*: If a circle contains a number, it represents the number of turns the line has between two circles.
* *Constraint*: If two circles have no number, then the line can take any number of turns.
* *Constraint*: All cells must be part of either a line or contain a circle.
* *Constraint*: Each circle must be connected to another circle.

### Mirukuti
* *Goal*: Connect each group of circles. 
* *Constraint*: Connections form a T shape with white two white circles and one black circle. The white circles form the top of the T.
* *Constraint*: Lines cannot cross other lines.
* *Variant*: **Milk Tease** - The T can now also connect black circles in the  top of the T.

### Rectslider
* *Goal*: Move black cells orthogonally.
* *Constraint*: In the solution, black cells form rectangles with areas greater than one cell.
* *Constraint*: Rectangles cannot be orthogonally adjacent.
* *Constraint*: Numbers in the cell indicate how many cells they have to pass through.
* *Constraint*: Black cells with no numbers may move any distance or may not move at all.
* *Constraint*: Black cells cannot cross the tracks of other black cells.
* *Constraint*: Black cells cannot move over black cells.

### Roma
* *Goal*: Place arrows pointing in four orthogonal directions in each empty cell.
* *Constraint*: Arrows cannot repeat in a region.
* *Constraint*: Starting at any cell, going in the direction of the arrows, it is possible to reach the marked cell on the grid 

### Satogaeri
* *Goal*: Move the circles horizontally or vertically on the grid.
* *Constraint*: In the solved grid, each region must only contain one circle. 
* *Constraint*: Numbers in the circle indicate how many cells  they have to pass through.
* *Constraint*: Circles without a number may move any distance.
* *Constraint*: Circles cannot cross tracks with other circles.
* *Constraint*: Circles cannot move over other circles.

### Shirokuro
* *Goal*: Connect each white circle with a black circle with orthogonal lines.
* *Constraint*: Lines cannot cross 
* *Constraint*: Lines cannot turn.
* *Constraint*: Lines cannot pass through other circles.

### Snake
* *Goal*: Draw a single line between marked cells.
* *Constraint*: The line cannot touch itself orthogonally or diagonally. 
* *Constraint*: Numbers outside the grid show many cells are part of the snake.
* *Variant*: **Multiple Snakes** - the grid contains multiple snakes. Heads and tails are shown. Different snakes do not touch orthogonally or diagonally.
* *Variant* **Toroidal Snakes** - the grid wraps around the edge

### Stars and Arrows
* *Goal*: Place stars in empty cells.
* *Constraint*: Each arrow points to exactly one star.
* *Constraint*: Stars are pointed to by exactly one arrow. 
* *Constraint*: Stars obstruct vision from arrows.
* *Constraint*: Numbers outside the grid show the number of stars in that row or column.

### Thermometers
* *Goal*: Fill each thermometer on the grid to the appropriate level
* *Constraint*:  Numbers indicate how many squares are filled in that row or column.
* *Constraint*: Thermometers are filled from the bulb end towards the top.

### Trace Numbers
* *Goal*: Draw lines on the grid.
* *Constraint*: Lines start in the cell with number $1$ and visits all cells with numbers in order through the highest number.
* *Constraint*: Each cell must be visited exactly once.
* *Constraint*: Lines cannot cross.
### Wamuzu
* *Goal*: Connect circles on the grid using orthogonal lines
* *Constraint*: All empty cells must be part of the line.
* *Constraint*: All sections of each line must equal the length of the cell's side.

### Yajisan-Sokoban
* *Goal*: Move the some of the gray squares orthogonally.
* *Constraint*: Tracks cannot cross and cannot move over other gray squares.
* *Constraint*: Cells with numbers and arrows represent how many gray squares are in the row or column pointed by the arrow.
* *Constraint*: A gray square on top of a numbered cell plays no further role in the puzzle. The clue is either true or false.
* *Constraint*: If a gray square passes through a numbered cell, the numbered cell is true.
