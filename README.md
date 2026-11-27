# CLOUD-CPU

## Purpose

Repository boundary for CPU-oriented batch compute in the Symbiotyc Compute Federation. This repository is a bootstrap surface; it does not yet contain a production scheduler, worker pool, or job service.

## Execution model

- Linux CI validation uses GitHub-hosted `ubuntu-24.04` runners.
- Production CPU workers will be registered separately as persistent Linux workers after the Worker Registry and dispatch API are available.
- Do not add self-hosted runners to public pull-request workflows.
- Do not place cloud credentials or long-lived secrets in this public repository.

## Baseline

The Linux CI workflow validates the README baseline and emits a run receipt. This proves that GitHub Actions executed on a hosted runner; it does not prove that a production CPU worker executed a compute job.

## Planned integration

This repository will consume the versioned JobIntent / TaskRequest contract, declare capabilities and resource limits, return TaskResult plus an execution receipt, and publish artifacts through the federation artifact contract. These services remain unimplemented until the shared control plane is deployed.
