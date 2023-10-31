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

### Easy as ABC
* *Goal*: Place the letters on the square grid.
* *Constraint*: Letters outside the grid indicate which letter will come across first from that direction.
* *Variant*: Some cells in the solution will be empty. 

### Eulero
 * *Goal*: Fill in the grid with symbols 
 * *Constraint*: Each cell contains one letter and one digit.
 * *Constraint*: Every row and every column contains each letter and each digit exactly once.
 * *Constraint*: No two cells can contain the same pair of symbols.

### Futoshiki
* *Goal*: Place the numbers such that each row and column contains only one of each digits.
* *Constraint*: The inequality symbols that are given must be respected by the cells incident to it.

### Hakyuu
* *Goal*: Each polyomino section (called rooms) must be filled with the numbers $1$ to $n$, where $n$ is the number of cells in the room. 
* *Constraint*: If two identical numbers appear in the same row or column, at least that many cells with other numbers must separate them. (i.e., if two threes appear, they must be at least three apart).

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

### Mathrax
* *Goal*: Fill in each cell with the numbers $1-N$, where $N$ is the puzzle's side.
* *Constraint*: Numbers may not repeat in the rows or columns.
* *Constraint*: A number and a mathematical operation indicates that the number is a result of executing the operation with numbers in diagonally adjacent cells.
* *Constraint*: An "E" in the corner indicates all four cells incident to it have even numbers.
* *Constraint*: An "O" in the corner indicates all four cells incident to it have odd numbers.

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

### Skyscrapers
* *Goal*: Place the numbers $1...N$ on the regular (square) grid. 
* *Constraint*: No number may repeat in any row or column.
* *Constraint*: The numbers along the edge of the puzzle indicate the number of buildings which you would see from that direction if there was a series of skyscrapers with heights equal the entries in that row or column.
* *Variant*: The grid can have a side length of more than $N$, meaning there will be empty cells.

### Str8ts
* *Goal*: Place digits within the white cells.
  
  Black cells separate the grid into compartments (that run purely orthogonally)
* *Constraint*: Each compartment must contain a straight -- a set of consecutive numbers in any order.
* *Constraint*: Each row and column must contain unique digits.
* *Constraint*: Digits in some black cells remove that digit as an option in the row or column, and they do not form part of any straight.

### Suguru
* *Goal*: The grid is partitioned into regions. Fill in the grid with the numbers o from $1$ to the size of the region it belongs to (i.e., its number of cells)
* *Constraint*: Cells with the same digits must not be orthogonally or diagonally adjacent.

### Sutoreto
* *Goal*: Place a number in every white cell on the grid.
* *Constraint*: The numbers in a horizontal or vertical stripe of consecutive white cells must form a sequence of numbers without gaps but in any order.

### Tenner Grid
* *Goal*: Fill the grid so so that every row contains the digits $0-9$ (no repeats). Numbers in the columns may repeat.
* *Constraint*: The numbers at the bottom give the sum of the numbers in the column
* *Constraint*: Digits that are orthogonally or diagonally adjacent must be different.