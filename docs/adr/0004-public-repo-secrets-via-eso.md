# Public repo, secrets via External Secrets Operator, SOPS only for bootstrap

`home-ops` is public. No secret is ever committed in plaintext. Runtime secrets are pulled into clusters by **External Secrets Operator** from an external store (Bitwarden Secrets Manager or Infisical). **SOPS + age** encrypts only the few files that must live in git, such as the ESO bootstrap credential and Terraform variables. GitHub push protection rejects pushes that contain known secret formats, and every pull request runs gitleaks and a check that each `*.sops.yaml` file is encrypted. There are no local hooks to install.

## Considered Options

- **Private repo**: hides little (open ports are found by scanners anyway) and gives up showing the work.
- **SOPS everywhere**: the norm with Flux, but Argo CD has no native decryption and would need KSOPS or helm-secrets, which is known friction. Key rotation is also painful.
- **ESO + external store, minimal SOPS** (chosen): integrates cleanly with Argo CD and is the common enterprise pattern.

## Consequences

The age private key and the ESO bootstrap credential are the root of trust. They must be backed up outside the lab, in a password manager.
