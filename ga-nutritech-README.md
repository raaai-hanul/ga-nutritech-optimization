# Personalised Nutri-Tech Optimization for Women's Health (Genetic Algorithm)

**Tools:** Python, NumPy, Matplotlib | **Context:** ISP611 Optimization Algorithms (UiTM)

## Business Question
A subscription supplement company must pick the best combination of supplements from its inventory so a customer hits her Recommended Daily Intake (Iron, Folic Acid, Calcium) without over-supplementing, without "pill fatigue", and within budget. Manual selection does not scale, so how can this be automated?

## Approach
- Chromosome = bit-string where each gene is one supplement (1 = included)
- Multi-objective fitness: `f(x) = (w1 * Accuracy) - (w2 * Pill count) - (w3 * Cost in RM)`
- Accuracy is capped at 1.0 per nutrient so a surplus cannot hide a deficiency
- GA steps: random initialization, roulette-wheel selection, single-point crossover, bit-flip mutation

## Experiments
| Experiment | Mutation | Population | Budget (RM) | What it showed |
|---|---|---|---|---|
| EXP 1 Default | 0.1 | 20 | 5.00 | Stable, converged almost immediately (best fitness about 2.47) |
| EXP 2 High mutation | 0.5 | 20 | 5.00 | Unstable, fitness swings between about 2.0 and 2.5 |
| EXP 3 Low population | 0.1 | 5 | 5.00 | Stagnates (about 1.99), one brief spike |
| EXP 4 Restricted budget | 0.1 | 20 | 2.50 | Lower ceiling (about 1.35 to 1.70) |

**Key takeaway:** parameter choice changes both stability and the best solution found, and a tight budget caps achievable nutritional accuracy no matter how many generations run.

## Suggested Improvements (documented in the report)
Bioavailability deduction (calcium inhibits iron absorption) and a soft parabolic budget penalty instead of a hard cut-off.

## Files
- `nutritech_ga.ipynb` full code
- `ISP611_report.pdf` full report
- `results/` convergence plots

## How to Run
Open the notebook in Google Colab, then Runtime > Run all.
