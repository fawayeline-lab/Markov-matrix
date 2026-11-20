# Markov Chains Applied to a Bank Queue

**Author: Yeline Fawa** · Bachelor's year 3 (L3 SDIA) project · Operations research

> All numbers in this project are **fictitious**. They illustrate the method and do not describe any real bank.

## The problem and the answer
How many tellers should a bank open (from 1 to 5), when there are priority and ordinary customers?

The model is a **Markov chain** whose state is the number of priority and ordinary customers present (capacity 8, i.e. 45 states, one step = 1 minute). We build its **transition matrix P**, compute the stationary distribution (πP = π), then the mean waiting time and the probability that the bank is full. With a waiting-time threshold of 1 minute for ordinary customers (a fictitious value chosen for the example), **2 tellers are needed off-peak and 4 at peak time**. A Monte Carlo simulation confirms the calculation.

## Getting started (RStudio)
1. *File > Open Project…* then `projet-markov.Rproj`.
2. Install the required packages once: open `install_packages.R` and click **Source**.
3. Run `run_all.R` (calculations, figures, tests) or `demo_simulation.R` (a bank day simulated customer by customer, case by case from 1 to 5 tellers, with a live animation).
4. `projet_markov.Rmd`: click **Knit** to produce the full notebook.

From the command line: `Rscript run_all.R`

## Required R packages
| Package | Used for |
|---|---|
| `jsonlite` | reads the parameter file `data/parameters.json` |
| `testthat` | automatic tests |
| `rmarkdown` | **Knit** button: builds the Word / HTML document |
| `knitr` | runs the R code inside the document |
| `officer` | optional, builds Word files |

Install them all at once:

```r
source("install_packages.R")
```

or by hand:

```r
install.packages(c("jsonlite", "testthat", "rmarkdown", "knitr", "officer"))
```

R 4.0 or newer is required (4.2+ recommended). Pandoc, needed by `rmarkdown`, is bundled with RStudio.

## Contents
| Item | Role |
|---|---|
| `src/model.R` | Transition matrix `build_P`, stationary distribution, indicators |
| `src/simulation.R` | Monte Carlo simulation of the chain |
| `src/scenarios.R` | Comparison of 1 to 5 tellers, off-peak and peak |
| `src/day.R` | Customer-by-customer day simulation and animation |
| `src/figures.R` | Plots |
| `data/parameters.json` | Fictitious parameters (editable) |
| `tests/` | Automatic tests (testthat) |
| `docs/` | Documentation in English: research notes, model description, sources |
| `markovteller/` | The same model as a local R package |
| `run_all.R`, `demo_simulation.R` | Scripts to run |

The `figures/` and `outputs/` folders are created automatically when the scripts run. Function names, file names and comments are all in English.

## Documentation
- [`docs/01_research.md`](docs/01_research.md): Markov chains and transition matrices, queueing theory, Little's law.
- [`docs/02_model.md`](docs/02_model.md): assumptions, transition matrix, hand-worked 3-state example, indicators, validation, limits.
- [`docs/sources.md`](docs/sources.md): sources.

## The `markovteller` package
```r
install.packages("markovteller", repos = NULL, type = "source")   # from the folder that contains markovteller/
library(markovteller)
```
See [`markovteller/README.md`](markovteller/README.md).

## License
MIT, see [`LICENSE`](LICENSE).
