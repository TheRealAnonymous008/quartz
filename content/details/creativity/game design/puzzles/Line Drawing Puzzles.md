* The general goal is to draw a line (sometimes a loop) around the grid
* Has some overlap with [[Partitioning Puzzles]] since the line can partition the grid into two sections. However, this category specifically pertains to performing the partition by drawing a loop

### Corral
* *Goal*: Draw a single continuous loop along the lines of the grid.
* *Constraint*: All numbers on the grid are contained inside.
* *Constraint*: Each number indicates the total number of cells visible in any orthogonal direction before a line in the loop is reached.
### Four Winds
* *Goal*: Draw orthogonal lines on each white cell.
* *Constraint*: Numbers in the black cells represent the total number of white cells occupied by the lines from that number.
* *Constraint*: Lines cannot enter other black cells.
* *Constraint*: Lines cannot intersect.

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

### Slitherlink
* *Goal*: Draw a loop connecting the dots on the grid. There may be no loose ends. 
* *Constraint*: Numbers represent how many of its four sides are segments in the loop

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