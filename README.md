<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/wunderlab-ai/brand/main/svg/wunderlab-logo-horizontal-reversed.svg">
    <img alt="Wunderlab" src="https://raw.githubusercontent.com/wunderlab-ai/brand/main/svg/wunderlab-logo-horizontal.svg" width="420">
  </picture>
</p>

<p align="center">
  A local-first AI workspace where a curator-led network of specialized agents runs on your own hardware.
</p>

<p align="center">
  <a href="https://wunderlab.eu">Website</a> ·
  <a href="docs/">Docs</a> ·
  <a href="CONTRIBUTING.md">Contributing</a>
</p>

> **Status: early development.** This README describes the design and goals of Wunderlab. Features land in the open, and parts of what's described here are not built yet. Watch the repository and the issue tracker for progress.

## The idea

Most AI tools send your work to someone else's servers and rely on one very large model. Wunderlab bets on a different approach: **smarter task splitting, curation, and specialization let models you can run yourself do work that usually needs a hosted giant.**

A *curator* reads your request, works out what you actually mean, and plans the work. Specialized *roles* (conversation, research, data analysis, workspace analysis, coding, translation, and more) carry it out, delegating to other agents until every step is small enough for one agent to do well. Everything runs on your machine, within limits you set.

The claim is testable, so we ship the tools to test it: [`bench`](https://github.com/wunderlab-ai/bench) lets you reproduce quality, speed, and cost comparisons on your own hardware.

## What Wunderlab does

**Agents and orchestration**
- A curator that plans, recommends roles and models, and makes sure you always get an answer
- Large networks of specialized agents that can delegate to each other
- Hard step budgets and timeouts per agent, with automatic retries and model rotation on failure
- Model-to-model delegation, model comparison, and prompt crafting

**Control over your hardware**
- Load-balanced inference across your CPUs and GPUs (CUDA and OpenCL)
- A hard cap on concurrent models, and user-defined ceilings on the share of CPU, memory, and GPU Wunderlab may use
- Live performance and usage views

**Safe by design**
- Sandboxed tools instead of sandboxed agents: tools run through Wunderlab's own runtime and can only reach what you have linked into the conversation
- Changes to your files are reviewed and approved by you before they are applied
- Accounts can only be created by the owner, so remote access stays under your control
- Agent bug reporting to help improve roles and models

**A research lab on your desk**
- Conversational memory stored locally
- Import models and datasets from Hugging Face, quantize models, and train new ones
- Casual tools for everyday use and developer tools for going deeper

**Everywhere you work**
- Web interface, desktop app, and mobile apps

## How the pieces fit

| Repository | What it is |
|---|---|
| [`wunderlab`](https://github.com/wunderlab-ai/wunderlab) (this repo) | Runtime (scheduler, agents, daemon, CLI), Laravel server, web app, and deployment |
| [`contracts`](https://github.com/wunderlab-ai/contracts) | API and event definitions shared by every component |
| [`core`](https://github.com/wunderlab-ai/core) | Foundation library for the C++20 runtime |
| [`engine-api`](https://github.com/wunderlab-ai/engine-api) | The engine interface for inference, training, and quantization |
| [`engine-cuda`](https://github.com/wunderlab-ai/engine-cuda) · [`engine-opencl`](https://github.com/wunderlab-ai/engine-opencl) | GPU backends |
| [`roles`](https://github.com/wunderlab-ai/roles) | Agent roles, curator instructions, and network presets as data |
| [`bench`](https://github.com/wunderlab-ai/bench) | Reproducible benchmark harness |
| [`ui`](https://github.com/wunderlab-ai/ui) | Shared React components and design tokens |
| [`brand`](https://github.com/wunderlab-ai/brand) | Logos, icons, and brand guidelines |

Repositories listed here are added as they are extracted from this one.

## Getting started

Wunderlab has no stable release yet. To follow along or contribute, clone with submodules:

```bash
git clone --recurse-submodules https://github.com/wunderlab-ai/wunderlab
cd wunderlab
git submodule update --init --recursive   # if you forgot --recurse-submodules
```

Build instructions will be added here with the first alpha. The toolchain is:

| Part | Tools |
|---|---|
| Runtime | C++20, CMake 3.28+, Ninja, a CUDA or OpenCL SDK for GPU builds |
| Server | PHP, Composer, Laravel |
| Web and apps | Node.js, pnpm, Next.js, React, Tailwind |

## Contributing

Issues, ideas, and pull requests are welcome. Start with [CONTRIBUTING.md](CONTRIBUTING.md). To report a security problem, please follow [SECURITY.md](SECURITY.md) instead of opening a public issue.

## License

The Wunderlab software is licensed under the [Apache License 2.0](LICENSE).

The Wunderlab name and logos are not covered by that license. See the [brand repository](https://github.com/wunderlab-ai/brand) for the Brand Assets License.

---

<p align="center">Made with love from 🇳🇱 · <a href="https://wunderlab.eu">wunderlab.eu</a></p>
