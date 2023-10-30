
* Although they usually play in rectangular or square grids, most grid puzzles can generalize to non-rectangular grids.
	* Orthogonal simply means parallel to the edges of the cell.
	* Diagonal simply means a combination of two orthogonal movements.
* Many of these puzzles are published by Nikoli.
# Grid-Based Puzzles
## Doing
### Tenner Grid
### Hundred
### Arrows
### Mathrax
### Straights

### Linesweeper
### Binairo
### Walls
### Dominosa
### Patchwork

### Knossos
### Rekuto
### Neighbors
### Four Winds
### Shakashaka

### Kakurasu
### Mochikoro
### Seethrough
### Lighthouses
### Lighthouses Battleships

## Done
### Akari
* *Goal*: Place light bulbs in white cells and light up the grid.
* *Constraint*: Light bulbs may not shine on each other. Bulbs illuminate in all orthogonal directions. 
* *Constraint*: Light is obstructed by the black cells.
* *Constraint*: Numbers in black cells indicate how many bulbs must be placed adjacent to it. 

### Battleships
* *Goal*: Find the location of all the ships on the grid.
* *Constraint*: Ships do not touch each other. Not even diagonally.
* *Constraint*: Numbers MAY indicate the number of squares in that row or column are occupied by part of a ship.
* *Constraint*: Numbers MAY indicate the number of water segments in the ship

### Calcudoku / Kenken
* *Goal*: Fill the grid with the digits $1$ to $N$, where $N$ is the number of rows or column in the grid.
* *Constraint*: Each row and column contains exactly one of each digit
* *Constraint*: Each bold outlined region of cells contain digits which achieve the specified result using the specified mathematical operation 
* Digits may otherwise repeat within a region.

### Clouds
* *Goal*: Similar to [[#Battleships]]
* *Constraint*: Clouds occupy an area of rectangular shape with width and height of at least two cells.
* *Constraint*: No clouds may touch each other. Not even diagonally.

### Easy as ABC
* *Goal*: Place the letters on the square grid.
* *Constraint*: Letters outside the grid indicate which letter will come across first from that direction.
* *Variant*: Some cells in the solution will be empty. 

### Fill-a-Pix
* *Goal*: Shade some cells on the board. The solved board will form a picture.
* *Constraint*: The cells with clues represent how many of the nine squares around it (including itself) should be filled in.

### FIllomino 
* *Goal*: Divide the grid into polyominoes by filling in the boundaries of the cells (i.e., the edges)
* *Constraint*: Each clue $n$ given is part of a polyomino of size $n$. 
* *Constraint*: No polyominoes of matching size are adjacent to each other (i.e., share a side).
* It is possible for two givens with matching numbers to be part of the same polyomino
* It is possible for a polyomino to have no given at all.

### Futoshiki
* *Goal*: Place the numbers such that each row and column contains only one of each digits.
* *Constraint*: The inequality symbols that are given must be respected by the cells incident to it.

### Galaxies / Tentai Show
* *Goal*: Draw lines along the edges of the grid to divide the grid into regions representing galaxies
* *Constraints*: All galaxies must have $180\degree$ rotational symmetry.
* *Constraint*: All galaxies contain exactly one dot at its center. The dot, therefore acts as the center of the symmetry

### Grand Tour
* *Goal*: Connect the grid of points together to form a single loop.

### Hakyuu
* *Goal*: Each polyomino section (called rooms) must be filled with the numbers $1$ to $n$, where $n$ is the number of cells in the room. 
* *Constraint*: If two identical numbers appear in the same row or column, at least that many cells with other numbers must separate them. (i.e., if two threes appear, they must be at least three apart).

### Hashiwokakero / Hashi
* *Goal*: Connect all islands by drawing a series of bridges between islands.
* *Constraint*: Bridges must begin and end at distinct islands, travelling a straight line in between.
* *Constraint*: Bridges cannot cross other bridges or other islands.
* *Constraint*: Bridges travel straight orthogonally (no diagonal movements).
* *Constraint*: At most two bridges connect a pair of islands.
* *Constraint*: The number of bridges connected to each island must match the clue given on that island.
* *Constraint*: The bridges must connect the islands into a single connected group.

### Heyawake
* *Goal*: Shade some cells in the puzzle. 
* *Constraints*: The grid is divided into variously sized rectangular rooms. 
* *Constraint*: Shaded cells cannot be orthogonally connected, although they can touch diagonally.
* *Constraint*: All unshaded cells form a single connected region.
* *Constraint*: Some rooms contain a single number.
* *Constraint*: A number indicates how many painted cells there are in that room.
* *Constraint*: A room which has no number may contain any number of painted cells or none.
* *Constraint*: Any line of unshaded cells that connects three or more rooms is forbidden. No straight orthogonal line may contain unshaded cells from more than two rooms.

### Hidato
* *Goal*: Fill the grid with consecutive numbers that connect horizontally, vertically or diagonally.
* *Constraint*: The smallest and highest number are presented in the grid. 
	* *Variant*: They may only be given without being presented on the grid.

### Hitori 
* *Goal*: Shade some cells such that there are no duplicate numbers in any row or column. 
* *Constraint*: Shaded cells may not touch each other orthogonally (but they can touch diagonally). 
* *Constraint*: The remaining cells must all be connected to each other orthogonally.

### Kakuro
* *Goal*: Insert the digits one 1-9 into the white cells (like a crossword)
* *Constraint*: Some shaded cells contain clues that pertain to a contiguous run of white cells 
  
  Entries corresponding to a clue must sum to the clue. Top-right clue is for "across". Bottom-left clue is for "down".
* *Constraint*: Clues may not repeat within an entry.
* *Extension*: A given combination of numbers can only be used once in the grid.

### Kuromasu
* *Goal*: Identify which cells on the grid are shaded
* *Constraint*: The numbers on the board represent the number of unshaded cells that can be seen from that cell, including itself.  
* *Constraint*: A cell can be seen from another cell if both cells are within the same row or column, and there are no shaded cells between them in that row or column.
* *Constraint*: Numbered cells are always unshaded.
* *Constraint*: No two shaded cells may be orthogonally adjacent.
* *Constraint*: Unshaded cells must form a connected region.

### Masyu
* *Goal*: Draw a single continuous non-intersecting loop that properly passes through all circled cells.
* *Constraint*: The loop enters each cell it passes through from the center and exits on a different side. In a rectangular grid, all turns are 90 degrees.
* *Constraint*: White circles must be travelled straight through, but the loop must turn in the previous or next cell in its path.
* *Constraint*: Black cells must be turned upon, but the loop must travel straight through the next and previous cells in its path.
* *Variant*: Gray circles which MAY either be white or black. The solver must deduce their color.
* *Variant*: Allowing wrap arounds from the edges of the board.
* *Variant*: The board is divided into regions. The loop must turn in each region at least once.

### Minesweeper
* *Goal*: Place mines into empty cells on the grid.
* *Constraint*: Digits in the grid represent the number of mines in the neighboring cells, including diagonal neighbors.

### Minesweeper Battleships
* *Goal*: Similar to [[#Minesweeper]] but with [[#Battleships]] instead of mines.
* *Constraint*: Clues indicate how many ship pieces are adjacent to it.
* *Constraint*: Ships may not touch each other, not even diagonally.

### Numbrix
* *Goal*: Similar to [[#Hidato]]
* *Constraint*: No diagonal paths allowed.
* *Constraint*: The grid is regular (a square).

### Nurikabe
* *Goal*: Shade some of the cells on the grid to form islands (connected regions of unshaded cells) and the sea (connected regions of shaded cells)
* *Constraint*: Each numbered cell is part of an island. The number in it is the number of cells in that island.
* *Constraint*: Each island contains exactly one numbered cell.
* *Constraint*: There is only one sea.
* *Constraint*: No pools. No $2x2$ areas of only shaded cells.

### Link-A-Pix
* *Goal*: Shade some cells corresponding to lines drawn on the board. The solved board will form a picture
* *Constraint*: The cells with clues are the endpoints of a path and they represent the length of the path containing them (1 clues count as that cell being shaded.)
* *Constraint*: Both endpoints of a path must contain clues. All clues are given.
* *Constraint*: Paths may not cross

### Sashikabe
* *Goal*: Similar to [[#Nurikabe]] but with additional constraints
* *Constraint*: All islands must be L shaped and one cell wide.
* *Constraint*: Islands may not be connected.
* *Constraint*: Arrows mark the end of the island's leg. The arrow points to the cell in which the L "bends". 

### Shikaku
* *Goal*: Divide the grid into rectangular pieces.
* *Constraint*: Each piece contains exactly one number, and that number represents the area of the rectangle.

### Skyscrapers
* *Goal*: Place the numbers $1...N$ on the regular (square) grid. 
* *Constraint*: No number may repeat in any row or column.
* *Constraint*: The numbers along the edge of the puzzle indicate the number of buildings which you would see from that direction if there was a series of skyscrapers with heights equal the entries in that row or column.
* *Variant*: The grid can have a side length of more than $N$, meaning there will be empty cells.

### Slitherlink
* *Goal*: Draw a loop connecting the dots on the grid. There may be no loose ends. 
* *Constraint*: Numbers represent how many of its four sides are segments in the loop

### Tents
* *Goal*: Place tents in some of the remaining squares on the grid.
* *Constraint*: There are exactly as many tents as trees.
* *Constraint*: Tents and trees can be matched up such that each tent is directly orthogonally adjacent to its own tree. A tent may be adjacent to other trees as well as its own.
* *Constraint*: No two tents are adjacent orthogonally or diagonally.
* *Constraint*: The number of tents in each row and column matches the numbers given.

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

### Yajikabe
* *Goal*: Similar to [[#Nurikabe]] except with additional constraints 
* *Constraint*: A cell containing a number and an arrow represents how many unshaded cells are in the row or column pointed at by the arrow in the direction of the arrow.

# Sudoku
* The puzzle is played in a $9\times 9$ grid made of $3\times 3$ sub-grids called regions or blocks. 
* Place the numbers in the empty cells such that each row, column, and region contains  the numbers $1$ to $9$ exactly once. Some numbers are given.

### Adjacency and Board-wide Region Constraints
* **Anti-King** - cells within a king's move in chess must contain different numbers
* **Anti-Knight** - cells within a knight's move in chess must contain different numbers.
* **Battenburg Sudoku** - everywhere 2 odd and 2 even digits form a 2x2 checkerboard pattern, a Battenburg marking is given. 
* **Chains** - The grid consists of a group of circles linked together in chains. The digits $1-9$ appear in each chain exactly once.
* **Disjoint Sets** - the puzzle contains $9$ disjoint groups in the puzzle, one for each relative box position and no repeats may occur within groups. 
	* For example, the cells at position 1 in their boxes form a region and contain distinct digits.
* **Extra Region** - the puzzle contains an additional region.
	* **Dots Sudoku** - the centers of each box forms another region.
	* **Windoku** - contains $4$ additional $3\times 3$ regions. The "frame" of the window consists of R1, R5, R9, and C1, C5, C9. The remaining "panels" are the additional regions.
* **Jigsaw** - regions are no longer $3\times 3$ subgrids, but rather irregular, connected shapes each consisting of $9$ cells. 
* **Nonconsecutive** - orthogonally adjacent digits may not be consecutive.
* **Schrodinger** - place the digits $0-9$ respecting classical and any additional constraints. Two of the digits share a Schrodinger cell. Each row, column or box contains exactly one Schrodinger cell.
* **Unknown Regions** - Regions are no longer $3\times 3$ subgrids. Divide the grid into regions of $9$ orthogonally cells that contain the digits $1-9$. 

### Row/Column/Region Constraints
* **Cages** - No digit can repeat in marked cages.
* **Clone** - cells in a clone must appear in all related clones (for example, all blue clone cells must be $1$). If the clone is more than one cell in size, all instances must be identical.
* **Consecutive Sums** - clues outside the grid indicate the sum of all digits that have at least one consecutive digit as neighbor in the corresponding row or column
* **Descriptive Row / Column** - along row / column X, the digits give the location of X on that column / row 
	* For example a 4 in R4C5 with C5 as the marked column means that R4C4 = 5.  
	* **Descriptive Pairs** - for each pair of clues (X,Y) outside the grid at least one of the following is true: X is in the Yth position from that direction; Y is in the Xth position from that direction 
* **Equal Parities** - within every cage / sub-region, the sum of the odd digits equals the sum of the even digits.
* **Japanese Sums** - shade some cells such that the clues outside the grid indicate the sums of digits in contiguous sets of unshaded cells in the corresponding row or column.
* **Killer** - marked cages MAY specify a number. No number can repeat within cages. Numbers in cages must sum to the specified total
	* **Box Sums** - one marked cell in each 3x3 box contains a digit which is the sum of the other marked cells in that 3x3 box.
* **Little Killer** - numbers are placed outside the grid along with an arrow indicating the diagonal. Digits on the grid along the diagonal sum to the indicated total.
* **Look and Say Cage** - the clue on the cage is read literally. For example if it says "09", then there are "0 nines" in the cage.
* **Offset 1 and 9es** - all digits right below the digit 1 indicate the distance (to the left or right) to the 1 in the corresponding row.. All digits placed right below the 9 indicate the distance to the 9 in the corresponding row
* **Outside Sudoku** - clues appear outside of the grid. These must appear in the first 3 digits of the corresponding row or column (reading from that direction).
	* **Frame** - the numbers outside indicate the sum of the first three digits from that side
	* **Minimax** - numbers are placed outside of the grid. These indicate the sum of the lowest and the highest digits in the first three cells from that side.
* **Polyomino** - divide the grid into polyominos. At least one cell in the polyomino must contain the size of the polyomino.
* **Rank** - a digit "X" in a rank clue means that the digit in the cell is the Xth smallest digit in the corresponding cage.
	* **Full Rank** - a clue is given outside the grid. full rows / columns form $9$-digit numbers read from the direction of the clue and the clue gives the rank with respect to the other numbers.
* **Rossini** - arrows outside the grid indicate that the nearest three digits in the corresponding row are in ascending order (with respect to the arrow).
* **Sandwich** - numbers are placed outside the grid. The number tells you how many digits are "sandwiched" between the $1$ and the $9$.
	* **Double Inverse Sandwich** - clues outside the grid give the sums of the digits that are orthogonally adjacent to either the 1 or 9 in the row or column
* **Skyscraper** - numbers are placed outside the grid. The number tells you how many digits are visible from it. Interpret digits as the heights of skyscrapers. A taller skyscraper obstructs a smaller skyscraper.
	* In other words, it tells you the first immediately visible run of increasing digits.
* **Symmetry** - cells that are symmetric to each other must obey certain properties.
* **X-Sums** - numbers are placed outside the grid. The number tells you the sum of the first $X$ digits where $X$ is the first digit placed along that direction
	* **Parity Counter** - clues outside the grid indicate the sum of the first $N$ digits as seen from that side, where $N$ is equal to the number of even / odd digits
	* **X distance** - digits outside the grid have to be placed in the corresponding row or column in the given order, where the second digit is placed X cells away from the first digit and X is the digit in the first cell of the corresponding row or column.

### Cell and Edge Constraints
* **Difference** - an edge is marked with a dot. Incident cells must differ by this amount.
* **Evens** - cells with gray circles must contain odd digits.
* **Greater Than** - edges may be marked with a $<$ symbol. This symbol points to the cell with the lower digit.
* **Kropki Black** - cells separated by black dots must have a ratio of $1:2$. 
* **Kropki White** - cells separated by white dots must contain a difference of $1$.
* **LC Clues** - numbers are formed by reading left-to-right / top-to-bottom. L clues separate two numbers summing to 50. C clues separate two numbers summing to 100.
* **Mathdoku** - edge clues pertain to mathematical operators applied to cells incident to it. Constraints are applied based on these mathematical operators.
* **Maximum** - a cell is marked as maximum, in which case neighboring cells must be smaller than it.
* **Minimum** - a cell is marked as minimum, in which case neighboring cells must be larger than it.
* **Odds** - cells with gray squares must contain even digits.
* **Quads** - digits(s) within a Quad Clue (which occurs at the corners) indicate that the digit(s) must appear in one of the four neighboring cells.
	* **Group Sum** - the number in the Quad Clue instead, indicates the sum of the digits in the clue
* **Ratio** - an edge is marked with a dot. Incident cells must be in this ratio.
* **Self-Referential Cells** - the value of the cell gives the number of self-referential cells with that value 
	* For example, there must be if the cell is $5$, there are $5$ self-referential cells that have a value of $5$. 
* **XV clues** - Cells separated by a V sum to 5. Cells separated by an X sum to 10. Cells separated by an XV sum to 15.

### Line Constraints
* **10-Line** - the line consists of one or more contiguous groups of cells, each of which sums to 10.
* **Anti-Diagonal** - cells on each major diagonal has at most three different digits.
* **Anti-Factor** - if the line has length $n$, digits may not be any multiple or factor of $n$ other than 1. 
* **Argyle / Diagonals** - marked diagonals must contain no-repeats. The most common variant of this is using the 9-length diagonal(s) of the grid.
* **Arrows** - cells along the arrow must sum to the number in the bulb of the arrow. 
	* **Double Arrows** - the sum of the digits on a line equal to the sum of the two digits in the circles connected by that line
* **Between** - digits on the line are between the values in the marked ends.
* **Chinese Whispers** - digits differ by at most $2$
* **Dutch Whispers** - digits by at least $4$
* **Entropic** - a set of three sequential cells along the line must contain a low (1,2,3),  middle (4,5,6), and high (7,8,9) digit
* **Gemma** - digits must not repeat. For each digit, the counter-digit $10-X$ must also appear on the line.
* **German Whispers**  - digits  differ by at most $5$.
* **Modular** - every set of three sequential digits along the line must contain a digit from (1,4,7), one from (2,5,8) and one from (3,6,9).
* **Nabner** - no two digits on the line may not be consecutive.
* **Region Sum** - Each line segment within a different $3\times 3$ box must sum to the same total.
	* If the line passes through a box twice, each "pass through" counts as separate line segments. 
* **Renban** - digits form a set of non-repeating consecutive digits in any order.
* **Palindrome** - digits read the same forward and backward.
* **Parity** - adjacent digits must alternate in parity (even/odd)
* **Same Difference** - each pair of adjacent digits on this line has the same difference
* **Thermometer** - cells along the thermo increase starting from the bulb end.

### Meta Constraints
* **Dense Fog** - cells are obscured by fog which hides clues on the grid. Placing the correct digit on a cell will reveal only that cell.
* **Fog** - cells are obscured by fog which hides clues on the grid. Placing the correct digit will reveal orthogonally adjacent cells.
* **Negative Constraint** - all possible clues are given in the grid.
* **Unknown Clues** - some numerical clues may be marked with a ? which indicate it is unknown
* **Value Change** - digits may stand for symbols that have different values when operated on numerically
	* For example, a 1 may count as a 2 in a Killer Cage.
* **Wrogn Clues** - a number of the clues in the grid are wrogn -- that is, they are incorrect clues. 

# Links
* [Cracking the Cryptic](https://www.youtube.com/@CrackingTheCryptic) - really good channel that solves (primarily) variant sudoku and cryptic crosswords.
* [Cross+A](https://www.cross-plus-a.com/puzzles.htm) - website with a typology of logic puzzles. Main source for other non-sudoku variants. 
* [F-puzzles](https://f-puzzles.com) - for setting your own sudoku puzzles.
* [Logic Puzzles Index](https://www.logic-puzzles.ropeko.ch/php/db/search.php) - 