# Hybrid String Matching Algorithm

A Python-based framework that brings together three classic string-matching algorithms: **Naive Search**, **Knuth–Morris–Pratt (KMP)**, and **Rabin–Karp**. The project retrieves article text through the Wikipedia REST API, applies a rule-based algorithm selector, and compares the algorithms through correctness checks and repeated runtime measurements.

## Features

- Retrieve Wikipedia article source text using the Wikipedia REST API.
- Search text using Naive, KMP, and Rabin–Karp algorithms.
- Recommend an algorithm using simple rules based on pattern length, text length, and alphabet size.
- Compare matching positions and occurrence counts across all three algorithms.
- Benchmark three 500-character samples from the beginning of the article.
- Evaluate each algorithm over 10 trials using mean, median, standard deviation, minimum, and maximum runtime.
- Report the fastest measured algorithm, selector optimality, and runtime relative to Naive Search.

## Algorithms

| Algorithm | Main technique | Worst-case time complexity |
|---|---|---|
| Naive Search | Direct substring comparison | O(nm) |
| KMP | LPS (Longest Proper Prefix which is also Suffix) table | O(n + m) |
| Rabin–Karp | Hashing with rolling hash and character verification | O(nm) |

Here, `n` is the text length and `m` is the pattern length.

## Requirements

- Python 3
- `requests`
- `numpy` (imported in the evaluation notebook cell)
- Jupyter Notebook or JupyterLab

Install dependencies:

```bash
pip install -r requirements.txt
```

## Run the project

1. Clone or download this repository.
2. Install the dependencies.
3. Open `Hybrid_String_Matching_Algorithm.ipynb` in Jupyter Notebook or JupyterLab.
4. Run the notebook cells in order.
5. Enter a Wikipedia article title when prompted (the recorded example uses **Artificial intelligence**).
6. Enter a search pattern to compare the three algorithms.

An internet connection is required to retrieve the article from Wikipedia.

## Recorded experiment

The notebook's recorded experiment used the Wikipedia article **Artificial intelligence**.

| Parameter | Recorded value |
|---|---:|
| Text size | 283,885 characters |
| Search pattern | `intelligence` |
| Pattern length | 12 |
| Alphabet size | 137 |
| Trials per algorithm | 10 |
| Matches found | 248 |

### Median runtime results

| Algorithm | Median time (seconds) |
|---|---:|
| Naive | 0.04503857 |
| KMP | 0.06021139 |
| Rabin–Karp | 0.07616506 |

All three algorithms returned the same 248 matching positions. In this recorded run, Naive Search was the fastest measured algorithm, while the rule-based selector chose KMP. The selector was therefore not optimal for this particular input. These are observed results from one notebook run; timings can vary with hardware, Python version, and system load.

## Important implementation note

The function named `train()` performs preliminary timing benchmarks on text samples; it does **not** train a machine-learning model. Algorithm selection is rule-based, not learned. The test routine executes all three algorithms for comparison, while the selector reports its recommendation.

## Repository contents

- `Hybrid_String_Matching_Algorithm.ipynb` — project implementation, sample execution, and performance evaluation.
- `README.md` — project overview and instructions.
- `requirements.txt` — Python dependencies.
