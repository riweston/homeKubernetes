# Bootstrap

## Overview

This `kustomization.yml` file is used to bootstrap the initial out of the box required components for the cluster

The following components are hard requirements just to get the cluster operating as expected

* ArgoCD
* Sealed Secrets

Once bootstrapped the cluster should begin deploying all applications in `./argocd/`

## Gotchas

At present I haven't worked out how to manage ArgoCD with ArgoCD, all updates should probably be run from this directory.

Sealed Secrets is managed by ArgoCD, you see this in the `kustomization.yml` path.

ArgoCD seems to have issues with nested kustomizations, as such for bootstrapping we specify the file rather than the directory for Sealed Secrets (which is also missing a `kustomization.yml`). To build the config we must override this non-standard structure as below.

```shell
$ kustomize build --load_restrictor none . | kc apply -f -
```
