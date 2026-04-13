# Composite Health Scoring

Building a single 0-100 score from multiple heterogeneous sub-metrics.

## Pattern

```python
composite = sum(
    weight_i * normalize(metric_i)
    for weight_i, metric_i in weighted_metrics
)
# where sum(weights) = 1.0 and normalize maps any metric to 0.0-1.0
```

## Normalization

Map raw values to 0.0-1.0 using domain-specific ranges:
- Below alarm threshold = 0.0
- Within ideal range = 1.0
- Between alarm and ideal = proportional

## Weight Assignment

Weights should reflect:
1. **Impact**: How much does this metric affect the overall domain?
2. **Reliability**: How confident is the data source?
3. **Actionability**: Can the user influence this metric?

## Score Bands

Consistent across all domains:
- 80-100: Healthy
- 60-79: Needs attention
- 40-59: Degraded
- 0-39: Critical

## Bidirectional Recognition

Track both degradation AND sustained health. A system that only criticizes becomes another source of dread. One that also notices wins becomes worth believing in.
