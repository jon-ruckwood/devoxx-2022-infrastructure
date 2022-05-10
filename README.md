# devoxx-2022-infrastructure

Simulates a "GitOps" repository, for example, that would be used by a tool such as ArgoCD to keep a Kubernetes cluster in sync with version control. 

Any changes to this repository would then be reflected in the environment, e.g. if the image tag is updated in this repository, then it will be updated in the Kubernetes cluster. To find out more about GitOps see [here](https://www.gitops.tech).

**NOTE:** This is only a model of updating an image tag in a fictional Helm chart using GitHub Actions. You should not use any manifests defined in this repository.

## Workflows

* Update Image Tag – can be run manually or runs automatically when invoked by the [`jon-ruckwood/devoxx-2022-service`](https://github.com/jon-ruckwood/devoxx-2022-service) repository, this will:
  * Using `yq` set the new image tag in `values.yaml`
  * Using a local composite action:
    * Raise a PR with the change
    * Set "auto-merge on the PR
    * Actions will approve the PR, causing it to be automatically merged
