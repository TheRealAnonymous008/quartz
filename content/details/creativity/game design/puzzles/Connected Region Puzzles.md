* A subtype of [[Partitioning Puzzles]] where we must find one contiguous region of cells.

### Creek
* *Goal*: Shade some cells on the grid.
* *Constraint*: Clues at the corners of the grid indicate how many adjacent cells are shaded.
* *Constraint*: Unshaded cells must be connected horizontally or vertically 

### Fobidoshi
* *Goal*: Place circles into empty cells.
* *Constraint*: All circles form an orthogonally connected area
* *Constraint*: Lines of connected circles must not contain more than $3$ circles.

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

### Island
* *Goal*: Shade some cells in the grid.
* *Constraint*: Unshaded cells form a single island. Each numbered cell is a part of this island.
* *Constraint*: Numbers indicate how many unnumbered white cells can be reached by moving orthogonally.
* *Constraint*: Numbered cells block access from one another.

### Nurikabe
* *Goal*: Shade some of the cells on the grid to form islands (connected regions of unshaded cells) and the sea (connected regions of shaded cells)
* *Constraint*: Each numbered cell is part of an island. The number in it is the number of cells in that island.
* *Constraint*: Each island contains exactly one numbered cell.
* *Constraint*: There is only one sea.
* *Constraint*: No pools. No $2x2$ areas of only shaded cells.

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

### Yajikabe
* *Goal*: Similar to [[#Nurikabe]] except with additional constraints 
* *Constraint*: A cell containing a number and an arrow represents how many unshaded cells are in the row or column pointed at by the arrow in the direction of the arrow.