# Automated Microservice Infrastructure Scaffolding

As SRE Sanjay, I want to generate compliant infrastructure-as-code boilerplate from markdown specifications so that I reduce persistent service bootstrapping time by 3.75 hours per service.

## Actors

- SRE Sanjay
- CLI Agent

## Preconditions

- Docker daemon is active
- `design.md` specifies a 3-tier architecture pattern
- AWS credentials mounted safely to sandbox context

## Main Flow

1. Sanjay places architecture specs in `design.md` and resource limits in `requirements.md` within the repo root
2. Sanjay executes `agent-cli run --sandbox`
3. Agent interprets specs and generates Terraform boilerplate within the isolated container
4. Agent runs `terraform plan` to verify resource graph integrity
5. Agent commits generated artifacts to the local repository

## Postconditions

- Valid Infrastructure-as-Code files exist in the target directory
- Sandbox environment terminates completely

## Acceptance Criteria

- CLI parses 3 markdown inputs ($requirements.md, $design.md, $tasks.md) in under 5 seconds
- Generated Terraform configurations pass `terraform validate` with 0 errors
- Sandbox environment creates 100% of specified resources without network leakage to host
- Agent reduces scaffolding lead time from 4 hours to 15 minutes

