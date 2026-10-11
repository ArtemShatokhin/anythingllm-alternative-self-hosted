# Why self-host an open-source AI Operating System instead of renting a chat window

Self-hosting decides who owns the model calls, the memory, and the configuration. Kortix is the open-source AI Operating System that puts all three in one git repo you own, so a team keeps the platform rather than renting a chat window from a vendor that holds the setup.

## Two layers to own, and what renting leaves out

Running software yourself lets you own the deployment: the documents, the data, and the machine it sits on. Self-hosting a chat app still leaves a second layer inside the product, where the agents, the memory, the connectors, and the permission rules live. That second layer is the one that decides how a company works.

Kortix moves both layers to the repo. Your agents, their skills, your company memory, the connectors, the triggers, and the definition of the machines are files you can read, version, and diff. Nothing about how the system behaves sits in a vendor's database.

## What a git repo changes

When the configuration is code, a change to how your company works arrives as a diff a person reviews. An agent can edit its own configuration on its session branch and propose the change, and a person approves it.

The repo also makes the system portable and reversible. You can grep the whole company, roll any part of it back, and hand a new teammate the whole setup with a clone. `kortix.yaml` declares the machine image, the connectors, the triggers, and the secret names, so the shape of the system travels with the code.

## What stays behind when you rent

The lab-hosted products, including Claude Cowork and ChatGPT Work, run on their cloud, on their models, and keep your configuration in their product. Their version of an AI Operating System is real and it improves quickly. What a company does not get from them is ownership of the setup that runs its work.

Renting buys a fast start and someone else's operations. The cost is that the memory, the permissions, and the configuration that accumulate stay on the vendor's side of the wall, and the system is theirs to change.

## Self-host is free, the bills are yours

Kortix self-host is free. You run one Docker Compose stack on your own Linux box, and you pay your own model and compute bills. Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Any model provider works with your own keys, so the model decision stays a line item you control.

Owning the platform carries its own obligations. You run the box and keep it reachable, because each session's sandbox calls back to it, and updates are automatic unless you pin a version. A security review that needs a tighter topology is scoped with the Kortix team.

## What AnythingLLM gets right

AnythingLLM is open source and MIT licensed, and it takes the ownership idea seriously at the document layer. It runs a private assistant entirely on your computer, keeps your documents local, and ships a Docker deployment for a small shared instance. For private document chat, it is a strong choice.

The gap is scope. AnythingLLM keeps its configuration and workspaces inside the application, and its agents run inside the same instance. Kortix keeps the system in a repo the team owns, gives each session an isolated cloud computer, and gates the work through review.

## How to decide

- If the work is document chat and retrieval, self-hosting AnythingLLM is a good answer.
- If a team needs agents that act in its tools and one shared body of company knowledge, self-hosting Kortix keeps that work and its configuration as files.

To see what a self-hosted Kortix stack requires, the [self-hosting guide](https://anythingllm-alternative.com/self-hosting-anythingllm-alternative) lists the prerequisites and the command. For the ownership question across open-source tools, [why open source matters here](https://anythingllm-alternative.com/open-source-anythingllm-alternative) covers what each project lets you keep.

Try Kortix at [kortix.com](https://kortix.com).
