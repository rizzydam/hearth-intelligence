# Flow Tracing

Pipeline instrumentation for diagnostic analysis. Monkey-patch at runtime, capture every data handoff, restore originals on stop.

## Architecture

```python
@dataclass
class TraceEvent:
    stage: str          # "sense.export", "bus.publish", "desk.aggregate"
    component: str      # Which module
    event_type: str     # "data_in", "data_out", "error"
    data_count: int     # Items processed
    duration_ms: float  # Time spent
    metadata: dict      # Stage-specific details
```

## What to Instrument

1. **Data producers**: Wrap export/publish methods to record what goes out
2. **Data consumers**: Wrap aggregate/process methods to record what comes in
3. **Message bus**: Wrap publish to record topic, subscriber count, payload size
4. **External calls**: Wrap AI/API calls to record latency and cost

## Analysis from Traces

- **Dead stages**: Received no input during the run
- **Data sinks**: Received input but produced no output
- **Zero-subscriber topics**: Published but nobody listening
- **Bottlenecks**: Stage timing as % of total pipeline time
- **Error rates**: Failures per stage

## Design Constraints

- Zero overhead when not active (monkey-patch only on start)
- Restore all originals on stop
- Thread-safe event collection
- No dependency on the systems being traced
