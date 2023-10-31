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
* [F-puzzles](https://f-puzzles.com) - for setting your own sudoku puzzles.
* [Logic Puzzles Index](https://www.logic-puzzles.ropeko.ch/php/db/search.php)  - a list of sudoku variants