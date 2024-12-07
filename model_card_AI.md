# Model Card: SimpleTransformerClassifier

## Model Description

**Input:** 
- Time series financial data organized in sequences
- Sequence lengths of 20-90 timesteps (optimal: 40-60)
- Features are normalized using Layer Normalization
- Input dimension matches the financial features provided
- Data is processed through sliding windows to create sequences

**Output:** 
- Three-class classification predictions (Buy, Hold, Sell)
- Probability distributions across the three classes
- Model produces outputs through a classification head after processing sequential patterns

**Model Architecture:** 
A transformer-based neural network with the following components:
- Input Layer Normalization
- Embedding Layer (d_model=32)
- Transformer Encoder
  - 2-head self-attention mechanism
  - Feed-forward network (dimension=64)
  - Dropout rate of 0.1
- Global Average Pooling
- Classification Head
  - Two-layer network with ReLU activation
  - Final projection to 3 classes

## Performance

Based on extensive hyperparameter tuning:
- Best Accuracy: 38.847%
- Minimum Loss: 1.08537
- Optimal Configuration:
  - Learning Rate: 0.00005
  - Sequence Length: 60
  - Batch Size: 64
  - Training Epochs: 10

Performance was evaluated using:
- Cross-entropy loss for classification
- Standard accuracy metrics
- Validation on held-out test set
- Early stopping with patience of 7 epochs

## Limitations

1. Model Capacity Constraints:
   - Single transformer layer architecture
   - Relatively small model dimension (d_model=32)

2. Training Constraints:
   - Fixed sequence length limits temporal pattern capture
   - Memory complexity of O(n²) due to attention mechanism
   - Sensitivity to hyperparameter choices

3. Performance Ceiling:
   - Accuracy plateaus around 39%
   - Minimal improvement beyond optimal configuration
   - Limited ability to capture very long-term dependencies

## Trade-offs

1. Architectural Decisions:
   - Simple architecture promotes stability but may miss complex patterns
   - Multi-head attention (2 heads) balances complexity with computational efficiency
   - Global average pooling reduces memory but may lose some temporal information

2. Training Configuration:
   - Larger batch sizes (64) improve performance but increase memory requirements
   - Higher learning rate (0.00005) speeds up training but may miss fine details
   - Sequence length of 60 balances context window with computational feasibility

3. Feature Processing:
   - Layer normalization adds computation but ensures training stability
   - Sliding window approach captures local patterns but may miss global trends
   - Standard scaling of features helps training but may remove important scale information

4. Practical Considerations:
   - AdamW optimizer with weight decay (0.01) controls overfitting but slows convergence
   - Early stopping saves computation but might prevent finding better minima
   - Dropout (0.1) helps generalization but reduces model capacity
  
# Hyperparameter Tuning Results Analysis

## Results Table (Sorted by Accuracy)
| Trial | Learning Rate | Sequence Length | Batch Size | Epochs | Min Loss | Accuracy |
|-------|--------------|-----------------|------------|---------|----------|----------|
| 1 | 0.00005 | 60 | 64 | 10 | 1.08537 | 0.38847 |
| 2 | 0.00001 | 60 | 32 | 10 | 1.08847 | 0.38817 |
| 3 | 0.00005 | 40 | 64 | 10 | 1.08444 | 0.38751 |
| 4 | 0.00005 | 60 | 12 | 10 | 1.07650 | 0.38654 |
| 5 | 0.00005 | 40 | 32 | 10 | 1.08059 | 0.38650 |
| 6 | 0.00005 | 90 | 64 | 10 | 1.08870 | 0.38648 |
| 7 | 0.00005 | 20 | 12 | 10 | 1.07987 | 0.38642 |
| 8 | 0.00001 | 40 | 32 | 10 | 1.08741 | 0.38513 |
| 9 | 0.00005 | 40 | 12 | 10 | 1.07854 | 0.38505 |
| 10 | 0.00001 | 60 | 12 | 10 | 1.08342 | 0.38438 |

[Table truncated for clarity]

## Key Findings

1. Best Performing Configuration:
- Learning Rate: 0.00005
- Sequence Length: 60
- Batch Size: 64
- Epochs: 10
- Resulting in:
  - Accuracy: 0.38847
  - Min Loss: 1.08537

2. Parameter Impact Analysis:

a) Learning Rate:
- Best performances with 0.00005
- Lower learning rates (0.00001) generally performed worse
- Sweet spot appears to be around 0.00005

b) Sequence Length:
- Optimal range: 40-60
- Longer sequences (90) didn't improve performance
- Shorter sequences (20) showed decreased performance

c) Batch Size:
- Larger batch sizes (64) generally performed better
- Smaller batch sizes (12) showed mixed results
- Medium batch sizes (32) were competitive

3. Performance Patterns:
- Loss values range: 1.076 - 1.100
- Accuracy range: 0.365 - 0.388
- Small variations in parameters can lead to meaningful performance differences

4. Recommendations:
- Stick with learning rate around 0.00005
- Use sequence lengths between 40-60
- Prefer larger batch sizes (64)
- Consider exploring around these values with finer granularity

