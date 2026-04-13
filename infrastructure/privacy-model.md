# Privacy Model

Data classification, permission boundaries, and threat modeling for personal data systems.

## Data Classification

| Class | Examples | Rule |
|-------|---------|------|
| Critical | API keys, auth tokens | Encrypted, never logged, env vars only |
| Sensitive | Financial amounts, health vitals, mood | Local storage, no cloud without consent |
| Personal | Names, dates, journal entries | Local storage, owning module only |
| Derived | Trends, patterns, scores | Local storage, all processing layers |

## Permission Boundaries

- Each domain module owns its data exclusively
- Cross-domain intelligence flows through signals, never raw data
- Personal identity data is the most protected — only the identity module reads it
- API tokens auto-generated, localhost requests exempt

## Rules

1. Data never leaves the machine without explicit user action
2. Cross-domain intelligence flows through abstract signals, not raw data
3. No telemetry, no anonymous usage data, no cloud sync by default
4. AI call content is not stored (only token counts for cost tracking)
