# Pre-Deployment Governance Enforcement

As Platform Elena, I want to test infrastructure templates against security policies in a sandbox so that I prevent 100% of non-compliant configurations from reaching staging environments.

## Actors

- Platform Elena
- CLI Agent

## Preconditions

- `requirements.md` contains strict security governance policies
- Proposed infrastructure template contains a known security violation

## Main Flow

1. Elena defines strict ingress rules (Port 443 only) in `requirements.md`
2. Elena interacts with the agent to simulate a deployment containing Port 22 open access
3. Agent attempts to create the security group in the ephemeral sandbox
4. Agent detects deviation from the security baseline
5. Agent halts execution and signals a `POLICY_VIOLATION` error
6. Elena updates the template to remove Port 22 access
7. Agent resumes and verifies compliance

## Postconditions

- Architecture implementation matches documentation strictly
- Non-compliant resource requests are rejected

## Acceptance Criteria

- Agent detects 100% of security group violations defined in `requirements.md`
- Provisioning process halts within 500ms of detecting a policy violation
- Sandbox logs provide exact line number of the drift source

