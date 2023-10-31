* The goal of these puzzles is to divide the grid in a certain way to satisfy certain constraints.

### Anraikumazaiku
* *Goal*: Divide the grid into rectangular regions.
* *Constraint*: Each region contains one circle.
* *Constraint*: Black cells do not belong to any region.
* *Constraint*: Regions of the same size do not share an edge.

### Dominion
* *Goal*: Shade some cells in the grid.
* *Constraint*: Shaded cells form dominoes which can touch each other diagonally.
* *Constraint*: Cells with letters are unshaded
* *Constraint*: Cells with the same letter belong to the same region.
* *Constraint*: Unshaded regions must contain at least one letter.

### Dominosa
* *Goal*: Place borders to form dominoes within the grid.
* *Constraint*: The domino numbers are shown on the grid.
* *Constraint*: No domino may repeat.



### FIllomino 
* *Goal*: Divide the grid into polyominoes by filling in the boundaries of the cells (i.e., the edges)
* *Constraint*: Each clue $n$ given is part of a polyomino of size $n$. 
* *Constraint*: No polyominoes of matching size are adjacent to each other (i.e., share a side).
* It is possible for two givens with matching numbers to be part of the same polyomino
* It is possible for a polyomino to have no given at all.

### Fosenzuru
* *Goal*: Divide the grid into regions.
* *Constraint*: The regions must contain exactly four cells.
* *Constraint*: A number in a cell represents how many of its four sides are segment of a region's borders (including the grid's borders).

### Galaxies / Tentai Show
* *Goal*: Draw lines along the edges of the grid to divide the grid into regions representing galaxies
* *Constraints*: All galaxies must have $180\degree$ rotational symmetry.
* *Constraint*: All galaxies contain exactly one dot at its center. The dot, therefore acts as the center of the symmetry

### Kapetto
* *Goal*: Divide the grid into rectangular blocks.
* *Constraint*: Each block contains exactly one number.
* *Constraint*: The numbered clues represent the amount of cells in the block.
* *Constraint*: Cells do not have to belong to a block.

### Knossos
* *Goal*: Divide the grid into rooms.
* *Constraint*: Each region contains exactly one number.
* *Constraint*: The number represents the border's length of the region (sides of the board incident to the region count to the border length)

### Neighbors
* *Goal*: Divide the grid into regions.
* *Constraint*: Region sizes must be the same.
* *Constraint*: Regions contain exactly one number (or question mark).
* *Constraint*: Regions have as many neighbors as their number indicates. Regions are neighbors when they share a part of their border.

### Rekuto
* *Goal*: Divide the grid into rectangular pieces.
* *Constraint*: Each piece contains exactly one number
* *Constraint*: The number in each piece represents the the sum of the width and height of the rectangle

### Renkatsu
* *Goal*: Divide the grid into regions.
* *Constraint*: Each region contains digits $1\dots N$, where $N$ is the number of cells in the region.

### Seethrough
* *Goal*: Every cell denotes a room. Close some doors by placing edges. 
* *Constraint*: Open doors allow looking into other rooms.
* *Constraint*: The number in the cell indicates the total number of rooms visible orthogonally (excluding the room itself)
* *Constraint*: All rooms must be connected (going through doors).
### Shikaku
* *Goal*: Divide the grid into rectangular pieces.
* *Constraint*: Each piece contains exactly one number, and that number represents the area of the rectangle.

### Trinudo
* *Goal*: Divide the grid into blocks.
* *Constraint*: Blocks may be either of one, two or three cells.
* *Constraint*: Blocks of the same size are not orthogonally adjacent.
* *Constraint*: Each given number represents the size of the block to which it belongs.

### Yonmasu
* *Goal*: Divide the grid into regions
* *Constraint*: Regions contain exactly four cells.
* *Constraint*: Each region contains one circle.
* *Constraint*: Black cells are not part of any region.