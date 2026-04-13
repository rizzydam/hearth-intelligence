# Inference Routing

Selecting the right AI model at the right cost per task.

## Task-Based Routing

| Task | Model Tier | Example |
|------|-----------|---------|
| Classification | Haiku | Transaction categorization |
| Extraction | Haiku/Sonnet | Entity extraction from text |
| Summarization | Sonnet | Daily briefings |
| Analysis | Sonnet | Pattern interpretation |
| Reasoning | Opus | Life recommendations, adversarial scrutiny |

## Fallback Chain

```python
routing = {
    "categorize": ["haiku", "sonnet"],
    "summarize":  ["sonnet", "haiku"],
    "recommend":  ["opus", "sonnet"],
    "challenge":  ["opus", "sonnet"],
}
```

## Cost Management

- Track daily spend against budget
- When budget low, downgrade non-critical calls to cheapest tier
- Batch where possible (10 items in 1 call, not 10 calls)
- Cache common prompts
- Use structured output (JSON mode reduces token waste)

## Key Insight

Most systems only need the best model in 2-3 places. Everything else can run cheaper. Identify the high-reasoning bottlenecks and optimize everything else.
