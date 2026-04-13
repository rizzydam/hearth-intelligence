# Crisis Escalation

AI is not a therapist. This pattern defines the boundary between "I can help" and "you need a human professional."

## Severity Levels

| Level | Signal Pattern | Response |
|-------|---------------|----------|
| **Green** | Within baselines | Normal operation |
| **Yellow** | 1-2 metrics trending down | Surface awareness, suggest small actions |
| **Orange** | Multiple domains degrading | Activate containment, reduce demands, check in more |
| **Red** | Crisis thresholds crossed | Gentle response, suggest professional resources, make no demands |

## Detection

### Threshold-Based (immediate)
```python
CRISIS_THRESHOLDS = {
    "mood": 2,      # <= 2 out of 10
    "anxiety": 9,   # >= 9 out of 10
    "energy": 1,    # = 1 out of 10
}
```

### Pattern-Based (accumulative)
- 5+ consecutive days declining mood
- Sleep below 4 hours for 3+ nights
- Complete communication avoidance (response rate = 0)
- Sudden spending spike on comfort items at unusual hours

### Compound (cross-domain)
- Three or more orange-level domains simultaneously = escalate to red

## Response Protocol

### Orange
1. Acknowledge ("I notice things are harder than usual")
2. Simplify (reduce task list to 1-2 items)
3. Contain (prevent cascade across domains)
4. No demands (everything optional)

### Red
1. Be present ("You don't have to do anything right now")
2. Name resources (988 Lifeline, Crisis Text Line 741741, SAMHSA)
3. Do NOT attempt therapy, minimize, or demand explanation
4. Stay available, make no demands

## Ethical Boundaries

- Never diagnose. Never prescribe. Never assume.
- Always offer human connection over AI help for mental health.
- Respect autonomy — user can dismiss any suggestion.
