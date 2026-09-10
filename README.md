# arca-bench-k8s — Kubernetes manifests for Arca Bench - Test & Evaluation Laboratory

Deploys the `arca-bench` module with a zero-trust posture:

- `base/` — Kustomize base (namespace, RBAC, deployment, network policies, mTLS).
- `overlays/` — environment overlays (dev / staging / prod).
- `helm/` — equivalent Helm chart.
- `policies/` — Kyverno admission policies and Falco runtime rules.

## Rules
- No secret in clear text: everything sensitive comes from Vault via the
  External Secrets Operator (`base/externalsecrets.yaml`).
- mTLS is STRICT (`base/peerauthentication.yaml`).
- Network default is deny-all; allowances are explicit (`base/networkpolicies.yaml`).

## Deploy
```bash
kubectl apply -k overlays/dev
helm template bench helm/bench
```
