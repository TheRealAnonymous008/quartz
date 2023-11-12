* A subtype of [[Partitioning Puzzles]] where we must find one contiguous region of cells.

### Agre
* *Goal*: Shade some cells.
* *Constraint*: Black cells form an orthogonally connected area.
* *Constraint*: Cells with a number indicate how many cells in the region must be shaded.
* *Constraint*: In regions without a number any amount may be shaded or none may be shaded.
* *Constraint*: There cannot be a run of four or more black or white cells. 

### Canal View
* *Goal*: Shade some cells on the grid.
- *Constraint*: All black cells create a single connected group.
- *Constraint*: No pools. No $2\times 2$ cell area within the grid can contain all black cells.
- *Constraint*: Numbered cells must not be black.
- *Constraint*: Each numbered cell indicates the total number of black cells connected orthogonally to that numbered cell, in a straight line until the next white cell, or the edge of the grid.

### Creek
* *Goal*: Shade some cells on the grid.
* *Constraint*: Clues at the corners of the grid indicate how many adjacent cells are shaded.
* *Constraint*: Unshaded cells must be connected horizontally or vertically 

### Fobidoshi
* *Goal*: Place circles into empty cells.
* *Constraint*: All circles form an orthogonally connected area
* *Constraint*: Lines of connected circles must not contain more than $3$ circles.

### Gaidoaro
* *Goal*: Shade some cells on the grid.
* *Constraint*: White cells form one orthogonally connected regions.
* *Constraint*: Black cells are not orthogonally adjacent to each other.
* *Constraint*: Cells with arrows cannot be blackened. The arrow indicates the direction to move to reach the star (following white cells). 
* *Constraint*: Cells with the star cannot be blackened
* *Constraint*: From any white cell, there must only be one way to reach the cell with a star

### Golem Grad
* *Goal*: Shade some cells. Combines Nurikabe and Snake
* *Constraint*: The black cells divide the grid into areas of white cells ("islands"), each containing at most one number.
- *Constraint*: Two islands may not be connected.
- *Constraint*: The island must have the same number of white cells as the number it contains.
- *Constraint*: All black cells must form an orthogonally continuous area.
- *Constraint*: No $2\times 2$ cell area within the grid can consist of only shaded cells.
- *Constraint*: All black cells can be decomposed into snakes. The heads and tails are given
- *Constraint*: Snakes must not cross each other.

### Hakoiri
* *Goal*: Place exactly one triangle, one square, and one circle in each region.
* *Constraint*: The same figure cannot be placed in orthogonally or diagonally adjacent squares.
* *Constraint*: Cells with figures form an orthogonally connected region.

### Hamle
* *Goal*: Move every black cell orthogonally.
* *Constraint*: The numbers in the black cell indicate the length of the moves made.
* *Constraint*: In the solved board, all white cells are interconnected.
* *Constraint*: In the solved board, no black cell should share an edge.

### Heyablock
* *Goal*: Shade some cells on the grid.
- *Constraint*: All black cells in a region must be connected.
- *Constraint*: A cell with a number indicates how many cells in the region must be shaded.
- *Constraint*: In regions without a number at least one cell must be shaded
- *Constraint*: When two cells are orthogonally adjacent across a region boundary, at least one cell must be white.
- *Constraint*: All white cells form one orthogonally connected area.
- *Constraint*: A line of connected white cells cannot go through two or more region borders.

### Heyawake
* *Goal*: Shade some cells in the puzzle. 
* *Constraints*: The grid is divided into variously sized rectangular rooms. 
* *Constraint*: Shaded cells cannot be orthogonally connected, although they can touch diagonally.
* *Constraint*: All unshaded cells form a single connected region.
* *Constraint*: Some rooms contain a single number.
* *Constraint*: A number indicates how many painted cells there are in that room.
* *Constraint*: A room which has no number may contain any number of painted cells or none.
* *Constraint*: Any line of unshaded cells that connects three or more rooms is forbidden. No straight orthogonal line may contain unshaded cells from more than two rooms.

### Hitori 
* *Goal*: Shade some cells such that there are no duplicate numbers in any row or column. 
* *Constraint*: Shaded cells may not touch each other orthogonally (but they can touch diagonally). 
* *Constraint*: The remaining cells must all be connected to each other orthogonally.

### Irupu
* *Goal*: Locate some blocks in the grid
* *Constraint*: Blocks are either $1\times 3$ or $3\times 1$ in size.
* *Constraint*: Blocks contain one circle
* *Constraint*: Blocks must be orthogonally adjacent to exactly two other blocks.
* *Constraint*: Blocks form one contiguous region.

### Island
* *Goal*: Shade some cells in the grid.
* *Constraint*: Unshaded cells form a single island. Each numbered cell is a part of this island.
* *Constraint*: Numbers indicate how many unnumbered white cells can be reached by moving orthogonally.
* *Constraint*: Numbered cells block access from one another.

### Kabingurodo
* *Goal*: Shade some cells on the grid.
* *Constraint*: Cells with circles are always white.
* *Constraint*: All white cells form an orthogonally continuous area
* *Constraint*: Black cells cannot touch each other orthogonally.
* *Constraint*: Each path from one circle to another must turn at least two times.

### Kuroshuto
* *Goal*: Shade some of the cells on the grid.
* *Constraint*: Numbers indicate that only one of the cells with that distance from the cell must be blackened (so  exactly one of $-X$ or $+X$  must be blackened)
* *Constraint*: Black cells are not orthogonally adjacent.
* *Constraint*: White cells are connected.

### Kurotto
* *Goal*: Shade some cells on the grid.
* *Constraint*: Cells with circles cannot be blackened
* *Constraint* Shaded cells form orthogonally contiguous regions.
* *Constraint*: Numbers in a circle indicate the number of black cells in regions orthogonally neighboring the cell. 
	* That is, the sum of the sizes of regions that are orthogonally adjacent to the clue
* *Constraint*: Cells with empty circles may have any number of black cells around them.

### LITS
* *Goal*: Shade exactly four connected cell in each region.
* *Constraint*: Shaded cells form either an L, I, T, or S tetromino, rotated or mirrored.
* *Constraint*: Tetrominoes form an orthogonally contiguous area.
* *Constraint*: No pools. No $2\times 2$ area contains only shaded cells.
* *Variant*: **Double LITS** - each region contains two tetrominoes. These two tetrominoes cannot touch orthogonally (but they can touch diagonally). They can be of the same or different shape.

### Nuraf
* *Goal*: Shade some cells, combining [[Partitioning Puzzles#Araf|Araf]] and [[#Nuraf]] rules.
- *Constraint*: The black cells divide the grid into areas of white cells ("islands").
- *Constraint*: Numbered cells are always white.
- *Constraint*: Two islands may not be orthogonally connected.
- *Constraint*: All of the black cells must be connected.
- *Constraint*: No $2\times 2$ cell area within the grid can have the black color.
- *Constraint*: Each island contains exactly two numbers. An island must have an area that is strictly between those numbers. 


### Nurikabe
* *Goal*: Shade some of the cells on the grid to form islands (connected regions of unshaded cells) and the sea (connected regions of shaded cells)
* *Constraint*: Each numbered cell is part of an island. The number in it is the number of cells in that island.
* *Constraint*: Each island contains exactly one numbered cell.
* *Constraint*: There is only one sea.
* *Constraint*: No pools. No $2x2$ areas of only shaded cells.
* *Variant*: **Line Nurikabe** - grid cannot contain five consecutive black cells in a row or column. In return, pools are allowed.
* *Variant*: **Pairs Nurikabe** - islands must contain exactly two numbers. The size of the island equals the sum of these numbers.

### Nurimaze
* *Goal*: Shade some regions.
* *Constraint*: Cells with letters, circles or triangles are always white.
- *Constraint*: White cells form a one-cell-wide path from a cell with S ("start") to a cell with G ("goal").
- *Constraint*: A path from S to G includes all cells with circles and no cells with triangles.
- *Constraint*: No pools. No $2\times 2$ cell area within the grid can have the same color.
- *Constraint*: All white cells must form an orthogonally continuous area.
- *Constraint*: White cells must not form a loop.

### Nurimisaki
* *Goal*: Shade some cells
- *Constraint*: White cells form a path exactly one cell wide.
- *Constraint*: Cells with circles are always white.
- *Constraint*: A cell with a circle must have exactly one white cell adjacent to its side.
- *Constraint*: A white cell without a circle must have at least two orthogonally adjacent white cells.
- *Constraint*: A number in a circle indicates how many white cells can be seen orthogonally from that cell, including the cell itself.
- *Constraint* White cells form an orthogonally connected region.
- *Constraint*: No $2\times 2$ cell area within the grid can have the same color.

### Oases
* *Goal*: Shade some cells.
* *Constraint*: Unshaded cells form an orthogonally connected region.
* *Constraint*: Shaded cells cannot share an edge with each other.
* *Constraint*: Cells with circles are unshaded.
* *Constraint*: No pools. No $2\times 2$ area of only unshaded cells.
* *Constraint*: Each circled number represents the number of other circles that can be reached from that circle by only going through empty (unshaded and uncircled cells).

### Peintoeira
* *Goal*: Shade some cells in the grid.
* *Constraint*: All cells in a region have the same color.
* *Constraint*: A cell with a number indicates how many shaded cells are adjacent to it.
* *Constraint*: Black cells must form an orthogonally continuous area.
* *Constraint*: No pools. No $2x2$ area on the grid can have the same color.

### Sashikabe
* *Goal*: Similar to [[#Nurikabe]] but with additional constraints
* *Constraint*: All islands must be L shaped and one cell wide.
* *Constraint*: Islands may not be connected.
* *Constraint*: Arrows mark the end of the island's leg. The arrow points to the cell in which the L "bends". 

### Stitches
* *Goal*: Connect each region with exactly one line (the stitch).
* *Constraint*: Each line is one cell long.
* *Constraint*: Cells may be visited by at most one line.
* *Constraint*: Numbers at the edge of the grid indicate how many end points must be placed in the row or column.

### Sukoro
* *Goal*: Place the numbers $1$ to $4$.
* *Constraint*: The number inside a cell represents how many neighboring cells contain numbers.
* *Constraint*: When two cells with numbers are orthogonally adjacent, the numbers must be different.
* *Constraint*: Numbered cells form an orthogonally connected region.

### Tapa
* *Goal*: Shade some cells in the grid.
* *Constraint*: Shaded cells form one contiguous region.
* *Constraint*: No pools. No $2x2$ area can contain all shaded cells.
* *Constraint*: Cells with numbers may not be filled.
* *Constraints*: Numbers tell the length of each consecutive shaded cell block in the eight surrounding cells.
* *Constraint*: If there is more than one digit in a cell, the groups of shaded cells have to be separated by at least one unshaded cell
* *Constraint*: Question mark clues represent any nonzero integer.
* *Variant*: **Tapa Line** - no four consecutive black cells in any row or column.
* *Variant*: **No Squares** - no $2\times 2$ area can contain cells of the same color (extends Tapa's constraints to apply to white cells.)
* *Variant*: **Equal Tapa** - the amount of non-clue white cells must be equal to the amount of black cells.
* *Variant*: **B&W** 
	* Black cells should form two separate contiguous regions.
	* Clue cells are considered white cells.
	* No $2\times 2$ area can contain cells of the same color (extends Tapa's constraints to apply to white cells.)
* *Variant*: **Tapa [[#Island|Islands]]** 
	- White cells form separate areas ("islands") surrounded by the black cells.
	- Each separate area may contain at most one clue cell.
	- If there is a clue cell in an area, at least one digit should give the size of that area in unit squares.
- *Variant*: **Pata** - number clues apply to white cells instead.
- *Variant*: **Tapa Balance** - the amount of black cells in the left part of the grid is equal to the amount of black cells on the right (refer to the indicated marker). Clues and White cells are considered weightless.
- *Variant*: **Tapa Row** - the sum of all clue digits in the row is equal to the amount of black cells in this row.
- *Variant*: **Tapa 1-n** - all rows and columns contain different amounts of black cells.
- *Variant*: **Dissected Tapa** - black cells and white cells form regions of the same size and shape. 
- *Variant*: **Diagonal neighbors** - every black cell must have at least one diagonally adjacent black cell.

### Tasukeua
* *Goal*: Shade some cells on the grid.
* *Constraint*: Cells with clues cannot be shaded.
* *Constraint*: Shaded cells form square regions.
* *Constraint*: Square regions are not orthogonally adjacent
* *Constraint*: Numbered clues indicate the number of black cells in regions neighboring the numbered cell.
* *Constraint*: Question mark clues indicate at least one adjacent shaded cell.
* *Constraint*: The white cells form one orthogonally continuous region

### Usowan
* *Goal*: Shade some cells in the grid.
* *Constraint*: Numbered cells are unshaded.
* *Constraint*: Numbers indicate how many black cells are adjacent to its four sides.
* *Constraint*: In each region, there is exactly one wrong number that shows the wrong amount of black cells.
* *Constraint*: Black cells are not orthogonally adjacent.
* *Constraint*: White cells must be connected.

### Yajikabe
* *Goal*: Similar to [[#Nurikabe]] except with additional constraints 
* *Constraint*: A cell containing a number and an arrow represents how many unshaded cells are in the row or column pointed at by the arrow in the direction of the arrow.

### Yajisan-Kazusan
* *Goal*: Shade some cells in the grid.
- *Constraint*: Shaded cells must not be orthogonally connected.
- *Constraint*: A cell with a number may be shaded. 
- *Constraint*: All the white cells must form an orthogonally continuous area.
- *Constraint*: A cell containing a number and an arrow represents how many black cells are in the row or column pointed at by the arrow.
- *Constraint*: Numbered cells must be painted black if they contain false clues, but numbered cells painted black do not necessarily contain false clues.