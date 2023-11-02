* The general goal is to draw a line (sometimes a loop) around the grid
* Has some overlap with [[Partitioning Puzzles]] since the line can partition the grid into two sections. However, this category specifically pertains to performing the partition by drawing a loop
* Distinct from [[Bridge and Chain Drawing Puzzles]] by specifically involving loops. Although [[Trails, Walks, Paths and Cycles|loops are subsets of walks and trails]].

### Arukone / Number Link
* *Goal*: Connect each pair of numbers with a single continuous line
* *Constraint*: Lines cannot cross or touch each other.
* *Variant*: **Arakune-3** 
	* Every line must not cover a $2\times 2$ area (so $2\times 2$ areas must contain lines from at least two distinct pairs). 
	* All cells must be filled.

### Balance Loop
* *Goal*: Draw a single continuous non-intersecting loop.
* *Constraint*: The loop visits all cells with circles.
* *Constraint*: Loop segments extending orthogonally (up to turning points) from a white circle are of equal length.
* *Constraint*: Loop segments extending orthogonally (up to turning points) from a black circle are of unequal length.
* *Constraint*: If a circle contains a number, the number indicates the sum of the lengths of the loop segments on both sides of the circle before turning.

### Castle Wall
* *Goal*: Draw a single, closed non-intersecting loop.
* *Constraint*: Black cells must be outside the loop.
* *Constraint*: Bordered cells must be inside the loop.
* *Constraint*: Gray cells may or may not be inside the loop.
* *Constraint*: Numbers and arrows refer to how many cell borders in the arrow's direction are crossed by the loop.

### Corral
* *Goal*: Draw a single continuous loop along the lines of the grid.
* *Constraint*: All numbers on the grid are contained inside.
* *Constraint*: Each number indicates the total number of cells visible in any orthogonal direction before a line in the loop is reached.
* *Variant*: **Inside/Outside** - numbers can be anywhere. In both cases the number indicates how many cells can be seen orthogonally from that cell including the cell itself.

### Country Road
* *Goal*: Draw a single continuous non-intersecting loop that connects the centers of the grid cells.
* *Constraint*: Loop must visits each region exactly once.
* *Constraint*: The number in a region indicates how many cells in this region are visited by the loop.
* *Constraint*: In regions without a number, the loop may visit any number of cells.
* *Constraint*: If the loop does not visit any two neighboring cells, these cells must be in the same region.

### Detour
* *Goal*: Draw a single continuous non-intersecting loop.
* *Constraint*: The loop visits each cell exactly once.
* *Constraint*: Numbers in regions indicate the number of times the loop turns in the region.

### Dotchi-Loop
* *Goal*: Draw a single non-intersecting loop.
* *Constraint*: The loop must visit all cells with white circles.
* *Constraint*: The loop cannot pass through black circles.
* *Constraint*: In a region, the loop either always travels straight through white circles or always turns at a white circle.

### Double Back
* *Goal*: Draw a single closed loop of horizontal and vertical segments passing through all white cells.
* *Constraint*: Each region must be visited exactly twice.
* *Constraint*: The loop cannot pass through black cells.

### Endoran
* *Goal*: Draw orthogonal lines between the centers of cells.
* *Constraint*: Each line connects two cells at different regions.
* *Constraint*: Numbers in a region indicates how many lines start or end in the region.
* *Constraints*: All cells must be part of a line.

### Entry/Exit
* *Goal*: Draw a single continuous non-intersecting loop through all cells.
* *Constraint*: The loop enters and exits each region exactly once.

### Every Second Turn
* *Goal*: Draw a single continuous non-intersecting loop that visits every cell exactly once.
* *Constraint*: It can make a 90 degree turn at every cell with a circle.
* *Constraint*: There is exactly one turn between two consecutive circles that the loop visits.

### Geradeweg
* *Goal*: Draw a single, closed, non-intersecting loop.
* *Constraint*: The loop passes through all circles.
* *Constraint*: The number indicates the length of the straight segment that passes through the circle.
* *Constraint*: If the loop turns at a circle, both straight segments must have the same length as the number indicates.

### Grand Tour
* *Goal*: Connect the grid of points together to form a single loop.

### Kanjo
* *Goal*: Draw loops that passes through all cells.
* *Constraint*: Loops  may cross itself or other loops.
* *Constraint*: All given line fragments must be used as a part of a loop.
* *Constraint*: Cells with the same number belong to the same oop.
* *Constraint*: Cells with different numbers belong to different loops.
* *Constraint*. Loops go through at least one numbered cell.
* *Constraint*: A cell with a number must not contain the intersection point where a loop crosses itself or another loop.

### Koburin
* *Goal*: Shade some cells and draw a continuous non-intersecting loop passing through all empty white cells.
* *Constraint*: Cells with numbers are not included in the loop. They indicate the total number of black cells orthogonally adjacent to the cell.
* *Constraint*: The grid may contain black cells not adjacent to numbered cells.
* *Constraint*: Numbered cells are not shaded.
* *Constraint*: Black cells are not orthogonally adjacent.

### Konarupu
* *Goal*: Create a continuous non-intersecting loop drawn from one dot orthogonally to another adjacent dot.
* *Constraint*: Numbers indicate how many times the loop turns in the dots surrounding the cell.

### Kuroshiro
* *Goal*: Draw a single continuous non-intersecting loop.
* *Constraint*: The loop passes through all circled cells.
* *Constraint*: Between two successive circles of the same color, the loop must not be turned.
* *Constraint*: The loop must turn exactly once when travelling between two successive circles of different color.

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

### Mid Loop
* *Goal*: Draw a single continuous non-intersecting loop that passes through all dots at the centers of the cells.
* *Constraint*: Dots must be travelled straight through.
* *Constraint*: Segments of a straight line going out the dot must be equal That is, the length of the straight line segment going in equals the length of the straight line segment going out.

### Miti
* *Goal*: Shade some of the grid lines.
* *Constraint*: In each given grid dot, exactly three black lines must meet.
* *Constraint*: In all other grid dots, at most two black lines may intersect
* *Constraint*: All cells of the grid form a single closed loop without dead ends, exactly one cell wide.

### Moonsun
* *Goal*: Draw a single non-intersecting loop.
* *Constraint*: The loop must cross the borders of each region exactly twice.
* *Constraint*: In a region, the loop must visit either all cells with black cells or all cells with white circles.
* *Constraint*: Alternate between region types when following the loop. That is, if the current region has all X colored cells visited, then the next region visited must have all Y colored cells visited.

### Pipelink
* *Goal*: Draw a single continuous loop that passes through all cells.
* *Constraint*: The loop must use the given sections on the board.
* *Constraint*: The loop may cross itself.

### Purenrupu
* *Goal*: Draw a single loop passing through cell centers
* *Constraint*: The loop visits all white cells [[Trails, Walks, Paths and Cycles#Hamiltonian Graphs|exactly once]].

### Rimotoeiji
* *Goal*: Connect all dots with a single continuous non-intersecting loop.
* *Constraint*: All crosses and arrows are contained within the loop.
* *Constraint*: Arrows point in the direction of the longest straight sequence of cells visible from that cell.
* *Constraint*: Crosses are placed at the center of more than one longest straight sequences of cells within the loop.
### Round Trip
* *Goal*: Draw a single loop.
* *Constraint*: The loop can cross itself orthogonally, but otherwise does not touch or retrace itself.
* *Constraint*: Numbers along the edges indicate how many cells are visited by the nearest section of the loop in the corresponding row or column.

### Slitherlink
* *Goal*: Draw a loop connecting the dots on the grid. There may be no loose ends. 
* *Constraint*: Numbers represent how many of its four sides are segments in the loop
* *Variant*: **Sheep and Wolves** - sheep and wolves are given. Sheep must be kept within the loop. Wolves must be kept outside.

### Yajilin
* *Goal*: Draw a single, continuous, non-intersecting loop.
* *Constraint*: Some cells are black. Not all black cells are given
* *Constraint*: Some cells are indicative consisting of a number and an arrow pointing in an orthogonal direction.  The number tells you the count of the black cells that lie in that row or column in the direction of the arrow.
* *Constraint*: Indicative cells are never black and do not count as black cells for the purposes of satisfying other indicative cells.
* *Constraint*: Not all black cells may be accounted for by an indicative cell
* *Constraint*: The loop may not pass through indicative cells 
* *Constraint*: The loop may not pass through black cells.
* *Constraint*: The loop must pass through all non-indicative, non-black cells.
* *Constraint*: Loops must enter each cell from the center of one of the four sides and exit from a different side. All turns are orthogonal (90 degrees). 
* *Variant*: **Regional** - Shade some cells and draw a single non-intersecting loops through all white cells.
	* Numbers in regions indicate the number of black cells in the region.
	* Regions with no number can contain any number of black cells.
	* No two black cells can share a border.
	* Loops can visit numbered cells.
	* Numbered cells can be shaded