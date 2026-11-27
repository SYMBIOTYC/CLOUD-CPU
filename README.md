# CLOUD-CPU

## Purpose

Repository boundary for CPU-oriented batch compute in the Symbiotyc Compute Federation. This repository is a bootstrap surface; it does not yet contain a production scheduler, worker pool, or job service.

## Execution model

- Linux CI validation uses GitHub-hosted `ubuntu-24.04` runners.
- Production CPU workers will be registered separately as persistent Linux workers after the Worker Registry and dispatch API are available.
- Do not add self-hosted runners to public pull-request workflows.
- Do not place cloud credentials or long-lived secrets in this public repository.

## Baseline

The initial CI workflow validates repository metadata and emits a run receipt. It proves that GitHub Actions executed the bootstrap job; it does not prove that a production CPU worker executed a compute job.

## Planned integration

This repository will consume the versioned JobIntent / TaskRequest contract, declare capabilities and resource limits, return TaskResult plus an execution receipt, and publish artifacts through the federation artifact contract. These services remain unimplemented until the shared control plane is deployed.

## Documentation

[CPU worker contract](docs/worker-contract.md)


## Bootstrap CI status

The Ubuntu 24.04 workflow validates the repository baseline and emits a short-lived CI execution receipt. A passing hosted CI run proves only that repository validation executed; it does not prove that a production CPU worker, registry, or dispatcher is deployed.
