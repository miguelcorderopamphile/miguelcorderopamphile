# Miguel Cordero Pamphile

I write Rust in Venezuela. Most of my work is on low-level correctness: unsafe code, memory
layout, and the places where the compiler or the runtime does not do what the source
suggests.

I look for those problems with small reproductions. Miri for undefined behavior, differential
runs for behavior, and the repository's own tests and CI for everything else. If I cannot
reproduce something, I do not claim it. I also write down what I ruled out.

## DatioLabs

I built and run [DatioLabs Retail](https://github.com/miguelcorderopamphile/datiolabs), a
point-of-sale system for shops in Venezuela. It is a Tauri application with a Rust core and
desktop shell, and a [TypeScript frontend](https://github.com/miguelcorderopamphile/datiolabs-frontend).
It works offline on Windows, and the source is public (MIT).

Prices are in USD and customers pay in bolívares (Venezuela's currency) at the daily BCV rate
(Banco Central de Venezuela). The only external input is that rate: a small scraper validates
it, keeps the last known value and lets the operator override it; a missing rate blocks the
sale instead of becoming zero.

The Rust core has 67 tests: stock conservation, cart totals independent of insertion order,
double-entry settlement, FEFO across lots, crash consistency, torn-state reload and backup
integrity. The Tauri command contract (names, arguments, registration) is audited in CI
against every frontend `invocar()` call. The Windows installer attached to the release is a
CI build used as a compile/smoke check. The engineering write-up is at
[datiolabs.com/engineering](https://datiolabs.com/engineering) and the web demo at
[datiolabs.com/demo](https://datiolabs.com/demo).

## Upstream

Merged:

| Repository | PR | Merged | Change |
|---|---|---|---|
| `apache/arrow-rs` | [#11315](https://github.com/apache/arrow-rs/pull/11315) | 2026-10-06 | Correct `i256 → f64` rounding at midpoints |
| `OffchainLabs/stylus-sdk-rs` | [#457](https://github.com/OffchainLabs/stylus-sdk-rs/pull/457) | 2026-10-02 | Fix storage for `ruint ≥ 1.17.1`; drop the pin affected by RUSTSEC-2025-0137 |

Open:

| Repository | PR | Opened | Change |
|---|---|---|---|
| `apache/arrow-rs` | [#11572](https://github.com/apache/arrow-rs/pull/11572) | 2026-10-15 | Cast `Utf8`/`LargeUtf8`/`Utf8View → Duration` |
| `google/zerocopy` | [#3775](https://github.com/google/zerocopy/pull/3775) | 2026-10-05 | Require move-stability in `ByteSlice` (soundness) |
| `rkyv/rkyv` | [#711](https://github.com/rkyv/rkyv/pull/711) | 2026-10-12 | Authenticate the `#[rkyv(crate = ...)]` path in `derive(Portable)` (soundness) |
| `model-checking/kani` | [#5001](https://github.com/model-checking/kani/pull/5001) | 2026-10-14 | Detect invalid vtable metadata in virtual calls |
| `Rust-for-Linux/pin-init` | [#183](https://github.com/Rust-for-Linux/pin-init/pull/183) | 2026-10-06 | `derive(Zeroable)` on unions: require at least one zeroable field |
| `microsoft/qdk` | [#3767](https://github.com/microsoft/qdk/pull/3767) | 2026-09-30 | Fix a complex-arithmetic panic in QIR codegen |
| `cloudflare/boringtun` | [#497](https://github.com/cloudflare/boringtun/pull/497), [#499](https://github.com/cloudflare/boringtun/pull/499) | 2026-10-18 | Do not update the peer endpoint on cookie replies; return an error instead of panicking on peer update |

## Security

I reported issues in `boringtun` and `cloudflared` through the Cloudflare HackerOne program.
The details are under coordinated disclosure. Two upstream fixes are proposed in
[#497](https://github.com/cloudflare/boringtun/pull/497) and
[#499](https://github.com/cloudflare/boringtun/pull/499).

## Contact

- Email: miguelcorderopamphile@gmail.com
- LinkedIn: [miguel-corderopamphile](https://www.linkedin.com/in/miguel-corderopamphile/)
- Venezuela (UTC-4), remote; open to relocating anywhere if needed
