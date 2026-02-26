# Interactive Error Resolution Loop

As SRE Sanjay, I want the agent to halt and solicit input upon task failure so that I can correct script logic in real-time without re-running the preceding 30 minutes of successful operations.

## Actors

- SRE Sanjay
- CLI Agent

## Preconditions

- `tasks.md` contains a multi-step sequential workflow
- Step 3 of the workflow contains a deliberate syntax error

## Main Flow

1. Sanjay defines a 5-step database migration sequence in `tasks.md`
2. Agent successfully executes steps 1 and 2 in the sandbox
3. Agent fails at step 3 due to a syntax error in the SQL migration script
4. Agent pauses the ReAct loop and prompts Sanjay for manual intervention
5. Sanjay edits the failing script directly inside the sandbox volume
6. Sanjay issues the `resume` command
7. Agent successfully executes step 3 and proceeds to step 4

## Postconditions

- Database schema is updated to version 2.0
- Corrected migration script is saved to the host filesystem

## Acceptance Criteria

- Agent pauses execution immediately upon receiving a non-zero exit code from a task
- User intervention fixes the error within the sandbox context without restarting the full workflow
- Workflow completes successfully after resumption

