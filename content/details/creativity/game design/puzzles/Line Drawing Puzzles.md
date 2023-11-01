* The general goal is to draw a line (sometimes a loop) around the grid
* Has some overlap with [[Partitioning Puzzles]] since the line can partition the grid into two sections. However, this category specifically pertains to performing the partition by drawing a loop

### Arukone / Number Link
* *Goal*: Connect each pair of numbers with a single continuous line
* *Constraint*: Lines cannot cross or touch each other.

### Corral
* *Goal*: Draw a single continuous loop along the lines of the grid.
* *Constraint*: All numbers on the grid are contained inside.
* *Constraint*: Each number indicates the total number of cells visible in any orthogonal direction before a line in the loop is reached.
### Four Winds
* *Goal*: Draw orthogonal lines on each white cell.
* *Constraint*: Numbers in the black cells represent the total number of white cells occupied by the lines from that number.
* *Constraint*: Lines cannot enter other black cells.
* *Constraint*: Lines cannot intersect.

### Gokigen Naname
* *Goal*: Fill in a diagonal line in every cell.
* *Constraint*: Numbers in circled clues at grid points equal the number of lines extending from that circle.
* *Constraint*: Diagonal lines do not form closed loops.

### Grand Tour
* *Goal*: Connect the grid of points together to form a single loop.

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

### Koburin
* *Goal*: Shade some cells and draw a continuous non-intersecting loop passing through all empty white cells.
* *Constraint*: Cells with numbers are not included in the loop. They indicate the total number of black cells orthogonally adjacent to the cell.
* *Constraint*: The grid may contain black cells not adjacent to numbered cells.
* *Constraint*: Numbered cells are not shaded.
* *Constraint*: Black cells are not orthogonally adjacent.

### Korekutokonekuto
* *Goal*: Connect all the white cells with orthogonal lines.
* *Constraint*: Lines do not cross or touch black circles
* *Constraint*: If a number is given, the number of lines connected to the white circle must match the digit in the circle.

### Linesweeper / Loop
* *Goal*: Create a single continuous, non-intersecting loop that connects the centers of the grid cells.
* *Constraint*: Numbered cells cannot be passed through.
* *Constraint*: The number in the cell indicates how many of the orthogonal and diagonal neighbors contain part of the loop.

### Masyu
* *Goal*: Draw a single continuous non-intersecting loop that properly passes through all circled cells.
* *Constraint*: The loop enters each cell it passes through from the center and exits on a different side. In a rectangular grid, all turns are 90 degrees.
* *Constraint*: White circles must be travelled straight through, but the loop must turn in the previous or next cell in its path.
* *Constraint*: Black cells must be turned upon, but the loop must travel straight through the next and previous cells in its path.
* *Variant*: Gray circles which MAY either be white or black. The solver must deduce their color.
* *Variant*: Allowing wrap arounds from the edges of the board.
* *Variant*: The board is divided into regions. The loop must turn in each region at least once.

### Pipelink
* *Goal*: Draw a single continuous loop that passes through all cells.
* *Constraint*: The loop must use the given sections on the board.
* *Constraint*: The loop may cross itself.

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

### Slitherlink
* *Goal*: Draw a loop connecting the dots on the grid. There may be no loose ends. 
* *Constraint*: Numbers represent how many of its four sides are segments in the loop

### Snake
* *Goal*: Draw a single line between marked cells.
* *Constraint*: The line cannot touch itself orthogonally or diagonally. 
* *Constraint*: Numbers outside the grid show many cells are part of the snake.

### Thermometers
* *Goal*: Fill each thermometer on the grid to the appropriate level
* *Constraint*:  Numbers indicate how many squares are filled in that row or column.
* *Constraint*: Thermometers are filled from the bulb end towards the top.

### Yaijlin
* *Goal*: Draw a single, continuous, non-intersecting loop.
* *Constraint*: Some cells are black. Not all black cells are given
* *Constraint*: Some cells are indicative consisting of a number and an arrow pointing in an orthogonal direction.  The number tells you the count of the black cells that lie in that row or column in the direction of the arrow.
* *Constraint*: Indicative cells are never black and do not count as black cells for the purposes of satisfying other indicative cells.
* *Constraint*: Not all black cells may be accounted for by an indicative cell
* *Constraint*: The loop may not pass through indicative cells 
* *Constraint*: The loop may not pass through black cells.
* *Constraint*: The loop must pass through all non-indicative, non-black cells.
* *Constraint*: Loops must enter each cell from the center of one of the four sides and exit from a different side. All turns are orthogonal (90 degrees). 