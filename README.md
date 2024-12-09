# Sentence   Generation
The goal here is to generate a sentence consisting of n+2 words, including the special tokens `<SoS>` (Start of Sentence) and `<EoS>` (End of Sentence), that maximizes the overall score. The score of a sentence is computed based on the transition probabilities between consecutive words, factoring in the likelihood of moving from one word to the next as per the transition matrix.

To achieve this, four search algorithms have been implemented: IDDFS, Greedy Search, Uniform Cost Search (UCS), and A* Search. Each algorithm is explored for its ability to efficiently generate a sentence with the highest cumulative score, following different search strategies and heuristics.


---

## Loading and Generating Transition Matrix and Vocabulary Data

This section of involves loading and generating the necessary data for sentence generation. The two key components are the transition matrix and the vocabulary.

- **In case of loading data**, only run the group of cells titled: `For loading data`
- **In case of generating data**, only run the group of cells titled: `For generating data`
- Run `Normalising Transition Matrix` to normalise the transition matrix (in both cases)

---

## Search Algorithms

### 0 -> Function: `calculate_score`
The `calculate_score` function computes the cumulative score of a given sentence based on the transition matrix. It evaluates the likelihood of transitioning between words, factoring in each consecutive word pair in the sentence.

### 1 -> Function: `IDDFS` (Iterative Deepening Depth-First Search)
The `iddfs` function implements an iterative deepening depth-first search strategy to explore possible sentences and find the one with the highest cumulative score, as calculated by the `calculate_score` function.

- **Helper Function**: `dfs_iterative`
  - The helper function `dfs_iterative` performs depth-limited DFS at each level of the `iddfs` search.

### 2 -> Function: `Greedy Search`
The `greedy_search` function implements a greedy algorithm to generate a sentence by selecting the most probable word at each step, based on the transition matrix.

### 3 -> Function: `UCS` (Uniform Cost Search)
The `uniform_cost_search` function implements a uniform cost search algorithm to generate a sentence by maximizing the cumulative transition score. It explores all possible paths to find the optimal sentence based on the transition matrix, ensuring that the sentence has the highest overall score.

### 4 -> Function: `A* Search`
The `a_star_search` function implements the A* search algorithm to generate a sentence by maximizing the transition probability score from the transition matrix, incorporating both an accumulated score (`g = calculate_score`) and a heuristic estimate (`h_heuristic`) of the remaining score to the goal (complete sentence with `<EoS>`).

- **Helper Function**: `h_heuristic`
  - The `h_heuristic` function calculates an optimistic estimate (heuristic) for the remaining score in the A* search by assuming the best-case transitions from the current path to the goal.
