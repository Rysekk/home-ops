# Each cluster alerts on its own; central observability is best-effort

Every cluster runs its own Prometheus and Alertmanager, so prod alerting never depends on the house. The homelab hosts a central LGTM stack that clusters `remote_write` to over Tailscale for cross-cluster dashboards and long-term data. If that link is lost, only visibility is degraded, never alerting. An external dead-man's switch (healthchecks.io) catches the case where alerting itself dies.
