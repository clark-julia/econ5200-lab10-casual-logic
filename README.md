# econ5200-lab10-casual-logic
# Causal Logic and DAGs: Diagnosing Bad Controls

## Objective
I investigated how incorrect control variables can bias causal estimates and used Directed Acyclic Graphs (DAGs) to identify valid adjustment sets.

## Methodology
- Compared regression estimates with and without a collider control, examining changes in coefficients, p-values, and R-squared.
- Tested how controlling for a pre-treatment collider introduced bias despite its timing.
- Compared total and direct treatment effects using a mediator.
- Evaluated the LaLonde job-training experiment by comparing its experimental benchmark with observational estimates using CPS data, before and after covariate adjustment.
- Used a `dag_utils.py` module to identify valid adjustment sets and test whether controls blocked backdoor paths.
- Asked AI to propose adjustment sets for a job-training study, revised the prompt to specify the causal structure, and checked both recommendations against the DAG.

## Key Findings
- Adding a collider control shifted the estimated effect from **-0.012 to -0.593** and increased R-squared from **0.000 to 0.585**, despite the true effect being zero.
- Controlling for a pre-treatment collider shifted the estimate from **-0.004 to -0.201**, despite the true effect being zero.
- The estimated total effect was **3.978** (true effect: 4.0), while the direct effect was **0.988** (true effect: 1.0).
- The LaLonde experimental benchmark was **$1,794**. The unadjusted observational estimate was **-$8,498**, improving to **$699** after covariate adjustment.
- Both AI recommendations identified `prior_earnings` as the valid adjustment set. Both produced an estimate of **4.047**, close to the true effect of 4.0. Revising the prompt helped clarify the causal reasoning behind excluding colliders and mediators.

