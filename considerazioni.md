We evaluate The VaR coverage (percentage of losses that exceeded the predicted VaR threshold) on both training and test datasets, with a specific focus on two periods within the test data: 2024 and 2025. This allows us to observe how the model’s performance varies across different market conditions.

### Standard Case

| Period       | VaR Coverage Rate |
|--------------|-----------------|
| Train        | 5.21%           |
| Test         | 2.90%           | 
| 2024         | 2.38%           | 
| 2025         | 4.30%           |

- The model shows good performance overall. On the training data, the VaR coverage is close to the expected 5%, indicating a good risk estimation. 
- In the test set, we observe a difference between 2024 and 2025, with 2025 being more challenging for the model. This suggests that market conditions or volatility in 2025 were different or more difficult to predict. 
- In the test set, the model tends to overestimate risk. To further investigate this behavior, we introduce a stress testing scenario to better assess model robustness under more volatile conditions.
---

### Stress Case – ARMA Model


| Period             | VaR Coverage Rate |
|--------------------|-------------------|
| Train              | 6.41%             |
| Test               | 7.25%             |
| Test (2024)        | 6.35%             |
| Test (2025)        | 9.68%             |


- On the training data, the coverage is about 6.41%, slightly above the typical 5% threshold, indicating the model has underestimated the risk.
- In the test data overall (7.25%), the coverage is even higher, suggesting the model is underestimating risk.
- Looking more closely, in 2024 (6.35%), the model performs closer to training levels, but in 2025 (9.68%), the coverage spikes significantly.
- This indicates **2025 was a stress period with more extreme losses**, which the model had difficulty predicting accurately, leading to more frequent violations of the VaR threshold.


### Stress Case – GARCH Model


| Period       | VaR Coverage Rate |
|--------------|-------------------|
| Train        | 5.50%             |
| Test         | 4.64%             |
| 2024         | 3.57%             |
| 2025         | 7.53%             |

- On the training data, the VaR coverage is approximately 5.5%, which is close to the expected level, indicating reliable risk estimation.
- In the overall test set, the coverage drops to about 4.6%, suggesting good results with a tendency to be conservative.
- For 2024, the coverage further decreases to 3.6%, meaning the model is more conservative during this period.
- However, in 2025, the coverage rises sharply to 7.5%, reflecting a more stressful market environment where the model underestimates risk and fails to capture the increased frequency of extreme losses.


### Comparison ARMA and GARCH
- GARCH has better results than ARMA during training.
- On the test data overall, ARMA shows a higher breach rate (7.25%) than GARCH (4.64%), indicating ARMA underestimates risk more significantly in unseen data.
- For 2024, both models have relatively low breach rates, with GARCH (3.57%) being more conservative than ARMA (6.35%).
- In 2025, a challenging period, both models struggle, but ARMA has a substantially higher breach rate (9.68%) compared to GARCH (7.53%), suggesting that ARMA underestimates extreme losses more during volatile periods.
<<<<<<< HEAD
- Overall, GARCH appears more conservative, particularly in calmer market periods, while ARMA tends to underestimate risk more during stress periods.
=======
- Overall, GARCH appears more conservative, particularly in market periods, while ARMA tends to underestimate risk more during stress periods.
>>>>>>> 481b840583e06a550ea2f4dbb49a78e5be0512da

In conclusion we can derive that GARCH provides a more cautious risk estimate and ARMA is less conservative but potentially more prone to large violations. 

---