* A subtype of [[Partitioning Puzzles]] where we must find one contiguous region of cells.

### Creek
* *Goal*: Shade some cells on the grid.
* *Constraint*: Clues at the corners of the grid indicate how many adjacent cells are shaded.
* *Constraint*: Unshaded cells must be connected horizontally or vertically 

### Fobidoshi
* *Goal*: Place circles into empty cells.
* *Constraint*: All circles form an orthogonally connected area
* *Constraint*: Lines of connected circles must not contain more than $3$ circles.

### Purenrupu
* *Goal*: Draw a single loop passing through cell centers
* *Constraint*: The loop visits all white cells [[Trails, Walks, Paths and Cycles#Hamiltonian Graphs|exactly once]].

### Hakoiri
* *Goal*: Place exactly one triangle, one square, and one circle in each region.
* *Constraint*: The same figure cannot be placed in orthogonally or diagonally adjacent squares.
* *Constraint*: Cells with figures form an orthogonally connected region.

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

### Nurikabe
* *Goal*: Shade some of the cells on the grid to form islands (connected regions of unshaded cells) and the sea (connected regions of shaded cells)
* *Constraint*: Each numbered cell is part of an island. The number in it is the number of cells in that island.
* *Constraint*: Each island contains exactly one numbered cell.
* *Constraint*: There is only one sea.
* *Constraint*: No pools. No $2x2$ areas of only shaded cells.

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

### Tapa
* *Goal*: Shade some cells in the grid.
* *Constraint*: Shaded cells form one contiguous region.
* *Constraint*: No pools. No $2x2$ area can contain all shaded cells.
* *Constraint*: Cells with numbers may not be filled.
* *Constraints*: Numbers tell the length of each consecutive shaded cell block in the eight surrounding cells.
* *Constraint*: If there is more than one digit in a cell, the groups of shaded cells have to be separated by at least one unshaded cell
* *Constraint*: Question mark clues represent any nonzero integer.

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