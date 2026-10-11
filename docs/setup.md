# Self-hosting Kortix, the open-source AI Operating System, as an AnythingLLM alternative

Kortix is the open-source AI Operating System, and self-hosting it as an AnythingLLM alternative means one Linux box, a public domain, and one Docker Compose stack. AnythingLLM's Docker deployment needs a host with Docker and an external model provider. Both projects are open source, so the difference is what your self-hosted instance keeps: a set of workspaces, or a git repo that is the company.

## Prerequisites, side by side

| Requirement | Kortix | AnythingLLM Docker |
| --- | --- | --- |
| Host | One Linux box | A webserver or cloud host with Docker |
| Domain | A domain with A/AAAA records for it and `api.<domain>` | Whatever your deployment maps |
| Network | Ports 80 and 443 open | Depends on your Docker mapping |
| Keys | A sandbox provider key and a model key | An external LLM provider key |
| Images | Pulled from docker.io | Pulled from a container registry |
| Multi-user | Built in | Docker only; the desktop app is single-user |
| Stack | One Docker Compose stack, no Redis or worker | Docker; server, frontend, and collector |

Kortix's self-host prerequisites and stack shape are documented in the [self-hosting guide](https://anythingllm-alternative.com/self-hosting-anythingllm-alternative). AnythingLLM's Docker requirements and its desktop split come from its own [installation overview](https://docs.anythingllm.com/installation-docker/overview).

## AnythingLLM: two shapes with two requirements

AnythingLLM ships as a desktop app and as a Docker deployment, and its own documentation treats them as different products.

The desktop app installs on macOS, Windows, or Linux with one click, runs entirely on the machine, and includes a built-in LLM provider. It is single-user, and AnythingLLM's docs steer anyone who does not need multi-user support to it.

The Docker deployment is the one that adds multi-user support, user management, workspace access management, password protection, white-labeling, and embeddable chat widgets. AnythingLLM's own feature table marks all of those as Docker-only, and it does not ship the built-in LLM provider on Docker, so you supply an external provider. Multi-user mode is also a one-way switch: its security documentation warns that once you enable it, you cannot return to single-user mode.

The deployment choice is fixed by the use case before you start. [AnythingLLM's docs](https://docs.anythingllm.com/features/security-and-access) hold the roles (Admin, Manager, Default) and the mode rules.

## Kortix: one stack from the CLI

Kortix is the open-source AI Operating System, and self-hosting it is one Docker Compose stack started from the CLI.

1. Provision the box. You need one Linux server, a domain with A/AAAA records for the domain and `api.<domain>`, ports 80 and 443 open, a sandbox provider key, and your own model key.
2. Install the CLI. Run `curl -fsSL https://kortix.com/install | bash` to fetch a prebuilt binary for macOS or Linux. Windows is not supported natively; use WSL.
3. Initialize the instance. `kortix self-host init --domain kortix.example.com` writes the instance configuration.
4. Start it. `kortix self-host start` brings up the stack. There is no Redis and no separate worker.
5. Point sessions at a provider. `kortix self-host configure` sets the sandbox provider once. The default is Daytona; Platinum and E2B are also supported.
6. Connect models and GitHub. Connect your model provider in the app. GitHub connects in the dashboard under Settings, then Git. The first run asks six things and no model key.

Two constraints are worth stating before you commit. The instance has to be reachable, because each session's sandbox calls back to it, and the one-shot bootstrap pulls its images from docker.io. If your security review needs a tighter topology, Kortix scopes that with you.

## What a repo-owned company OS adds

Self-hosting a document-chat app keeps answers. Self-hosting Kortix keeps the work and the configuration that produced it.

Your agents, their skills, your company memory, the connectors, the triggers, and the definition of the machines all live as files in one git repo you own. `kortix.yaml` declares the machine image, the connectors, the triggers, and the secret names. You can grep the whole company, diff any change, and roll any part of it back.

Each session runs on its own isolated cloud computer and its own branch, and thousands can run in parallel on one config. When a session has commits ready, the agent opens a change request, and merge is default-deny for agents, so a person reads the diff before it reaches main.

Connectors reach 3,000+ apps in a click, plus MCP, OpenAPI, Postman, GraphQL, and raw HTTP. Connector credentials are brokered server-side and never enter the machine, and each tool call is set to Allow, Ask, or Block, down to the arguments of the call.

For teams that answer to a security review, Kortix adds per-resource permissions for people and agents, roles, groups, and an audit trail, SAML 2.0 single sign-on and SCIM 2.0, and secrets encrypted at rest with a key per project.

## Which one to self-host

- One person, private document chat, on a laptop: AnythingLLM desktop.
- A small group sharing one instance for document chat: AnythingLLM Docker.
- A team that needs agents acting in its tools, one shared memory, and a review gate before work lands: Kortix.

If you already run AnythingLLM, [what moves to Kortix](https://anythingllm-alternative.com/migrate-from-anythingllm) lists the parts that carry over and the parts you rebuild as files. The [self-hosting guide](https://anythingllm-alternative.com/self-hosting-anythingllm-alternative) covers the install paths, the update schedule, and the backup model.

Try Kortix at [kortix.com](https://kortix.com).
