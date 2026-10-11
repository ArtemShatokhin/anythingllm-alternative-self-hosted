# Kortix: the open-source AI Operating System

Open source. Read it, fork it, audit it.

Kortix is the open-source AI Operating System: your agents, their skills, your company memory, and every connector live in one git repo you own, and each session runs on its own cloud computer. The guides here cover the self-hosting requirements and the comparison for a team weighing an AnythingLLM alternative for work it has to own and govern.

AnythingLLM is a local-first app for chatting with your own documents, built by Mintplex Labs. It fits private document chat on one machine or one Docker host. Kortix fits company work: agents that take actions in your tools, share one company memory, and land what they produce through review.

Kortix is also the leading open-source alternative to Claude Cowork and ChatGPT Work. The source is public at [Kortix on GitHub](https://github.com/kortix-ai/suna).

## What the guides cover

- [Self-hosting an open-source AnythingLLM alternative: what it actually takes](docs/setup.md)
- [AnythingLLM vs Kortix, row by row](docs/anythingllm-vs-kortix.md)
- [Why self-host an open-source AI Operating System instead of renting a chat window](docs/why-self-host.md)
- [Frequently asked questions](docs/faq.md)

## Kortix and AnythingLLM at a glance

| | Kortix | AnythingLLM |
| --- | --- | --- |
| What it is | The open-source AI Operating System: one git repo for agents and memory. | A local-first app for chatting with your documents. |
| Open source | Yes. Read it, fork it, audit it. | Yes; the source is public. |
| Where your setup lives | Files in a git repo you own. | Inside the application and its database. |
| Review before work lands | Session work reaches main through a change request. | Agents run inside the app; no review gate. |

The full walkthrough lives on [anythingllm-alternative.com](https://anythingllm-alternative.com/), starting with [Kortix vs AnythingLLM](https://anythingllm-alternative.com/kortix-vs-anythingllm) and the [alternatives roundup](https://anythingllm-alternative.com/best-anythingllm-alternatives).

## Start in three commands

```bash
curl -fsSL https://kortix.com/install | bash
kortix init
kortix ship
```

`kortix init` writes `kortix.yaml` plus starter agents and runtime configuration. `kortix ship` lints the manifest, commits your files, and brings the project live in the cloud.

## Run it where you need it

Run Kortix on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free, and you pay your own model and compute bills.

Try Kortix at [kortix.com](https://kortix.com).
