# Staging on homelab, promotion to prod by pull request

trading-app runs as **staging** on homelab and **prod** on oci. App CI, using a GitHub App token scoped to `home-ops`, commits each new image digest into staging's values. Promotion copies a validated digest into prod's values through a reviewed pull request. Argo CD Image Updater and Renovate-driven bumps were rejected because they are more magic and give less explicit control over what reaches prod.
