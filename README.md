<!-- action-docs-description -->

## Description

Deploy to Scaleway using a Kustomize config

<!-- action-docs-description -->

<!-- action-docs-inputs -->

## Inputs

| parameter                      | description                                                                                                                                                                                    | required | default         |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | --------------- |
| secret-key                     | Scaleway secret key                                                                                                                                                                            | `true`   |                 |
| cluster-id                     | Scaleway Cluster ID. Can be retrieved with `scw k8s cluster list name=$CLUSTER_NAME -o template="{{.ID}}"`.                                                                                    | `true`   |                 |
| region                         | Scaleway region (e.g. "fr-par")                                                                                                                                                                | `true`   |                 |
| docker-namespace               | Scaleway Docker registry namespace (e.g. "my-namespace")                                                                                                                                       | `true`   |                 |
| kustomization-base-dir         | Path to base kustomize directory                                                                                                                                                               | `true`   | kustomize/base  |
| kustomization-dir              | Path to the kustomize directory to apply / deploy (e.g. `kustomize/overlays/production`)                                                                                                       | `true`   |                 |
| create-k8s-namespace           | Create Kubernetes namespace if it does not exist                                                                                                                                               | `true`   | true            |
| image-name                     | Docker image name (e.g. `my-app`)                                                                                                                                                              | `true`   |                 |
| image-tag                      | Docker image tag to deploy (e.g. `0.9.14`)                                                                                                                                                     | `true`   |                 |
| age-secret-key                 | Secret key to decrypt deploy secrets with (e.g. `AGE-SECRET-KEY-123456`)                                                                                                                       | `false`  |                 |
| encrypted-filename             | Filename/subpath inside `kustomization-dir` to a file with age encrypted secrets to decrypt                                                                                                    | `true`   | secrets.env     |
| decrypted-filename             | Filename/subpath inside `kustomization-dir` to which the age encrypted secrets will be decrypted to                                                                                            | `true`   | secrets.env.dec |
| create-image-pull-secret       | Create an image pull secret named "rg.`$region`.scw.cloud", to be referenced in `imagePullSecrets` in a k8s deployment/job                                                                     | `true`   | true            |
| k8s-dry-run                    | Used to set `kubectl` option `--dry-run` Valid values are `none` (default), `client` and `server`.                                                                                             | `true`   | none            |
| pre-deploy-delete-job-selector | Delete objects with `status.successful=1` and the given label (e.g. `autodelete-successful-on-deploy=yes`), before doing the deploy. Useful for e.g. cleaning up a completed db migration job. | `false`  |                 |

<!-- action-docs-inputs -->

<!-- action-docs-outputs -->

<!-- action-docs-outputs -->

<!-- action-docs-runs -->

## Runs

This action is a `composite` action.

<!-- action-docs-runs -->
