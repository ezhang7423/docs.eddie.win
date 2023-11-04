---
description: Some options for running experiments automatically to save you a lot of time
---

# CI/CD

At a high level, I've experimented with two options so far:

### Fixed scale github actions (supports GPU):

{% embed url="https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners" %}

Some tutorials below on adding GPU (TODO, need to setup in research\_project)

{% embed url="https://iterative.ai/blog/cml-self-hosted-runners-on-demand-with-gpus" %}

{% embed url="https://st6.io/blog/jetson-nano-self-hosted-runner/" %}

### Autoscaling github actions (doesn't support GPU)

The following script will setup an autoscaling kubernetes cluster on an Ubuntu instance with docker already installed.&#x20;

The directions are taken from ARC [here](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/quickstart-for-actions-runner-controller).

{% @github-files/github-code-block url="https://github.com/ezhang7423/research_project/blob/main/scripts/setup-autoscaling.bash" %}

This is an example CI file that makes use of the cluster that is setup above.

{% @github-files/github-code-block url="https://github.com/ezhang7423/research_project/blob/main/.github/workflows/autoscaling-ci.yml" %}

