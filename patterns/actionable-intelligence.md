# Actionable Intelligence

Every piece of analysis must answer three questions: **What happened? Why does it matter? What should the user do?**

## The Action Pipeline

```
Raw Data -> Pattern Detection -> Significance Assessment -> Action Generation -> Presentation
```

### Pattern Detection (What happened?)

Not "you spent $450 on food" — that's a number. Instead: "Your food spending is 23% higher than your 3-month average, driven by a 4x increase in delivery orders."

Pattern types every engine should detect:
- **Trends**: Direction over time (increasing, decreasing, stable, volatile)
- **Anomalies**: Deviations from the user's normal (not a global normal)
- **Thresholds**: Crossing user-defined or intelligent boundaries
- **Correlations**: Two things moving together
- **Cycles**: Recurring patterns (payday spikes, seasonal changes)

### Significance Assessment (Why does it matter?)

```python
significance_score = (
    magnitude       # How big is the deviation? (0-1)
    * frequency     # How often does this happen? (0-1)
    * user_impact   # Does this affect a goal or priority? (0-1)
    * actionability # Can the user actually do something? (0-1)
)
# Only surface if significance_score > 0.4
```

**The actionability filter is critical.** "Your rent is high" has zero actionability. "You have 3 subscriptions totaling $47/month that you haven't used in 60 days" is highly actionable.

### Action Generation (What should they do?)

Every insight MUST include at least one concrete action:

| Action Type | When to Use |
|------------|-------------|
| **Stop** | Waste detected |
| **Start** | Opportunity identified |
| **Adjust** | Overspending/overcommitting pattern |
| **Monitor** | Emerging trend, not yet actionable |
| **Decide** | Decision point reached, options available |
| **Learn** | Knowledge gap detected |

### Presentation (The Action Card)

```
[urgency_indicator]
TITLE: One-line summary of what happened
CONTEXT: Why this matters to THIS person
ACTION: Specific thing to do (with how)
IMPACT: What changes if they do it
```
