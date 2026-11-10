🧩 Solving Sudoku with A*, Hill Climbing and Backtracking

A comparison of three classic AI techniques on the same set of Sudoku puzzles, built for an Artificial Intelligence course. The notebook runs every algorithm on identical puzzles, measures how well and how fast each one solves them, and picks a winner from the results.

📂 What's Inside

File| Description
"sudoku_ai_analysis.ipynb"| The full analysis: solvers, experiment, charts and conclusion
"images/"| Chart images used in this README
"README.md"| This file

🧠 Algorithms Compared

Algorithm| Family| Idea
Backtracking| Constraint Satisfaction| Fill cells one by one, undo on conflict
Backtracking + MRV| Constraint Satisfaction| Same, but always fill the cell with the fewest legal values first
A* Search| Informed Search| Expand the board with the lowest "f = g + h"
Hill Climbing| Local Search| Start from a full random guess, keep swapping cells to reduce conflicts

How Each Algorithm Works

- Backtracking: Depth-first assignment with constraint checking. The MRV version picks the most constrained empty cell, so dead ends show up early.
- A* Search: Each state is a partially filled board. "g" is the number of cells filled, and "h" is the sum of legal values across all empty cells. Boards with an empty cell that has no legal value are discarded. The heuristic is not strictly admissible, which is acceptable here because every solution has the same length.
- Hill Climbing: Every 3×3 box is filled with its missing digits at random, so only rows and columns can have duplicates. The cost is the number of duplicate digits across rows and columns. Each move swaps two non-given cells inside one box, and the search stops at a local minimum. It restarts up to 10 times.

📊 Dataset

"Kaggle: 9 Million Sudoku Puzzles and Solutions" (https://www.kaggle.com/datasets/rohanrao/sudoku?select=sudoku.csv)

Dataset file: "sudoku.csv"

The dataset is not included in this repository because of its size. Download it from Kaggle and place "sudoku.csv" in the same folder as the notebook.

To keep loading fast, the notebook reads a random 0.3% of the rows (seeded, so it is reproducible), then draws 60 puzzles from that sample.

Puzzles are split into Easy, Medium and Hard thirds by their number of blank cells.

⚙️ How to Run

1. Install the Requirements

pip install numpy pandas matplotlib jupyter

2. Download the Dataset

Download "sudoku.csv" from the Kaggle link above and place it in the same directory as the Jupyter Notebook.

3. Run the Notebook

Start Jupyter Notebook and execute all cells:

jupyter notebook sudoku_ai_analysis.ipynb

Loading the CSV takes a few seconds. The experiment itself finishes quickly.

🔬 Evaluation Method

The experiment follows a consistent evaluation procedure:

- All algorithms get exactly the same 60 puzzles.
- A run counts as solved only if the final board is a fully valid Sudoku that keeps every given digit.
- For each run, the notebook records the time taken and the number of states explored.
- Algorithms are ranked by success rate first, then by lower average execution time.

📈 Experimental Results

Results from one run of the notebook (random seed 42):

Algorithm| Success Rate| Mean Time (s)| Median Time (s)| Max Time (s)| Mean States Explored
Backtracking| 100%| 0.0051| 0.0008| 0.1835| 720.6
Backtracking + MRV| 100%| 0.0022| 0.0020| 0.0056| 44.2
A*| 100%| 0.0022| 0.0018| 0.0125| 45.7
Hill Climbing| 20%| 0.0300| 0.0307| 0.0625| 3591.7

1. Overall Comparison

"Overall comparison" (images/overall-comparison.png)

Three of the four algorithms solved every puzzle. Hill Climbing solved only 20%.

On the right, the time axis is logarithmic, so each gridline is ten times the one below. Backtracking + MRV and A* are the fastest, plain Backtracking is a little slower, and Hill Climbing is the slowest even though it fails most of the time.

2. Search Effort and Time Spread

"Search effort and time spread" (images/search-effort-and-time-spread.png)

The left chart shows how many states each algorithm had to generate or evaluate.

- MRV and A* need only about 45 states on average.
- Plain Backtracking explores about 720 states.
- Hill Climbing explores approximately 3,600 states.

The right chart shows how much the execution time varies between puzzles, where a short box means the algorithm is predictable.

MRV and A* are tightly grouped. Plain Backtracking has a much wider spread and one extreme case near 0.18 seconds. Hill Climbing is consistently slow because it keeps restarting.

3. Effect of Difficulty

"Effect of difficulty" (images/effect-of-difficulty.png)

Puzzles with more blank cells are harder.

On the left, Hill Climbing falls from roughly half the Easy puzzles to almost none on Medium and none on Hard, while the other three stay at 100%.

On the right, plain Backtracking is actually the quickest on Easy puzzles, but its execution time grows sharply on Hard ones. MRV and A* start slightly slower because they do extra work at every step, then stay almost flat as difficulty rises.

Note: Success rates for Hill Climbing are read from the bars, so they are approximate.

4. Execution Time vs. Number of Blanks

"Time vs number of blanks" (images/time-vs-blanks.png)

Each dot represents one puzzle run.

MRV and A* (teal and orange) rise slowly and stay close together as the number of blank cells increases.

Plain Backtracking (blue) is scattered, mostly fast but with occasional spikes on puzzles with many blanks.

Hill Climbing (red) sits above everything else.

🏆 Conclusion

The experimental results demonstrate the differences in performance among the four implemented approaches.

- A and Backtracking + MRV are effectively tied.* Both solved every puzzle with a mean execution time of approximately 0.0022 seconds and roughly 45 states explored. A* ranks first only because of the tie-break on tiny time differences, so the gap is not meaningful.
- Plain Backtracking is also complete, but it explores far more states and has a much worse worst case (0.18 seconds compared to 0.006 seconds for MRV). The MRV heuristic is what makes it efficient.
- Hill Climbing is incomplete. It gets stuck in local minima where no single swap helps, so its success rate collapses as puzzles get harder.

Sudoku is a Constraint Satisfaction Problem (CSP), so algorithms that use the constraints directly (Backtracking with MRV, or A* with a constraint-based heuristic) are the natural fit.

⚠️ Limitations

- The sample contains only 60 puzzles, so small differences (like A* vs. MRV) can change between runs or sample sizes.
- Backtracking is capped at 50,000 assignments and A* at 3,000 expanded states, so a run that hits the cap counts as unsolved.
- Hill Climbing is randomized, so its results vary with the seed.
- Execution timings depend on the machine on which the experiments are performed.

🛠️ Tech Stack

- Python
- NumPy
- Pandas
- Matplotlib
- Jupyter Notebook

---

<p align="center">
  ✨ Developed as part of an Artificial Intelligence course project ✨
</p>
