# Group Dynamics

Understanding group health, participation equity, and shared decision-making.

## Core Metrics

| Metric | Range | What It Measures |
|--------|-------|-----------------|
| Group health score | 0-100 | Overall cohesion and functioning |
| Engagement equity | 0-100 | How evenly distributed participation is |
| Psychological safety | 0-100 | Can members be vulnerable and disagree safely |
| Conflict risk | low/med/high | Early warning for relationship breakdown |

## Power Dynamic Detection

```python
voice_distribution = {member: contribution_count / total}
dominance_ratio = max(voice_distribution.values()) / (1 / member_count)
# > 2.0 = one person doing 2x their share of talking
```

## Decision Quality Scoring

```python
decision_quality = (
    participation_breadth    # Did everyone weigh in? (0-1)
    * information_quality    # Were relevant facts surfaced? (0-1)
    * implementation_rate    # Was the decision followed through? (0-1)
)
```

## Conflict Resolution

- Detect early: rising disagreement frequency, declining interaction quality
- Don't take sides: surface the pattern, not a judgment
- Track resolution: was the conflict addressed or suppressed?
