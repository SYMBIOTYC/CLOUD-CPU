# CPU Worker Boundary

## Purpose
Define the execution contract for CPU-oriented batch work. This repository does not provision production workers.

## Worker contract
A future worker must register a stable worker ID, software version, OS/architecture, capability set, concurrency limit and resource ceilings. Heartbeats must include health, free capacity and lease renewal. Workers must support drain, revoke and offline transitions.

## Job execution
Accept only versioned JobIntent/TaskRequest payloads. Validate schema, size, timeout, CPU/memory/disk ceilings and allowed operation before execution. Use an idempotency key and return TaskResult with exit status, timestamps, artifact manifest and SHA-256 checksums.

## Security
- Public pull requests run only on ephemeral GitHub-hosted runners.
- Never register a production self-hosted runner to this public repository's PR workflow.
- Do not store cloud keys, SSH private keys or production tokens in Git.
- Production cloud access must use short-lived, narrowly scoped OIDC federation after trust-policy review.

## Current status
The bootstrap CI workflow is repository validation only. No production CPU worker, registry, dispatcher or job API is claimed as deployed.
