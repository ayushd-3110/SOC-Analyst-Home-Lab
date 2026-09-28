# Lessons Learned

## Technical Lessons

- Authentication events are more useful when correlated with endpoint activity.
- Event 4688 is valuable for process investigation.
- PowerShell should be investigated using both process name and command line.
- Discovery commands should be interpreted in context.
- Persistence should be verified and then removed.
- Missing telemetry can limit an investigation.

## Investigation Lessons

The biggest lesson is to avoid jumping from:

> “I found a suspicious event”

to:

> “The machine was definitely compromised.”

Instead:

**Observe → Correlate → Validate → Conclude**

## Documentation Lessons

A good incident report should clearly separate:

- what was observed
- what was simulated
- what was attempted
- what was not confirmed

## Future Improvements

- Add stronger Sysmon coverage.
- Improve field extraction.
- Add more correlation searches.
- Add alert severity and risk scoring.
- Add automated response only after validation.
