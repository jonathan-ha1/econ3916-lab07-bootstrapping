# Estimation & Bootstrapping — Quantifying Uncertainty Without a Formula

## Objective
This lab measures how uncertain an estimate is, first with formulas based on the Central Limit Theorem and then with the bootstrap, which works even when no formula exists.

## Methodology
- Loaded the UCI Adult Census Income data, which has 32,561 respondents.
- Separated the standard deviation of the data from the standard error of an estimate, and checked the s/sqrt(n) relationship across four sample sizes.
- Built parametric confidence intervals from the CLT and compared how quickly the CLT converges for age and for capital gains.
- Ran the bootstrap by hand with a resampling loop, then repeated it with scipy.stats.bootstrap.
- Bootstrapped the median of age and looked into why its standard error came out as zero.
- Compared percentile and BCa bootstrap intervals on a heavily skewed variable.
- Bootstrapped a two-sample difference in mean weekly hours.
- Asked an AI to write a bootstrap-interval function, revised the prompt once, and checked the function against the earlier intervals.

## Key Findings
- The standard error of an estimate is different from the standard deviation of the data, and it shrinks in line with s/sqrt(n) as the sample size grows.
- The CLT converges quickly for age but slowly for capital gains, so a parametric interval is less trustworthy for a skewed variable like capital gains.
- The bootstrap SE of the median of 32,561 whole-number ages is exactly 0.0000. With that many tied values, every resample returns the same median. The bootstrap is reporting a real property of the data, not failing.
- The first AI prompt left out how to handle randomness, so the function gave a different interval on every run. After a seed was added in the second prompt, the function's interval matched the scipy interval exactly.
