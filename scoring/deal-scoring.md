# Deal Scoring

Multi-factor purchase value analysis. Composite 0-100 score from five weighted components.

## Formula

```python
deal_score = (
    price_vs_history * 0.30    # Current price vs historical range
    + value_per_use * 0.25     # Expected cost per use over lifetime
    + urgency_factor * 0.20    # Need it now or can wait?
    + budget_fit * 0.15        # Fits within spending plan?
    + opportunity_cost * 0.10  # What else could this money do?
)
```

## Score Bands

| Score | Meaning |
|-------|---------|
| 90-100 | Exceptional — buy now |
| 75-89 | Strong buy |
| 60-74 | Buy if needed |
| 40-59 | Wait for better price |
| 0-39 | Overpriced |

## Price vs History

```python
percentile = (current - historical_min) / (historical_max - historical_min)
price_vs_history = 1.0 - percentile  # 0 = all-time low (great)
```

## Value Per Use

```python
value_per_use = price / (expected_uses_per_week * expected_ownership_weeks)
```

## Purchase Timing Factors

- Historical seasonal pricing (Black Friday, end-of-season)
- Product lifecycle (new generation depresses old prices)
- Price trend direction (dropping = wait, rising = buy soon)
