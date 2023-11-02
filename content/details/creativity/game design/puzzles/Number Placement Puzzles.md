* The general goal is to place numbers on the grid. To distinguish from [[Object Placement Puzzles]], these puzzles exploit properties of numbers (ordering, arithmetic, etc...)

### Binairo / Taukuzu
* *Goal*: Fill the grid with the digits "0" and "1".
* *Constraint*: There are as many "1"s as digits "0"s in every row and every column (or one more for odd-sized grids).
* *Constraint*: No more than two of either number are adjacent to each other
* *Constraint*: There are no identical rows and columns.

### Bricks
* *Goal*: Fill each cell with the numbers $1\dots N$ where $N$ is the puzzle size.
* *Constraint*: No number may appear twice in any row or column.
* *Constraint*: Bricks contain one odd and one even number

### Calcudoku / Kenken
* *Goal*: Fill the grid with the digits $1$ to $N$, where $N$ is the number of rows or column in the grid.
* *Constraint*: Each row and column contains exactly one of each digit
* *Constraint*: Each bold outlined region of cells contain digits which achieve the specified result using the specified mathematical operation 
* Digits may otherwise repeat within a region.

### Different Neighbors
[^different_neighbors]: This is an application of the [[Graph Coloring|Four Color Theorem]]

* *Goal*: Place a number from 1-4 on each region.
* *Constraint*: No two orthogonally or diagonally adjacent digits share the same digit [^different_neighbors]

### Doppelblock
* *Goal*: Shade some cells on the grid.
* *Constraint*: Every row and column contains exactly two shaded cells.
* *Constraint*: Unshaded cells contain numbers from $1,\dots,N-2$, where $N$ is the puzzle size 
* *Constraint*: Each number appears once in every row and column.
* *Constraint*: Numbers outside the grid show the sums of the numbers between two black cells in the row or column.

### Easy as ABC
* *Goal*: Place the letters on the square grid.
* *Constraint*: Letters outside the grid indicate which letter will come across first from that direction.
* *Variant*: **Empty** Some cells in the solution will be empty. 
* *Variant*:  **Not as Easy**. 
	* Fill in the first letters of the alphabet on every row and column exactly once.
	* Numbers outside the grid indicate what position you come across this letter  when looking from that side.
	* Some cells will be empty.

### Eulero
 * *Goal*: Fill in the grid with symbols 
 * *Constraint*: Each cell contains one letter and one digit.
 * *Constraint*: Every row and every column contains each letter and each digit exactly once.
 * *Constraint*: No two cells can contain the same pair of symbols.

### Factorism
* *Goal*: Place the numbers from $1\dots N$ where $N$ is the board size. The numbers are placed at the edges of the grid.
* *Constraint*: Numbers on the grid correspond to the product of the number in the corresponding row and column.

### From 1 to X
* *Goal*: Place the numbers $1\dots N$, where $N$ is the size of the region.
* *Constraint*: Same numbers are not orthogonally adjacent.
* *Constraint*: Numbers outside the grid show the sums of the numbers in the corresponding row or column.

### Futoshiki
* *Goal*: Place the numbers such that each row and column contains only one of each digits.
* *Constraint*: The inequality symbols that are given must be respected by the cells incident to it.

### Grades
* *Goal*: Place numbers in some cells of the grid.
* *Constraint*: Numbered cells cannot touch orthogonally or diagonally
- *Constraint*: The numbers on the top and left equal the number of numbered cells.
- *Constraint*: The numbers on the bottom and right are the sums of numbers in the rows and columns.

### Hakyuu
* *Goal*: Each polyomino section (called rooms) must be filled with the numbers $1$ to $n$, where $n$ is the number of cells in the room. 
* *Constraint*: If two identical numbers appear in the same row or column, at least that many cells with other numbers must separate them. (i.e., if two threes appear, they must be at least three apart).

### Hanare
* *Goal*: Place a number in each region of the grid.
* *Constraint*: A number is equal to the size of the region.
* *Constraint*: The distance between two numbers that see each other orthogonally equals the difference of these two numbers 
### Hidato
* *Goal*: Fill the grid with consecutive numbers that connect horizontally, vertically or diagonally.
* *Constraint*: The smallest and highest number are presented in the grid. 
	* *Variant*: They may only be given without being presented on the grid.

### Hundred
* *Goal*: Fill additional digits in the cells such that the sum of numbers in each row and each column equals $100$.

### Kakuro
* *Goal*: Insert the digits one 1-9 into the white cells (like a crossword)
* *Constraint*: Some shaded cells contain clues that pertain to a contiguous run of white cells 
  
  Entries corresponding to a clue must sum to the clue. Top-right clue is for "across". Bottom-left clue is for "down".
* *Constraint*: Clues may not repeat within an entry.
* *Extension*: A given combination of numbers can only be used once in the grid.

### Kojun
* *Goal*: Place the numbers $1,\dots,N$ where $N$ is the number of cells in the region.
* *Constraint*: When two numbers are orthogonally adjacent, the numbers must be different
* *Constraint*: The upper number of two numbers in the same region must be greater than the lower number.

### Mathrax
* *Goal*: Fill in each cell with the numbers $1-N$, where $N$ is the puzzle's side.
* *Constraint*: Numbers may not repeat in the rows or columns.
* *Constraint*: A number and a mathematical operation indicates that the number is a result of executing the operation with numbers in diagonally adjacent cells.
* *Constraint*: An "E" in the corner indicates all four cells incident to it have even numbers.
* *Constraint*: An "O" in the corner indicates all four cells incident to it have odd numbers.

### Meandering Numbers
* *Goal*: Fill each region with the digits $1,\dots,N$ where $N$ is the size of the region.
* *Constraint*: Cells with the same digit are not orthogonally or diagonally adjacent.
* *Constraint*: Consecutive numbers within the region are orthogonally adjacent.
### Nanbaboru
* *Goal*: Fill some cells with numbers from the given range.
* *Constraint*: No number appears twice in any row or column
* *Constraint*: Circles must contain numbers
* *Constraint*: Crosses must not contain numbers.

### Nanro
* *Goal*: Fill in some cells with numbers
* *Constraint*: All numbers in the region must be the same.
* *Constraint*: The given number in a region denotes how many cells in this region contain a number.
* *Constraint*: All regions contain at least one number.
* *Constraint*: When two numbers are orthogonally adjacent across a region boundary, the numbers must be different.
* *Constraint*: No pools. No $2\times 2$ area contains only numbered digits.
* *Constraint*: All cells with numbers form one orthogonally continuous region.

### Number Chain
* *Goal*: Draw a single continuous line from the upper left to the lower right.
* *Constraint*: The line includes each number from $1\dots N$ exactly once.

### Numbrix
* *Goal*: Similar to [[#Hidato]]
* *Constraint*: No diagonal paths allowed.
* *Constraint*: The grid is regular (a square).

### Patchwork / Tatami
* *Goal*: The grid is divided into regions. Fill in the numbers.
* *Constraint*: Each region must be filled with each of the numbers from 1 to the number of cells in the room.
* *Constraint*: Every row and every  column must contain the same amount of each number. 
* *Constraint*: Same digits must not be orthogonally adjacent.

### Renban
* *Goal*: Fill in each cell in the grid with $1,\dots,N$ where $N$ is the size of the grid.
* *Constraint*: No number may appear twice in any row, column or region.
* *Constraint*: All numbers in a region must form a sequence of consecutive numbers in any order.

### Shingoki
* *Goal*: Draw a single continuous non-intersecting loop
* *Constraint*: The loop must pass through all circles.
* *Constraint*: The loop turns on a black circle.
* *Constraint*: The loop travels straight through a white circle.
* *Constraint*: The loop may or may not turn on a gray circle.
* *Constraint*: If a circle contains a number, the number indicates the total length of the straight lines going out of the circle.

### Sign In
* *Goal*: Fill in each cell with the numbers $1\dots N$ where $N$ is the size of the puzzle.
* *Constraint*: Numbers cannot repeat in each row and column.
* *Constraint*: Cells with consecutive numbers are separated with either $+$ or $-$. 
* *Constraint*: No other consecutive numbers exist in the grid.
* *Constraint*: If a border between cells contains a $+$, a digit in the left or upper cell is one lower than a digit on the right or lower cell.
* *Constraint*: If a border between cells contains a $-$, a digit in the left or upper cell is one higher than a digit on the right or lower cell.

### Skyscrapers
* *Goal*: Place the numbers $1...N$ on the regular (square) grid. 
* *Constraint*: No number may repeat in any row or column.
* *Constraint*: The numbers along the edge of the puzzle indicate the number of buildings which you would see from that direction if there was a series of skyscrapers with heights equal the entries in that row or column.
* *Variant*: **Empty Cells** The grid can have a side length of more than $N$, meaning there will be empty cells.
* *Variant*: **Sums**. Numbers outside the grid indicates the sum of the heights of the visible buildings.

### Str8ts
* *Goal*: Place digits within the white cells.
  
  Black cells separate the grid into compartments (that run purely orthogonally)
* *Constraint*: Each compartment must contain a straight -- a set of consecutive numbers in any order.
* *Constraint*: Each row and column must contain unique digits.
* *Constraint*: Digits in some black cells remove that digit as an option in the row or column, and they do not form part of any straight.

### Suguru
* *Goal*: The grid is partitioned into regions. Fill in the grid with the numbers o from $1$ to the size of the region it belongs to (i.e., its number of cells)
* *Constraint*: Cells with the same digits must not be orthogonally or diagonally adjacent.

### Sukrokuro
* *Goal*: Fill in the numbers in the white cells.
* *Constraint*: [[Sudoku]] rules. Digits 1-9 must be placed on white cell with no repeats. 
* *Constraint*: [[#Kakuro]] rules apply. These clues give the sum of numbers in consecutive cells right or downward
* *Constraint*: Kropki rules apply. Digits separated by a white dot are consecutive. 
* *Constraint*: All Kropki dots are given.

### Sutoreto
* *Goal*: Place a number in every white cell on the grid.
* *Constraint*: The numbers in a horizontal or vertical stripe of consecutive white cells must form a sequence of numbers without gaps but in any order.

### Tenner Grid
* *Goal*: Fill the grid so so that every row contains the digits $0-9$ (no repeats). Numbers in the columns may repeat.
* *Constraint*: The numbers at the bottom give the sum of the numbers in the column
* *Constraint*: Digits that are orthogonally or diagonally adjacent must be different.

### Terra X
* *Goal*: Place digits from $0,\dots,9$ into each region once
* *Constraint*: Regions with the same number cannot share an edge. They may touch at corners.
* *Constraint*: For each grid point where four regions meet, the sum of the digits equal ten. Grid points are marked on the grid.
### Yakazu
* *Goal*: Fill the white cells with numbers.
* *Constraint*: Compartments are runs of white cells going orthogonally. Compartments must contain consecutive numbers but in any order.
* *Constraint*: Compartments must contain the number 1. 

### Yin-Yang
* *Goal*: Place a black or white circle in each empty cell.
* *Constraint*: Cells with black circles form an orthogonally connected region.
* *Constraint*: Cells with white circles form an orthogonally connected region.
* *Constraint*: No pools. No $2\times 2$ group of cells contain circles of the same color.

