# SRE Sanjay

**Role:** Senior Site Reliability Engineer (SRE)

Manages infrastructure scalability and reliability for high-traffic enterprise applications, prioritizing automation reliability over speed.

## Environment

Hybrid cloud environment (AWS and On-premise); leads a team of 8 SREs; supports 200+ developers.

## Day in the Life

I start my day reviewing alerts from our 250-node Kubernetes cluster. Around 10:00 AM, I identify a repetitive task: upgrading the OpenTelemetry collector across 15 microservices. Instead of manually editing YAML files or writing a one-off bash script, I create a strict `tasks.md` file listing the upgrade steps and version constraints. I launch the agent in a local Docker sandbox. It executes the first five upgrades successfully but halts on service #6 due to a checksum mismatch. I inspect the signal, manually correct the `requirements.md` definition to account for the legacy architecture of that specific service, and resume the agent. By 2:00 PM, the agent completes the batch. I review the sandbox logs, commit the changes to Git, and trigger the CI/CD pipeline.

## Goals

- Reduce manual toil time by 40% per quarter
- Standardize infrastructure updates across legacy repositories
- Maintain 99.99% system availability during maintenance windows
- Automate complex operational workflows without sacrificing human oversight

## Pain Points

- Context switching between high-level architecture and low-level configuration editing
- Risk of automated scripts propagating errors across production environments
- Time consumed by scaffolding boilerplate code for new services
- Inconsistent environment configurations causing 'works on my machine' issues

## Frustration Quotes

> I spend 15 hours a week writing boilerplate Terraform that a script should handle.

> I don't trust autonomous agents that 'fix' code without asking; I need them to stop and let me drive when things get ambiguous.

> Debugging a runaway script that deleted the wrong resources is my nightmare.

## Adoption Drivers

- Availability of strict sandbox isolation to prevent production drift
- Ability to manually intervene (halt-and-signal) rather than debug opaque AI logic
- Integration with existing local CLI toolchains
- Support for standard markdown definition files

## Success Metrics

- Reduction in Toil (manual repetitive work) hours
- Mean Time To Recovery (MTTR) for infrastructure incidents
- Number of successful automated change executions
- Deployment frequency consistency

## Tools & Technologies

- Kubernetes (K8s)
- Terraform
- Prometheus
- Bash/Python scripting
- AWS CLI

