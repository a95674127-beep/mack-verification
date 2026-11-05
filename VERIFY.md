# Verify the attestation yourself

Everything you need is in this repository. You need any system with OpenSSH
(`ssh-keygen` ships with OpenSSH on Linux, macOS, and Windows).

## 1. Get the files

```bash
git clone https://github.com/a95674127-beep/mack-verification.git
cd mack-verification
```

(Or download `ATTESTATION.md`, `ATTESTATION.md.sig`, and `allowed_signers`
from the repo page — those three files are all the check requires.)

## 2. Run the verification

```bash
ssh-keygen -Y verify -f allowed_signers -I allenmack -n mack-release -s ATTESTATION.md.sig < ATTESTATION.md
```

## 3. Expected output

```
Good "mack-release" signature for allenmack with ED25519 key SHA256:iKgJ7s1r96fDWGlcPYObuL1cGYJNYL5e1npeF3KSZws
```

That line means the `ATTESTATION.md` in front of you is byte-for-byte the
statement the owner signed on November 2, 2026, with the key whose public
half is `allen-mack-release.pub` in this repo — and that not one character
of it has changed since.

If even one byte of `ATTESTATION.md` is altered, the command fails with a
signature-verification error instead. Try it: copy the file, change a
single digit in a copy, and verify the copy — it will not pass.

## What this does and does not prove

- It **does** prove the attestation text is authentic and untampered, and
  binds the verification record to the owner's release key.
- It does **not**, by itself, re-run the tests. The attestation cites the
  exact commit and CI run behind every number so the record can be checked
  against the source repository during due diligence (source access under
  mutual NDA), and the full evidence archive with SHA-256 manifests ships
  with the buyer's evidence pack.
