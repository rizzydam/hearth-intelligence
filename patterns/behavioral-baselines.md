# Behavioral Baselines

Every person has a unique normal. Deviations from baseline are signals, not diagnoses.

## Baseline Categories

- **Temporal**: When they engage, peak hours, consistency score
- **Financial**: Daily spending mean/std, category splits, impulse frequency
- **Health**: Sleep hours mean/std, exercise frequency, resting HR
- **Communication**: Response time, message volume, avoidance rate

## Establishing Baselines

- **Minimum data**: 14 days before baselines are reliable
- **Rolling window**: 30-day rolling to prevent stale baselines after life changes
- **Confidence**: `min(1.0, data_points / required_minimum)` — suppress alerts below 0.7

## Deviation Detection

### Static Threshold
```python
deviation_score = abs(current - baseline_mean) / baseline_std
# > 1.5 std: notable, > 2.0: significant, > 3.0: anomaly
```

### Trend Deviation
7-day moving average vs 30-day baseline — catches slow drift that daily checks miss.

### Pattern Deviation
Changes in WHEN/HOW, not just how much: spending shifted to nighttime, exercise became sporadic, communication response times doubled.

## Signal vs Noise Filter

| Factor | Weight |
|--------|--------|
| Magnitude | High |
| Duration (days persisted) | High |
| Multi-domain (other baselines also deviating) | Very High |
| Known context (holiday, vacation) | Reduces weight |
| User-flagged domain importance | Increases weight |

Single day of high spending during holidays = noise.
Three weeks of rising spending + declining sleep + social withdrawal = compound signal.
