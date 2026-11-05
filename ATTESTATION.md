# OWNER RELEASE ATTESTATION — MACK Stack (AI Infinity Force One)

**Owner:** Allen Mack, sole human author and owner
**Repository:** `a95674127-beep/ai-infinity-force-one-vault` (private)
**Date of attestation:** November 2, 2026

## Release state attested

- Main head at signing: **`d60e82d`** — a CI commit changing only the generated
  file `assets/ledger_demo_output.json` (1 insertion, 1 deletion, `[skip ci]`).
- No source file has changed since commit **`5233f027`** (the loom commit).
  Every code verification below therefore applies to the code at head exactly;
  each run is cited against the commit it actually ran on.

## Verification results attested

1. **Test suite:** 226 passed / 0 failed on commit `8359c2c9`, and 226/226
   again on the loom-modified tree (lockfile of 390 crates).
2. **Fuzzing:** CI Fuzzing run #46 SUCCESS on `8359c2c9`, job logs read in
   full — six targets, 2,639,356 executions in total, zero crashes
   (pov_batch 605,993; ingest_pov 474,703; audit_chain 86,805;
   lane_transitions 701,358; yara 703; entropy 769,794). Push run #48 on
   `5233f027` and scheduled run #49 (Nov 2, 2026) also SUCCESS.
3. **Concurrency models (loom):** 3 models in `tests/loom_sibling.rs` against
   the real `SiblingOwnership` API — 3/3 pass (commit `5233f027`).
4. **Continuous integration:** CI run #326 on `206578bd` — SUCCESS, all four
   jobs: test, Dependency Audit, Test Coverage, ledger-demo (output pushed
   on attempt 1). Lint run #16 on `206578bd` — SUCCESS.
5. **Dependency posture:** `cargo audit` exits 0 under the documented ignore
   list. The sole underlying vulnerability is rsa RUSTSEC-2023-0071
   (Marvin side-channel), transitive via yara-x, with no upstream fix; no
   RSA decryption exists anywhere in first-party code (see RSA-EXPOSURE.md).

## Evidence binding

The detailed evidence bundle accompanies this attestation. Its
pre-attestation file manifest is preserved as `EVIDENCE-SHA256SUMS.txt`,
SHA-256: `d85ada1e123accaeda4eb03d10c173530faafae2e8d999c499747d1b44f31621`.

## Statement

I, Allen Mack, attest that the verification results summarized above and
detailed in the accompanying evidence bundle are true and accurate to the
best of my knowledge; that I am the sole human author and owner of this
software, developed with AI assistance used as a tool and disclosed as such;
and that no patent application covering this software has been filed or is
pending.

Signed: Allen Mack — via the MACK release signing key
Key fingerprint: SHA256:iKgJ7s1r96fDWGlcPYObuL1cGYJNYL5e1npeF3KSZws
Signature: ATTESTATION.md.sig (OpenSSH Ed25519, namespace "mack-release"; see SIGNING.md to verify)
