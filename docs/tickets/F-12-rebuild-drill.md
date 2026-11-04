# F-12: Rebuild-from-scratch drill

**Refs**: ADR-0003 · **Depends on**: F-11

Prove the foundation is actually code: wipe it and bring it back from git alone.

## Acceptance criteria
- [ ] Uninstall k3s on both nodes, or reinstall the OS.
- [ ] From the runbook alone, run Ansible, then wait for Argo. The cluster returns to the same state with no manual `kubectl`.
- [ ] Time to rebuild measured and written down.
- [ ] Runbook `docs/runbooks/rebuild-homelab.md` written, and every surprise fixed in code (not in the runbook).
