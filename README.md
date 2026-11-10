
# 🧩 Solving Sudoku with A*, Hill Climbing and Backtracking

A comparison of classic Artificial Intelligence search algorithms applied to Sudoku puzzles. This project explores how different search strategies solve the same set of Sudoku puzzles by evaluating their success rates, execution times, and search efficiency.

## ✨ Project Overview

The project implements and compares four search approaches:

- **Backtracking Search** – Solves Sudoku by assigning values one cell at a time and backtracking whenever a constraint is violated.
- **Backtracking with MRV** – Improves Backtracking by selecting the cell with the Minimum Remaining Values first.
- **A* Search** – Uses an evaluation function `f(n) = g(n) + h(n)` to prioritize promising search states.
- **Hill Climbing** – Uses local search and iterative swapping to minimize conflicts in Sudoku boards.

The objective is to investigate how different AI algorithms perform when solving Sudoku puzzles of varying difficulty.

## 📁 Repository Structure

```text
Sudoku-AI-Project/
│
├── sudoku_ai_analysis.ipynb
├── sudoku.csv
├── images/
│   ├── overall-comparison.png
│   ├── search-effort-and-time-spread.png
│   ├── effect-of-difficulty.png
│   └── time-vs-blanks.png
│
└── README.md
```

## 📊 Dataset

**Dataset:** [9 Million Sudoku Puzzles and Solutions – Kaggle](https://www.kaggle.com/datasets/rohanrao/sudoku?select=sudoku.csv)

The project uses the `sudoku.csv` dataset containing Sudoku puzzles and their corresponding solutions.

To make the experiment computationally manageable:

- A random 0.3% sample of the dataset is selected.
- A total of 60 puzzles are used for evaluation.
- A fixed random seed ensures reproducibility.
- Puzzles are categorized into Easy, Medium, and Hard based on the number of blank cells.

**Note:** Download `sudoku.csv` from Kaggle and place it in the same directory as the Jupyter Notebook.

## ⚙️ Technologies & Libraries

- Python
- NumPy
- Pandas
- Matplotlib
- Jupyter Notebook

## 🚀 Installation & Execution

**1. Clone the repository**

```bash
git clone <your-repository-url>
cd Sudoku-AI-Project
```

**2. Install the required libraries**

```bash
pip install numpy pandas matplotlib jupyter
```

**3. Download the dataset**

Download `sudoku.csv` from Kaggle and place it in the project directory.

**4. Launch Jupyter Notebook**

```bash
jupyter notebook sudoku_ai_analysis.ipynb
```

**5. Run all cells**

Execute all notebook cells to perform the experiments, generate visualizations, and compare algorithm performance.

## 📈 Experimental Results

The following results were obtained from one experimental run using random seed 42.

| Algorithm | Success Rate | Mean Time (s) | Mean States Explored |
|---|---:|---:|---:|
| Backtracking | 100% | 0.0051 | 720.6 |
| Backtracking + MRV | 100% | 0.0022 | 44.2 |
| A* Search | 100% | 0.0022 | 45.7 |
| Hill Climbing | 20% | 0.0300 | 3591.7 |

### 📉 Performance Visualizations

**1. Overall Algorithm Comparison**

![Overall Comparison](images/overall-comparison.png)

**2. Search Effort and Execution Time Distribution**

![Search Effort and Time Spread](images/search-effort-and-time-spread.png)

**3. Effect of Puzzle Difficulty**

![Effect of Difficulty](images/effect-of-difficulty.png)

**4. Execution Time vs. Number of Blank Cells**

![Time vs Blanks](images/time-vs-blanks.png)

## 🏆 Key Findings

- **A* Search:** Achieved a 100% success rate with an average execution time of approximately 0.0022 seconds.
- **Backtracking with MRV:** Achieved a 100% success rate while significantly reducing the number of explored states compared to standard Backtracking.
- **Backtracking:** Successfully solved all evaluated puzzles but required more search operations.
- **Hill Climbing:** Achieved a 20% success rate and struggled with more difficult puzzles due to local minima.

### Final Observation

Backtracking with MRV and A* demonstrated the best overall performance in the experiment. The results highlight the importance of heuristic selection and constraint-based reasoning when solving Constraint Satisfaction Problems (CSPs).

## ⚠️ Limitations

- The experiment uses only 60 puzzles from a much larger dataset.
- Backtracking has a limit of 50,000 assignments.
- A* Search has a limit of 3,000 expanded states.
- Hill Climbing uses randomized initialization, so results may vary.
- Execution times depend on the hardware and environment.

## 🎓 Academic Context

**Course:** Artificial Intelligence Lab  
**Project:** Sudoku Solver Using AI Search Algorithms

This project demonstrates the practical implementation and comparative analysis of informed search, local search, and constraint satisfaction techniques in Artificial Intelligence.

---

<p align="center">
  ✧ Built with Python & Artificial Intelligence ✧
  <br>
  ♡ Exploring Search Algorithms, One Puzzle at a Time ♡
</p>
