# Miguel Cordero Pamphile

[![DatioLabs CI](https://github.com/miguelcorderopamphile/datiolabs/actions/workflows/ci.yml/badge.svg)](https://github.com/miguelcorderopamphile/datiolabs/actions/workflows/ci.yml)

Rust systems: memory safety of `unsafe` code, zero-copy layouts, and compiler/runtime behavior.

I work on low-level defects — uninitialized memory, invalid aliasing, misaligned or out-of-bounds access, and codegen/ABI mismatches — and send scoped fixes upstream. I reproduce them with Miri (Stacked/Tree Borrows), differential execution, targeted tests, and upstream CI.

## Built

**[DatioLabs Retail](https://github.com/miguelcorderopamphile/datiolabs)** — local-first Windows point of sale for Venezuelan retail, running in production. Rust + Tauri + Sled; fully offline, exact decimal multi-currency (USD/VES), local database with SHA-256-signed audit records.

- **67 core tests + 101 frontend tests**: property-based invariants (stock conservation, metamorphic cart totals, double-entry settlement), crash consistency, torn-state reload, backup tamper/truncation rejection.
- **Windows installer built and tested publicly in CI** — [download the latest release](https://github.com/miguelcorderopamphile/datiolabs/releases/latest).
- [Case study](https://datiolabs.com/engineering) · [Live demo](https://datiolabs.com/demo)

## Merged upstream

| Repository | PR | Opened | Merged | Change |
|---|---|---|---|---|
| `apache/arrow-rs` | [#11315](https://github.com/apache/arrow-rs/pull/11315) | 2026-10-01 | 2026-10-06 | Correct `i256 → f64` rounding at midpoints |
| `OffchainLabs/stylus-sdk-rs` | [#457](https://github.com/OffchainLabs/stylus-sdk-rs/pull/457) | 2026-09-30 | 2026-10-02 | Fix storage for `ruint ≥ 1.17.1`; drop vulnerable pin (RUSTSEC-2025-0137) |

## Open upstream

| Repository | PR | Opened | Change |
|---|---|---|---|
| `apache/arrow-rs` | [#11572](https://github.com/apache/arrow-rs/pull/11572) | 2026-10-15 | Cast `Utf8`/`LargeUtf8`/`Utf8View → Duration` |
| `google/zerocopy` | [#3775](https://github.com/google/zerocopy/pull/3775) | 2026-10-05 | Enforce move-stability in `ByteSlice` (soundness) |
| `rkyv/rkyv` | [#711](https://github.com/rkyv/rkyv/pull/711) | 2026-10-12 | Authenticate `#[rkyv(crate = ...)]` in `derive(Portable)` (soundness) |
| `model-checking/kani` | [#5001](https://github.com/model-checking/kani/pull/5001) | 2026-10-14 | Detect invalid vtable metadata in virtual calls |
| `Rust-for-Linux/pin-init` | [#183](https://github.com/Rust-for-Linux/pin-init/pull/183) | 2026-10-06 | `derive(Zeroable)` on unions: require ≥1 zeroable field |
| `microsoft/qdk` | [#3767](https://github.com/microsoft/qdk/pull/3767) | 2026-09-30 | Fix complex-arithmetic panic in QIR codegen |
| `cloudflare/boringtun` | [#497](https://github.com/cloudflare/boringtun/pull/497) · [#499](https://github.com/cloudflare/boringtun/pull/499) | 2026-10-18 | Endpoint handling on cookie replies; error instead of panic on peer update |

## Approach

- Repro first: a minimal test that fails on the current tree (Miri for UB, differential runs for behavior).
- One invariant per diff; repository tests and CI stay green.
- Record what was ruled out, not only what was fixed.

## Security research

- Reported issues in `boringtun` and `cloudflared` through the Cloudflare HackerOne program; details under coordinated disclosure. Upstream fixes proposed in [#497](https://github.com/cloudflare/boringtun/pull/497) and [#499](https://github.com/cloudflare/boringtun/pull/499).

## Contact

- Email: miguelcorderopamphile@gmail.com
- LinkedIn: [miguel-corderopamphile](https://www.linkedin.com/in/miguel-corderopamphile/)
- Based in Venezuela (UTC-4) · remote
