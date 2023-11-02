* The general goal is to place an object on the grid (or outside of it). Not all cells have to have that object.

### Battleships
* *Goal*: Find the location of all the ships on the grid.
* *Constraint*: Ships do not touch each other. Not even diagonally.
* *Constraint*: Numbers MAY indicate the number of squares in that row or column are occupied by part of a ship.
* *Constraint*: Numbers MAY indicate the number of water segments in the ship
* *Variant*: **Clouds**. Ships are now rectangular in shape, with width and height of at least two cells.
* *Variant*: **Digital Battleships** Grid contains numbers. Values on the right and bottom edges reveal the sum of the numbers in each ship piece that appears in the respective row or column.

### Dosun-Fuwari
* *Goal*: Place one black and one white circle in each region.
* *Constraint*: White circles (Balloons) must be placed either 
	* Into the top cell of the grid 
	* Into the cell right under black cells on the grid
	* Under other white circles.
* *Constraint*: Black circles (Iron balls) must be placed either
	* Into the bottom cell of the grid.
	* On the cell right over black cells on the grid.
	* Over other black circles.

### Gappy
* *Goal*: Shade some cells on the grid.
* *Constraint*: Each row and column contains exactly two shaded cells.
* *Constraint*: Shaded cells cannot touch each other orthogonally or diagonally.
* *Constraint*: Numbers outside the grid show the number of white cells between black cells in the corresponding row or column.

### Gokigen Naname
* *Goal*: Fill in a diagonal line in every cell.
* *Constraint*: Numbers in circled clues at grid points equal the number of lines extending from that circle.
* *Constraint*: Diagonal lines do not form closed loops.

### Hamusando
* *Goal*: Fill the grid with squares (toasts) and circles (hams).
* *Constraint*: Every row and column contains two squares and $N$ circles ($N$ is given).
* *Constraint*: A number at the edge of the grid indicates how many hams must be placed between the two toasts.

### Kakurasu
* *Goal*: Color some of the cells to satisfy the clues
* *Constraint*: Numbers on the top and left sides give the totals for the black squares based on their value reading in that direction
* *Constraint*: Numbers on the bottom and right side  give the value of the cells from that direction 
	* So that, for example, clues on the top give sums along columns. The values used are those specified on the right side of the grid (which go down along columns).

### Minesweeper
* *Goal*: Place mines into empty cells on the grid.
* *Constraint*: Digits in the grid represent the number of mines in the neighboring cells, including diagonal neighbors.
* *Variant*: **Minesweeper Battleships** - mines are replaced with battleships. Clues indicate how many ship pieces are adjacent to it. 
	* Ships may not touch each other, not even diagonally.
* *Variant*: **Double Minesweeper** - place mines into each empty cell in the grid.

### Mobiriti
* *Goal*: Shade some cells on the grid.
* *Constraint*: Cells with circles cannot be shaded.
* *Constraint*: Numbers indicate how many empty cells can be reached from that cell moving orthogonally and without jumping over circled cells, blacked cells or itself.

### Number Cross
* *Goal*: Shade some cells.
* *Constraint*: Numbers outside the grid show the sums of the numbers in white cells in the corresponding row or column.

### Retrograde Battleships
* *Goal*: Place the ships on the grid similar to [[#Battleships]]
* *Constraint*: No ship may touch another orthogonally or diagonally/
* *Constraint*: Ship segments are given and must be respected.

### SquarO
* *Goal*: Identify which of the circles on the grid points are black.
* *Constraint*: Numbers on the cell indicate how many of the four surrounding dots are black.

### Star Battle
* *Goal*: Place stars in some cells in the grid.
* *Constraint*: Each row, column and region contains the same number of stars.
* *Constraint*: Stars cannot be orthogonally or diagonally adjacent.

### Tents
* *Goal*: Place tents in some of the remaining squares on the grid.
* *Constraint*: There are exactly as many tents as trees.
* *Constraint*: Tents and trees can be matched up such that each tent is directly orthogonally adjacent to its own tree. A tent may be adjacent to other trees as well as its own.
* *Constraint*: No two tents are adjacent orthogonally or diagonally.
* *Constraint*: The number of tents in each row and column matches the numbers given.

### Tren
* *Goal*: Locate some blocks in the grid. Blocks correspond to "cars".
* *Constraint*: Blocks are either $1\times 2$ or $1\times 3$ in dimension.
* *Constraint*:  Each numbered cell is a part of a block.
* *Constraint*: Numbers indicate the amount of possible moves of the block. 
* *Constraint*: Blocks only move in the direction of their short edge.
* *Variant*: **Tren+**
	- Each block contains exactly one number or a question sign (unknown number), indicating the amount of its possible movements.
	- All cells that are not part of any block must be connected horizontally or vertically.
- *Variant*: **Ghost Tren**
	- Blocks can also be placed without any numbers, with no restrictions on their ability to move.
	- All cells that are not part of any block must be connected horizontally or vertically.

### Walls
* *Goal*: Place a single orthogonal line in every blank cell.
* *Constraint*: A number in a black cell indicates the total length of the segments connected to that square.

