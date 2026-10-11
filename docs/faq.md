# Frequently asked questions about the open-source AnythingLLM alternative from Kortix

Kortix is the open-source AI Operating System, and it is the alternative for teams that outgrow a document-chat app. AnythingLLM is a local-first app for chatting with your documents. These answers cover the questions buyers ask before choosing between them.

## Is Kortix open source?

Yes. Kortix is the open-source AI Operating System, and its source is public. The line is "Open source. Read it, fork it, audit it." You can read, fork, and audit the code, and you can run it on your own infrastructure without asking a vendor for access. The code is at [Kortix on GitHub](https://github.com/kortix-ai/suna).

## Is AnythingLLM open source?

Yes. AnythingLLM is open source and MIT licensed, and its source is public on [its repository](https://github.com/Mintplex-Labs/anything-llm). Its own [site](https://anythingllm.com/) says the project is built in the open. The desktop app is single-user, multi-user support runs on the Docker deployment, and its configuration and workspaces live inside the application rather than in files you own.

## Can I self-host Kortix for free?

Yes. Self-host is free. You run one Docker Compose stack on your own Linux box with `kortix self-host start`, and you pay your own model and compute bills. You can also run it in your VPC or on your own on-prem network. The managed cloud is the alternative when you would rather not run the server yourself.

## What does a Kortix self-host deployment require?

One Linux server, a domain with A/AAAA records for the domain and `api.<domain>`, ports 80 and 443 open, a sandbox provider key, and your own model key. Sessions run on a separate sandbox provider that calls back to the instance, and the stack bootstraps its images from a public registry. The [self-hosting guide](https://anythingllm-alternative.com/self-hosting-anythingllm-alternative) lists the full set.

## Can I run Kortix and AnythingLLM side by side?

Yes. Self-host is free, so you can run a Kortix project beside your current setup and move one workflow at a time. Your documents stay in AnythingLLM while you copy what you need into the repo, and the old app can stay as a fallback until a workflow is proven. [Moving from AnythingLLM to Kortix](https://anythingllm-alternative.com/migrate-from-anythingllm) lists what transfers and what is rebuilt.

## Does Kortix work with local models?

Yes. Kortix is model-agnostic: any model provider with your own keys, chosen per agent, per session, or per message. You can point it at any OpenAI-compatible endpoint, including one you host yourself, bring a key from a major provider, or sign in with the ChatGPT plan you already pay for. The model choice stays yours.

## How is Kortix different from AnythingLLM?

AnythingLLM is a local-first app for chatting with your documents, and its state lives in a workspace inside the app. Kortix is the open-source AI Operating System: agents, skills, company memory, and connectors in one git repo you own, each session on its own cloud computer, and work landing through a change request a person approves. The difference is scope, a workspace or a repository.

## Where is my configuration stored in Kortix?

In the git repo. Agents are markdown files with a matching `kortix.yaml` block, skills are markdown plus scripts, memory is files that accumulate, and `kortix.yaml` declares the machine image, the connectors, the triggers, and the secret names. You can grep the whole company, diff any change, and roll any part of it back.

## Which one should I choose?

Pick AnythingLLM for private document chat on one machine or one Docker host. Pick Kortix when a team needs agents that act in its tools, one shared body of company knowledge, and a review gate before work lands. The [row-by-row comparison](docs/anythingllm-vs-kortix.md) covers the details, and the [live comparison](https://anythingllm-alternative.com/kortix-vs-anythingllm) is on the site.

Try Kortix at [kortix.com](https://kortix.com).
