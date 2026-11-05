# MACK — Public Verification Record

**MACK** is a fail-closed zero-trust security and verification platform in Rust, built and owned by **Allen Mack** (AI Infinity Force One), a solo security engineer. The platform itself is proprietary — its source repository is private and it is offered for non-exclusive licensing.

**This repository contains no source code.** It exists so that anyone — a prospective licensee, an employer, a reviewer — can check the platform's verification record *without having to trust a claim on a web page*. The centerpiece is an owner-signed release attestation whose signature you can verify yourself, in one command, using only files in this repo.

## What's here

| File | What it is |
|---|---|
| `ATTESTATION.md` | The owner's signed statement of the November 2, 2026 release record: tests, fuzzing, concurrency models, CI, and dependency posture — each result cited to the commit and run it came from. |
| `ATTESTATION.md.sig` | The Ed25519 signature over `ATTESTATION.md` (OpenSSH format, namespace `mack-release`). |
| `allen-mack-release.pub` | The public half of the release signing key. Fingerprint: `SHA256:iKgJ7s1r96fDWGlcPYObuL1cGYJNYL5e1npeF3KSZws` |
| `allowed_signers` | The `ssh-keygen` trust file used for verification (principal `allenmack`). |
| `SIGNING.md` | What the key is, how it is custodied, and the exact verification command. |
| `EVIDENCE-SUMMARY.md` | The verification results in one page, including the limitations and disclosures — read those too; they are part of the record. |
| `VERIFY.md` | Step-by-step verification instructions with the expected output. |

## The record, in brief

- **226 / 226 tests passing** (commit `8359c2c9`; repeated 226/226 on the loom-modified tree)
- **2,639,356 fuzz executions, zero crashes** across six cargo-fuzz targets (CI Fuzzing run #46; runs #48 and #49 also SUCCESS)
- **Loom concurrency models 3 / 3** against the real ownership API (commit `5233f027`)
- **CI run #326 SUCCESS** — all four jobs (test, Dependency Audit, Test Coverage, ledger-demo); Lint run #16 SUCCESS
- **Dependency audit exit 0** over 380 dependencies; the sole underlying vulnerability is the `rsa` Marvin advisory (RUSTSEC-2023-0071, no upstream fix) — disclosed, exposure-analyzed, and absent any RSA use in first-party code
- **Owner-signed attestation** published November 2–3, 2026; the identical signature set also lives in the source repository's `attestation/` folder (commit `e9e14ce8`) for cross-checking under NDA

## What MACK is

- **Zero-trust vault** — secrets encrypted at rest (Argon2id key derivation, XChaCha20-Poly1305 authenticated encryption)
- **12-lane containment engine** — workers confined by Landlock
- **Detection** — YARA-X scanning and STIX 2.1 bundle export
- **Tamper-evident audit ledger** — hash-chained, append-only records (tamper-*evident*, not tamper-proof — see the disclosures)
- **Sibling Mesh** — opt-in leased-execution ownership gate (in-process)

A free, open-source sample of the pattern is the [MACK Zero-Trust Rust Starter Kit](https://github.com/a95674127-beep/mack-zerotrust-rust-starter) (MIT).

## Stated plainly

- These results were produced by the owner's own test suite and CI pipeline. This is **not** a third-party audit and claims no certification. Its purpose is the opposite of "trust me": every result cites its commit and run, and the detailed evidence archive (run logs, manifests verified 28/28 and 30/30) is available to serious parties during due diligence under a mutual NDA.
- The software is **pre-deployment**, with no reference customers yet.
- **No patent application covering this software has been filed or is pending.**

## Contact

Allen Mack — a95674127@gmail.com · GitHub [@a95674127-beep](https://github.com/a95674127-beep)

Licensing inquiries welcome. Source access is provided under a mutual NDA during serious due diligence.
