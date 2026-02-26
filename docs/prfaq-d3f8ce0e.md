# Amazon Announces DevOps Sandbox Agent: Safe, Autonomous Infrastructure Automation with Human-in-the-Loop Control

## Press Release

SEATTLE--(BUSINESS WIRE)--November 15, 2024--Amazon Web Services, Inc. (AWS), an Amazon.com, Inc. company (NASDAQ: AMZN), today announced the general availability of the Amazon DevOps Sandbox Agent, a new intelligent automation service designed to act as a force multiplier for Site Reliability Engineers (SREs) and Platform teams. The DevOps Sandbox Agent transforms static documentation into compliant infrastructure code inside a secure, isolated environment, allowing engineers to automate complex provisioning tasks without sacrificing control or safety.\n\nFor years, SREs and Platform Engineers have struggled with the 'last mile' of infrastructure automation. Translating high-level architectural designs into functioning Infrastructure-as-Code (IaC) involves hours of writing boilerplate, manual syntax checking, and the constant risk of 'works on my machine' configuration drift. Furthermore, as organizations scale, ensuring that every microservice adheres to strict security governance often becomes a bottleneck, forcing senior engineers to manually review templates.\n\nAmazon DevOps Sandbox Agent addresses these challenges by providing an AI-driven environment that builds, tests, and validates infrastructure based on natural language or markdown specifications. Unlike standard coding assistants that simply suggest text, the DevOps Sandbox Agent executes commands within a local Dockerized sandbox. It interprets `design.md` files to scaffold services, compares intended changes against `requirements.md` governance policies, and verifies resource integrity before any code touches a repository.\n\n\"The cognitive load on SREs has reached a tipping point. They are expected to maintain mental maps of complex systems while perfectly executing low-level configuration syntax,\" said Deepak Singh, Vice President of Compute Services at AWS. \"With Amazon DevOps Sandbox Agent, we are giving engineers a safe space to automate. It handles the scaffolding and validation grunt work, but crucially, it knows when to stop and ask for help. It turns documentation into deployable reality without the risk.\"\n\nCrucially, the Agent employs a \"Halt and Signal\" philosophy. In the complex world of DevOps, an AI guessing blindly can be disastrous. If the Agent encounters an error—such as a failing database migration script or a security policy violation—it freezes the sandbox state and alerts the engineer. This allows the user to intervene, correct the specific script within the sandbox, and resume execution, preserving the progress of successful steps.\n\n\"In the past, bootstrapping a new microservice took us nearly four hours of scaffolding and compliance checking,\" said Elena Rodriguez, Principal Platform Engineer at TechStream Solutions. \"With the DevOps Sandbox Agent, we define our architecture in markdown and let the Agent build the Terraform boilerplate in a sandbox. It catches compliance issues, like open SSH ports, before I even see the code. We’ve cut our setup time down to under 30 minutes per service.\"\n\n**How It Works**\n\nThe Agent is a CLI tool that integrates with your existing terminal workflow. Users define their architecture in a `design.md` file and resource limits in `requirements.md` at the root of their repository. Upon running `agent-cli run --sandbox`, the tool spins up an isolated container. It analyzes the specifications, generates the necessary IaC (such as Terraform or CDK), and executes planning commands to verify the graph integrity. If the Agent detects a deviation from governance standards or hits a syntax error, it pauses and solicits user input, ensuring human oversight remains central to the process.\n\n**Availability**\n\nAmazon DevOps Sandbox Agent is available today in preview in US East (N. Virginia), US East (Ohio), and US West (Oregon). To learn more and download the CLI, visit aws.amazon.com/devops-sandbox-agent.

## Customer FAQ

### What is the Amazon DevOps Sandbox Agent?

Amazon DevOps Sandbox Agent is a command-line tool that combines generative AI with an isolated execution environment. Unlike standard code assistants that only suggest syntax, the Agent autonomously executes multi-step operational tasks—such as provisioning Terraform resources, running database migrations, or enforcing governance policies—inside a secure local container. It interprets high-level specifications from your project documentation (like markdown files) and performs the heavy lifting of scripting and validation.

### How does the Agent handle errors or failed deployment steps?

We prioritized safety and control over autonomous creativity. The Agent operates on a 'Halt and Signal' logic. If the Agent encounters an API error, a syntax failure, or a policy violation during execution, it pauses immediately and alerts the user. Returns control to you to inspect the sandbox state, manually fix the specific script or configuration, and issue a 'resume' command. This ensures the AI never hallucinates a fix that could degrade your infrastructure.

### Can I use the Agent to enforce security policies before deployment?

Absolutely. This is a core feature designed for Platform Engineers. You can define governance standards (e.g., 'Port 443 only') in a `requirements.md` file. The Agent acts as a pre-deployment gatekeeper, simulating infrastructure changes in the sandbox against your defined policies. If a generated template violates these rules (like opening Port 22), the Agent signals a violation and halts before the code can be committed to your repository.

### What are the technical prerequisites for using the Agent?

The Agent requires Docker to be installed on your local machine to run the sandboxed environment. It supports AWS Cloud Development Kit (CDK), Terraform, Pulumi, and standard bash scripting. It is optimized to interpret architectural diagrams and specifications written in Markdown.

## Internal FAQ

### How does this differentiate from Amazon Q or GitHub Copilot?

While services like Amazon Q Developer assist with code generation alongside the developer in the IDE, DevOps Sandbox Agent focuses on 'Agency' and 'Execution.' It bridges the gap between generating code and running it. By providing an ephemeral sandbox, we allow the model to test its own code, fail safely, and allow the human to debug the running state. This targets the 'SRE' and 'Platform' personas who need reliability and validation more than just raw code speed.

### What prevents the Agent from hallucinating destructive infrastructure commands?

Safety is built into the architecture via the 'Sandbox' constraint and 'Halt and Signal' behavior. The Agent has no direct access to production environments by default; it operates solely within a local containerized environment. It cannot self-correct architectural specs, meaning it won't hallucinate a workaround to a hard security limit. All final artifacts must be manually committed by the engineer to their version control system, maintaining the human as the final authority.

### What is the pricing model?

The service follows a consumption-based model. Customers are charged for the underlying compute resources used by the sandbox (if run on AWS remote instances) and the token inference costs for the Agent's reasoning loop. There is a free tier for local execution where customers utilize their own hardware for the sandbox, paying only for the API calls to the LLM backend.

### What is the strategic value for AWS?

Our goal is to reduce the 'Time-to-Infrastructure' for enterprise teams. By automating the boilerplate scaffolding and validation steps, we believe we can reduce the time required to bootstrap new services by 40-50%. This creates a sticky ecosystem where customers store their architecture specs as Markdown in CodeCommit or S3, driving deeper integration with AWS management tools.

