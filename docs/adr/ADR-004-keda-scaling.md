# ADR-004: KEDA Scaling on Test Runs

- Status: Proposed
- Date: 2026-09-05

Runner workers scale on Kafka lag of `bench.run.completed`; cooldown 300 s.
