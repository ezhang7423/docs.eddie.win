---
description: Some options for running experiments automatically to save you a lot of time
---

# CI/CD

At a high level, I've experimented with two options so far:

### Fixed scale github actions (supports GPU):

First you need to install the docker nvidia runtime (from the instructions below and [this repo](ci-cd.md#fixed-scale-github-actions-supports-gpu)):

{% embed url="https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html" %}

Try running the following now on a desktop with GPUs:

```
docker run -it --gpus all nvidia/cuda:12.2.2-cudnn8
-runtime-ubi8 nvidia-smi
```

If this returned with the GPU info, the runtime has now been successfully installed!



Next, you'll need to register a runner on this machine by following the below documentation:

{% embed url="https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners" %}

After that, you can go ahead and try running a test-ci run to use GPUs:

{% @github-files/github-code-block url="https://github.com/ezhang7423/research_project/blob/main/.github/workflows/gpu-ci.yml" %}

### Autoscaling github actions (doesn't support GPU)

The following script will setup an autoscaling kubernetes cluster on an Ubuntu instance with docker already installed.&#x20;

The directions are taken from ARC [here](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/quickstart-for-actions-runner-controller).

{% @github-files/github-code-block url="https://github.com/ezhang7423/research_project/blob/main/scripts/setup-autoscaling.bash" %}

This is an example CI file that makes use of the cluster that is setup above.

{% @github-files/github-code-block url="https://github.com/ezhang7423/research_project/blob/main/.github/workflows/autoscaling-ci.yml" %}

