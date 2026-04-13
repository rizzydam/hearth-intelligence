# Compound Stress Detection

Stress is a compound signal — detected by reading across ALL life domains, not just self-reported mood.

## Multi-Domain Signal Normalization

Convert heterogeneous signals to a unified 0.0-1.0 severity scale:
- **Financial**: Overdrafts, late payments, spending spikes on comfort items
- **Health**: Missed appointments, medication gaps, sleep disruption
- **Career**: Job search activity spikes, salary dissatisfaction
- **Social**: Communication avoidance, response time increases
- **Family**: Conflict frequency, goal abandonment
- **Self-reported**: Anxiety scores, mood drops, journal sentiment

## Stressor Ranking

Four-factor ranking:
- **Severity**: Current intensity (0-1)
- **Acuity**: Acute (days), subacute (weeks), chronic (months)
- **Scope**: How many life domains affected
- **Trajectory**: Getting worse or better

## Compound Cycle Detection

Model stressors as a directed graph. Detect feedback loops:
```
financial_stress -> sleep_disruption -> mood_decline -> comfort_spending -> financial_stress
```

Each edge has a causality confidence from temporal precedence: if A precedes B 80% of the time, infer likely causation.

### Intervention Point Analysis

Within a detected cycle, rank where to intervene for maximum impact. Breaking the root cause beats treating symptoms.

## Early Warning

Flag when 3+ domains simultaneously worsen. Velocity matters more than absolute level — a fast decline from 7 to 4 is more urgent than a stable 3.

## Resilience Tracking

- **Recovery speed**: Time from acute stress to baseline
- **Coping effectiveness**: severity_before - severity_after per strategy
- **Optimal conditions**: When is the person most resilient?
