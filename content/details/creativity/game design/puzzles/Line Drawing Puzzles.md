* The general goal is to draw a line (sometimes a loop) around the grid
* Has some overlap with [[Partitioning Puzzles]] since the line can partition the grid into two sections. However, this category specifically pertains to performing the partition by drawing a loop

### Arrow Maze
* *Goal*: Find a path through the grid visiting every cell once.
* *Constraint*: The path starts from the cell numbered $1$.
* *Constraint*: The path can travel only in the direction of the arrow, but it can travel any number of cells.

### Arrow Web
* *Goal*: Shade some of the arrows.
* *Constraint*: Each shaded arrow in the grid points to exactly one shaded arrow.

### Arukone / Number Link
* *Goal*: Connect each pair of numbers with a single continuous line
* *Constraint*: Lines cannot cross or touch each other.
* *Variant*: **Arakune-3** 
	* Every line must not cover a $2\times 2$ area (so $2\times 2$ areas must contain lines from at least two distinct pairs). 
	* All cells must be filled.

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

### Endoran
* *Goal*: Draw orthogonal lines between the centers of cells.
* *Constraint*: Each line connects two cells at different regions.
* *Constraint*: Numbers in a region indicates how many lines start or end in the region.
* *Constraints*: All cells must be part of a line.

### Entry/Exit
* *Goal*: Draw a single continuous non-intersecting loop through all cells.
* *Constraint*: The loop enters and exits each region exactly once.

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

### Miti
* *Goal*: Shade some of the grid lines.
* *Constraint*: In each given grid dot, exactly three black lines must meet.
* *Constraint*: In all other grid dots, at most two black lines may intersect
* *Constraint*: All cells of the grid form a single closed loops without dead ends, exactly one cell wide.

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

### Rectslider
* *Goal*: Move black cells orthogonally.
* *Constraint*: In the solution, black cells form rectangles with areas greater than one cell.
* *Constraint*: Rectangles cannot be orthogonally adjacent.
* *Constraint*: Numbers in the cell indicate how many cells they have to pass through.
* *Constraint*: Black cells with no numbers may move any distance or may not move at all.
* *Constraint*: Black cells cannot cross the tracks of other black cells.
* *Constraint*: Black cells cannot move over black cells.

### Round Trip
* *Goal*: Draw a single loop.
* *Constraint*: The loop can cross itself orthogonally, but otherwise does not touch or retrace itself.
* *Constraint*: Numbers along the edges indicate how many cells are visited by the nearest section of the loop in the corresponding row or column.

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
* *Variant*: **Sheep and Wolves** - sheep and wolves are given. Sheep must be kept within the loop. Wolves must be kept outside.

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