# Challenge 16: Monte Carlo Pricer (Rust)

## Problem

Price options using Monte Carlo simulation. European, Asian, Barrier options.

## Files

- `solution/mod.rs` — Your implementation (edit this)
- `src/types.rs` — Trait and types (do NOT modify)
- `src/main.rs` — Benchmark harness (do NOT modify)

## Limits

- Time: 60 seconds
- Memory: 512 MB
- Daily submissions: 5

## Validation

Every result is compared with a high-precision reference price of the same
model (100 steps, the barrier checked at the end of each step, the Asian on the
mean of the 100 step values): Black-Scholes for Europeans, a 10-million-path
simulation for the rest. On every option:

- **Precision:** the price is within 5 standard errors of a plain 10,000-path
  simulation of that option.
- **Honest `std_error`:** the price is within 5 of your own reported
  `std_error`. Report a smaller error only if your price really is that
  accurate.
- **10,000-path precision:** the reported `std_error` is at most 1.25 times
  that of a plain 10,000-path simulation. Variance reduction is welcome;
  fewer effective paths are not.

All checks accept any difference below 0.001. They run on the timed batch
(every timed call) and on a held-out batch; a failed check fails the run. The
certified run does the same with batches from private seeds.
