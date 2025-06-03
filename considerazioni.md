We evaluate The VaR breach rate (percentage of losses that exceeded the predicted VaR threshold) on both training and test datasets, with a specific focus on two periods within the test data: 2024 and 2025. This allows us to observe how the model’s performance varies across different market conditions.

### Standard Case

| Period       | VaR Breach Rate |
|--------------|-----------------|
| Train        | 5.1837%          |
| Test         | 3.1073%           |
| 2024         | 2.3810%           |
| 2025         | 4.9020%           |

- The model shows good performance overall. On the training data, the VaR coverage is close to the expected 5%, indicating a good risk estimation.
- In the test set, we observe a difference between 2024 and 2025, with 2025 being more challenging for the model. This suggests that market conditions or volatility in 2025 were different or more difficult to predict. Furthermore, we notice that the model tends to overestimate risk. To further investigate this behavior, we introduce a stress testing scenario to better assess model robustness under more volatile conditions. 


---

### Stress Case – ARMA Model

| Period             | VaR Breach Rate |
|--------------------|-------------------|
| Train              | 6.4084%          |
| Test               | 6.4972%             |
| Test (2024)        | 5.5556%             |
| Test (2025)        | 8.8235%              |


- On the training data, the coverage is about 6.4%, slightly above the typical 5% threshold, indicating the model has underestimated the risk.
- In the test data overall (6.4%), the coverage is even higher, confirming that model is underestimating risk.
- Looking more closely, in 2024 (5.5%), the model performs better than training levels, with a good estimation. In 2025 (8.8%), the coverage spikes significantly.
- This indicates **2025 was a stress period with more extreme losses**, which the model had difficulty predicting accurately, leading to more frequent violations of the VaR threshold.


---



### Stress Case – GARCH Model


| Period       | VaR Breach Rate |
|--------------|-------------------|
| Train        | 5.8958%             |
| Test         | 5.3672%             |
| 2024         | 4.7619%             |
| 2025         | 6.8627%             |

- On the training data, the VaR coverage is approximately 5.8%, which is close to the expected level, indicating reliable risk estimation.
- In the overall test set, the coverage drops to about 5.3%, suggesting good results.
- For 2024, the coverage further decreases to 4.7%, meaning the model is more conservative during this period.
- However, in 2025, the coverage rises sharply to 6.8%, reflecting a more stressful market environment where the model underestimates risk and fails to capture the increased frequency of extreme losses.



---


### Comparison ARMA and GARCH
- GARCH has better results than ARMA during training.
- On the test data overall, ARMA shows a higher breach rate than GARCH, indicating ARMA underestimates risk more significantly in unseen data.
- For 2024, both models have relatively good breach rates, with GARCH being more conservative than ARMA.
- In 2025, a challenging period, both models struggle, but ARMA has a substantially higher breach rate compared to GARCH, suggesting that ARMA underestimates extreme losses more during volatile periods.
- Overall, GARCH appears more conservative, particularly in calmer market periods, while ARMA tends to underestimate risk more during stress periods.


In conclusion we can derive that GARCH provides a more cautious risk estimate and ARMA is less conservative but potentially more prone to large violations.

---
