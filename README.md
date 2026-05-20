# svc-hello-deploy

Kubernetes manifests for `svc-hello`. ArgoCD watches this repo; the CI in `svc-hello-app` bumps the image tag here on every push to `main`.

## Layout

```
base/
  namespace.yaml
  deployment.yaml
  service.yaml
  kustomization.yaml    # the image tag lives here, kustomize edit set image updates it
```

## Rendering locally

```sh
kustomize build base | less
```

## What ArgoCD points at

`base/` directly, with the Application's `path: base` and `repoURL: https://github.com/afontan/svc-hello-deploy.git`.
