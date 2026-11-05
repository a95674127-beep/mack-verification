# SIGNING — MACK release attestation key

## Public key (publish freely)

```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIND1595NG9ikCVo4N3B4QaShBLN/gyjj/M337cPMErOw Allen Mack — MACK release signing — 2026-11-02
```

Fingerprint: `SHA256:iKgJ7s1r96fDWGlcPYObuL1cGYJNYL5e1npeF3KSZws`

## What this key is for

This key signs MACK release attestations only (OpenSSH signatures, namespace
`mack-release`). It is not an account credential and grants access to nothing.

## Custody — stated plainly

- Generated November 2, 2026, on the owner's agent workstation, at the
  owner's direction, because the owner works phone-first and has no Linux
  machine of his own.
- The private key was delivered to the owner in the same session it was
  created. **On November 3, 2026, at the owner's direction, the private key
  was stored in the owner's private Google Drive, in a folder named
  "MACK Signing Key" whose permissions were verified owner-only (no shares,
  no public link). The workstation copy of the private key was then
  destroyed (secure shred) the same day, November 3, 2026; only the public
  key remains on the workstation, which is safe to hold. The owner's Drive
  copy — together with the copy delivered to the owner on November 2 — is
  now the key's home.**
- The private key is never committed to any repository and never pasted into
  any chat or AI tool. If the private key file is lost, this key can never
  sign again; a new key would be generated and this document updated.

## Verify the attestation signature

With `ATTESTATION.md`, `ATTESTATION.md.sig`, and an `allowed_signers` file
containing `allenmack` followed by the public key line above:

```
ssh-keygen -Y verify -f allowed_signers -I allenmack -n mack-release -s ATTESTATION.md.sig < ATTESTATION.md
```

Expected result: `Good "mack-release" signature for allenmack with ED25519 key SHA256:iKgJ7s1r96fDWGlcPYObuL1cGYJNYL5e1npeF3KSZws`
— this exact result was produced at signing time, November 2, 2026.
