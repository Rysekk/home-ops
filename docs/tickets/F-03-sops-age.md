# F-03: SOPS + age setup

**Refs**: ADR-0004 · **Depends on**: F-01

SOPS is only for the few secrets that must live in git (the ESO bootstrap credential, and later Terraform variables).

## Acceptance criteria
- [ ] age key pair generated. The **private key is stored in the password manager** and never committed, and its path is documented.
- [ ] `.sops.yaml` with creation rules: files matching `*.sops.yaml` encrypt only `data`/`stringData` (via `encrypted_regex`).
- [ ] Round trip verified: encrypt a dummy secret, commit it, decrypt it on another machine using the key from the password manager.
- [ ] Runbook `docs/runbooks/sops.md`: how to encrypt, edit, and rotate the key.
