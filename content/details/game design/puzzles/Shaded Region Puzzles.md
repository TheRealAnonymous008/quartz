* Similar to [[Object Placement Puzzles]] but where we shade areas in the grid. Areas are defined as containing possibly more than one cell.
* Typically shaded areas form regions that satisfy certain properties but distinct from [[Partitioning Puzzles]] where the color of the region is important.
* Overlaps with [[Connected Region Puzzles]] but here we do not require regions to be connected.
* Shading is not required. The spirit is to "mark" cells with a color.

### Akiperago
* *Goal*: Shade some cells in the grid
* *Constraint*: The black cells form "islands". No two islands may share an edge. Islands may be connected through their corners.
- *Constraint*: If an island contains a numbered cell, this number represents the amount of black cells in the island. 
- *Constraint*: An island may contain few numbered cells (all numbers will be the same inside an island).
- *Constraint*: All islands form "archipelagos". An archipelago is a group of two or more islands, connected through their corners.
- *Constraint*: If an archipelago contains N islands, they will be from 1 to N cells (not necessarily in that order)

### Chiyotsui
* *Goal*: Shade some cells in the grid.
* *Constraint*: Black cells form areas. Each area spans exactly two regions.
* *Constraint*: The black areas are symmetrical with respect to a region border.
* *Constraint*: Cells with a number indicate how many cells in the region must be shaded.
* *Constraint*: No two black areas may share an edge.

### Choco banana
* *Goal*: Shade some cells on the grid.
* *Constraint*: Areas of black cells form a rectangle or square.
* *Constraint*: Areas of white cells must not form rectangular regions.
* *Constraint*: Numbers indicate area sizes.
* *Constraint*: An area may contain more than one cell with a number.

### Chocona
* *Goal*: Shade some cells in the grid
* *Constraint*: A cell with a number indicates how many cells in the region must be shaded.
* *Constraint*: Regions without numbers mean any number of cells may be blackened
* *Constraint*: Black cells must form rectangles independent of region borders.
* *Constraint*: Black rectangles are not orthogonally adjacent.
### Dominion
* *Goal*: Shade some cells in the grid.
* *Constraint*: Shaded cells form dominoes which can touch each other diagonally.
* *Constraint*: Cells with letters are unshaded
* *Constraint*: Cells with the same letter belong to the same region.
* *Constraint*: Unshaded regions must contain at least one letter.

### Fill-a-Pix
* *Goal*: Shade some cells on the board. The solved board will form a picture.
* *Constraint*: The cells with clues represent how many of the nine squares around it (including itself) should be filled in.

### Kapama
* *Goal*:  Shade some cells
* *Constraint*: Create pairs of figures called twin shapes. Twin shapes are symmetrical with respect to the indicated diagonal line.
* *Constraint*: No shape may share an edge.
* *Constraint*: Cells with diagonal lines cannot be shaded.
* *Constraint*: Numbers indicate the number of black cells in the corresponding row or column
* *Variant*: **Sunglasses** - adds bridges which are not necessarily diagonal lines, and may be of any length. Twin shapes must be symmetrical with respect to the bridges. Bridges are never shaded.

### Kuroclone
* *Goal*: Shade some cells on the grid
* *Goal*:  Each region must contain two areas of black cells.
* *Constraint*: Cells with numbers are always white.
* *Constraint*: Area pairs are of the same size and shape, potentially rotated or mirrored
* *Constraint*: Arrows in cells point to adjacent cells that belong to a black area.
* *Constraint*: Numbers in cells pertain to the size of the area pointed to by the arrow.
* *Constraint*: When two cells are orthogonally adjacent across region boundaries, at least one must be white.

### Light and Shadow
* *Goal*: Divide the grid into gray and white regions
* *Constraint*: Every region contains exactly one number
* *Constraint*: The region must have the same number of cells as the number it contains
* *Constraint*: Numbers in X colored cells are part of the region of color X
* *Constraint*: Same colored regions cannot share an edge.

### Link-A-Pix
* *Goal*: Shade some cells corresponding to lines drawn on the board. The solved board will form a picture
* *Constraint*: The cells with clues are the endpoints of a path and they represent the length of the path containing them (1 clues count as that cell being shaded.)
* *Constraint*: Both endpoints of a path must contain clues. All clues are given.
* *Constraint*: Paths may not cross

### Miraringutairu
* *Goal*: Locate blocks of black cells in the grid.
* *Constraint*: Numbered cells indicate the total number of black cells in the block 
* *Constraint*: Blocks do not have to contain numbers.
* *Constraint*: Blocks cannot share edges.
* *Constraint*: Each block must be connected to another block of the same size and shape through their corners, subject to rotation or reflection.

### Mochikoro
* *Goal*: Shade some cells on the grid.
* *Constraint*: Shaded cells divide the grid into rectangular islands of unshaded cells.
* *Constraint*: Islands cannot share edges, but they must be connected diagonally via their corners
* *Constraint*: Islands must have the same number of  cells as the number it contains.
* *Constraint*: No pools. No $2x2$ areas must contain only shaded cells

### No Four in a Row
* *Goal*: Fill the grid with symbols.
* *Constraint*:  Four consecutive symbols never appear in any row, column, or diagonal.

### Nondango
* *Goal*: Shade some circles on the grid.
* *Constraint*: Each region contains one black circle.
* *Constraint*: Three consecutive circles of of the same color never appear in any orthogonal or diagonal direction. There must be a circle of the other color or an empty cell between them.

### Norinori
* *Goal*: Shade some cells in the grid
* *Constraint*: Every region contains exactly two black cells.
* *Constraint*: Each block must be a part of a domino, irrespective of region borders.
* *Constraint*: No two dominoes may share an edge. They can touch diagonally.

### Nuribou
* *Goal*: Shade some cells on the grid.
* *Constraint*: The black cells divide the grid in regions of white cells. Each region contains one cell with a number.
* *Constraint*: The number in the region gives the number of cells in the region.
* *Constraint*: Black cells form orthogonal stripes that are not orthogonally adjacent and are exactly one cell wide.
* *Constraint*: If two stripes are connected diagonally, the length of the stripes must be different

### Santoitchi
* *Goal*: Shade some cells in the grid
* *Constraint*: Numbered cells must not be shaded.
* *Constraint*: All white cells must be divided on regions having the size of exactly three cells.
- *Constraint*: Two black cells must not be orthogonally adjacent.
- *Constraint*: Each region contains a number.
- *Constraint*: A number indicates how many black cells share an edge with that region.

### Shakashaka
* *Goal*: Place triangles in some of the white cells.
* *Constraint* The white parts of the grid (that do not have black triangles) must form rectangular regions.
* *Constraint*: Black cells with a number must be orthogonally adjacent to the specified number of black triangles.

### Shimaguni
* *Goal*: Shade some cells in the grid.
* *Constraint*: All black cells in a region must be connected.
- *Constraint*: A cell with a number indicates how many cells in the region must be shaded.
- *Constraint*: In regions without a number at least one cell must be shaded.
- *Constraint*: Two regions with the same amount of shaded cells must not be orthogonally adjacent.
- *Constraint*:: When two cells are orthogonally adjacent across a region boundary, at least one cell must be unshaded.

### Starry Night
* *Goal*: Place one white circle (sun), one black circle (moon) and one star in every row and column of the grid.
* *Constraint*: Same figures may not touch each other diagonally.
* *Constraint*: Figures outside indicate the distance between the star and circles in that row or column.
	* White circle indicates the sun is closer to the star than the moon.
	* Black circle indicates the moon is closer to the star than the sun.
	* A star indicates that both sun and moon are equidistant.

### Stostone
* *Goal*: Shade some cells (i.e., place stones on the grid)
- *Constraint*: All black cells in a region must be connected horizontally or vertically.
- *Constraint*: A cell with a number indicates how many cells in the region must be blackened.
- *Constraint*: In regions without a number any amount of cells may be blackened (at least one).
- *Constraint*: When two cells are orthogonally adjacent across a region boundary, at least one cell must be white.
- *Constraint*: If all stones "fall down", they must cover exactly the bottom half of the grid.

### Tairupeinto
* *Goal*: Shade some cells on the grid.
* *Constraint*: Each region is either completely filled or completely empty.
* *Constraint*: Numbers outside the grid indicate the number of shaded cells in that direction.

### Trilogy
* *Goal*: Fill the grid with figures.
* *Constraint*: Consecutive figures must not be all the same or all different in any row column or diagonal.

### Trinairo
* *Goal*: Fill the grid with letters so that each row and column has three A's, three B's and three C's.
* *Constraint*: Marked cells have their letters differ from all other orthogonally adjacent cells.

### Triplets
* *Goal*: Fill each square with figures (square, circle, triangle)
* *Constraint*: Regions must either contain all identical or all different figures.
* *Constraint*: When two figures are orthogonally adjacent across a region boundary, the figures must be different.

### Water Fun
* *Goal*: Fill the grid with water
* *Constraint*: Numbers outside the grid show how many cells of each row and column are filled with water.
* *Constraint*: Connected areas of filled cells must have the same level of water everywhere
