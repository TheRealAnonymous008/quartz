* The goal of these puzzles is to divide the grid in a certain way to satisfy certain constraints.

### Anraikumazaiku
* *Goal*: Divide the grid into rectangular regions.
* *Constraint*: Each region contains one circle.
* *Constraint*: Black cells do not belong to any region.
* *Constraint*: Regions of the same size do not share an edge.

### Araf
* *Goal*: Divide the grid into regions
* *Constraint*: Each region contains exactly two numbers.
* *Constraint*: The area of each region must be between the two numbers inside it.

### Bodaburokku
* *Goal*: Divide the grid into regions.
* *Constraint*: Cells with the same number belong to the same region.
* *Constraint*: All points where three or four lines meet are given (indicated by dots).
* *Constraint*: Every region contains at least one cell with a number.

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

### Firumatto 
* *Goal:* Divide the grid into rectangular regions.
* *Constraint*: Regions are one cell wide.
* *Constraint*: Regions are o length 1-4 cells.
* *Constraint*: Numbered cells indicate the size of the region.  Not all numbers are given
* *Constraint*: Regions of the same size must not be orthogonally adjacent.
* *Constraint*: Grid dots are not shared by the corners of four regions.

### Fosenzuru
* *Goal*: Divide the grid into regions.
* *Constraint*: The regions must contain exactly four cells.
* *Constraint*: A number in a cell represents how many of its four sides are segment of a region's borders (including the grid's borders).

### Furisuri
* *Goal*:  Locate some regions on the grid
* *Constraint*: Regions are of size $3$.
* *Constraint*: Each block contains one circle.
* *Constraint*: It must be possible to move each block by one cell in at least one orthogonally direction.

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

### Light and Shadow
* *Goal*: Divide the grid into gray and white regions
* *Constraint*: Every region contains exactly one number
* *Constraint*: The region must have the same number of cells as the number it contains
* *Constraint*: Numbers in X colored cells are part of the region of color X
* *Constraint*: Same colored regions cannot share an edge.

### Makaro
* *Goal*: Divide the grid into regions.
* *Constraint*: Each region must be filled with the numbers $1,\dots, N$ where $N$ is the size of the region. 
* *Constraint*: Arrows on cells point to the greatest number among the four cells adjacent to it.
* *Constraint*: Arrows are not part of a region.
* *Constraint*: When two numbers are orthogonally adjacent across a region boundary, the numbers must be different.

### Nawabari
* *Goal*: Divide the grid into rectangular regions.
* *Constraint*: Each region contains exactly one digits.
* *Constraint*: Digits in the cell represent how many sides of the  cell belongs to the border of the region. Edges of the grid are included.

### Neighbors
* *Goal*: Divide the grid into regions.
* *Constraint*: Region sizes must be the same.
* *Constraint*: Regions contain exactly one number (or question mark).
* *Constraint*: Regions have as many neighbors as their number indicates. Regions are neighbors when they share a part of their border.

### Nuribou
* *Goal*: Shade some cells on the grid.
* *Constraint*: The black cells divide the grid in regions of white cells. Each region contains one cell with a number.
* *Constraint*: The number in the region gives the number of cells in the region.
* *Constraint*: Black cells form orthogonal stripes that are not orthogonally adjacent and are exactly one cell wide.
* *Constraint*: If two stripes are connected diagonally, the length of the stripes must be different

### Rekuto
* *Goal*: Divide the grid into rectangular pieces.
* *Constraint*: Each piece contains exactly one number
* *Constraint*: The number in each piece represents the the sum of the width and height of the rectangle

### Renkatsu
* *Goal*: Divide the grid into regions.
* *Constraint*: Each region contains digits $1\dots N$, where $N$ is the number of cells in the region.

### Sashigane
* *Goal*: Divide the grid into L shaped regions.
* *Constraint*: The two legs of the region must be exactly one cell wide.
* *Constraint*: A circle represents which cell in an L must bend. Not all regions have circles
* *Constraint*: An arrow marks the end of the region's leg, pointing to the cell in which the L bends.

### Sashikazune
* *Goal*: Divide the grid into L shaped regions.
* *Constraint*: The two legs of the region must be exactly one cell wide.
* *Constraint*: Each region contains no more than three cells with numbers Some regions may not have numbers
* *Constraint*: Numbers indicate the amount of cells up to a place where the L will bend (including the cell with the number)
* *Constraint* 1's indicate where the L bends.

### Seethrough
* *Goal*: Every cell denotes a room. Close some doors by placing edges. 
* *Constraint*: Open doors allow looking into other rooms.
* *Constraint*: The number in the cell indicates the total number of rooms visible orthogonally (excluding the room itself)
* *Constraint*: All rooms must be connected (going through doors).
### Shikaku
* *Goal*: Divide the grid into rectangular pieces.
* *Constraint*: Each piece contains exactly one number, and that number represents the area of the rectangle.

### Star Battle
* *Goal*: Place stars in some cells in the grid.
* *Constraint*: Each row, column and region contains the same number of stars.
* *Constraint*: Stars cannot be orthogonally or diagonally adjacent.

### Sukima
* *Goal*: Locate some regions on the grid.
* *Constraint*: Each region has three cells.
* *Constraint*: Regions contain one circle.
* *Constraint*: Each $2\times 2$ area has at least one cell that does not belong to any one region.
* *Constraint*: Unshaded cells do not belong to any region.

### Tatamibari
* *Goal*: Divide the grid into rectangular regions.
* *Constraint*: Regions must contain only one symbol.
* *Constraint*: Crosses indicate that the region must be square.
* *Constraint*: Vertical bars indicate the region's height is greater than its width.
* *Constraint*: Horizontal bars indicate the region's width is greater than its height.
* *Constraint*: Grid dots are not shared by he corners of four regions

### Tetroid
* *Goal*: Divide the grid into regions of exactly four cells, forming tetrominoes
* *Constraint*: Tetrominoes can be mirrored or rotated. 
* *Constraint*: Black cells are not part of any tetromino.
* *Constraint*: When two tetrominoes in adjacent regions share an edge, they must not be of the same type.

### Trinudo
* *Goal*: Divide the grid into blocks.
* *Constraint*: Blocks may be either of one, two or three cells.
* *Constraint*: Blocks of the same size are not orthogonally adjacent.
* *Constraint*: Each given number represents the size of the block to which it belongs.

### Usotatami
* *Goal*: Divide the grid into rectangular regions.
* *Constraint*: Regions contain exactly one number.
* *Constraint*: Every region is exactly one cell wide.
* *Constraint*: The number of cells in the region is not equal to the number in the region.
* *Constraint*: Grid dots are not shared by the corners of four regions.

### Yagit
* *Goal*: Divide the grid into regions
* *Constraint*: Each region must be non-empty
* *Constraint*: Each region separates circles (goats) and squares (wolves). Thus, a region must either contain all circles or all squares.
* *Constraint*: Border lines start and end at edges of the grid.
* *Constraint*: Lines can turn but only at the black dots on the grid.
* *Constraint*: Lines can cross each other, except at black dots.
* *Constraint*: Not all black dots need to be used.

### Yonmasu
* *Goal*: Divide the grid into regions
* *Constraint*: Regions contain exactly four cells.
* *Constraint*: Each region contains one circle.
* *Constraint*: Black cells are not part of any region.