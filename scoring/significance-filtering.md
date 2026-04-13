# Significance Filtering

Deciding what's worth surfacing vs. suppressing. Not every pattern deserves attention.

## The Filter

```python
significance = (
    magnitude * 0.30       # How big is the deviation?
    * frequency * 0.20     # How often does this happen?
    * user_impact * 0.25   # Does it affect a goal or priority?
    * actionability * 0.25 # Can the user actually do something?
)
# Surface only if significance > 0.4
```

## Actionability Is the Key Filter

- "Your rent is high" = 0 actionability (they know, can't change it tomorrow)
- "3 subscriptions, $47/month, unused 60 days" = high actionability

## Suppression Rules

- Don't alert on the same pattern twice in 7 days unless it escalated
- Don't alert on patterns the user has dismissed 3+ times
- Don't alert during crisis mode (reduce noise, not add to it)
- Don't alert on metrics with < 0.7 confidence

## Escalation Rules

- If suppressed pattern gets 2x worse, re-surface with context
- If 3+ suppressed patterns in the same domain, surface the compound view
- User-flagged priority domains get lower significance threshold (0.2 instead of 0.4)
