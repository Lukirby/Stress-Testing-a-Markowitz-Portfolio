### Portfolio simulation

---
##### Parameters

- `var_source` : Specifies whether to use real or predicted values for variance and covariance. 
- `r1` and `r2`: returns for NVDA and SPY respectively
- `dataframe`: Pandas DataFrame with at least var_NVDA, var_SPY, and cov columns
- `capital`: initial capital (default=1000)
- `output`: Required if var_source='predicted'; list of tuples (cov, var_NVDA, var_SPY)

---

##### Procedure explanation

1) **Initialization**: 
- Empty lists for weights, capital per asset, and portfolio returns.
- Initial portfolio value set to capital.
2) **Loop over each day**
- Step 1: Update portfolio value based on previous day's returns and allocation.
- Step 2: Extract variance and covariance (real or predicted).
- Step 3: Decide which asset has higher variance to set as "Asset 1".
- Step 4: Compute Minimum Variance Portfolio weight using get_mvp().
- Step 5: Store daily weights and capital invested using get_capital_values().
3) **End of simulation**
- Final portfolio value is printed.

- Function returns: daily portfolio values, daily weights in NVDA and SPY, daily capital invested in each asset, daily portfolio returns