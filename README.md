<p align="center">
  <a href="https://briq.cloud"><img src="assets/logo.svg" width="96" height="96" alt="briq"></a>
</p>

<h1 align="center">briq</h1>

<p align="center"><b>Give your agent its own cloud.</b><br>
Postgres, Redis, a sandbox to run code in, an app from a GitHub repo, or any Docker image, each on its own microVM, in one MCP call.</p>

<p align="center">
  <a href="https://briq.cloud/?utm_source=github&amp;utm_medium=readme"><img src="https://img.shields.io/badge/Get_started-briq.cloud-f06a3c?style=for-the-badge" alt="Get started on briq.cloud" height="32"></a>
</p>

<p align="center">
  <a href="https://briq.cloud/docs">Docs</a> ·
  <a href="https://briq.cloud/cookbook">Cookbook</a> ·
  <a href="https://briq.cloud/docs/mcp/tools">MCP tools</a> ·
  <a href="https://app.briq.cloud">Dashboard</a>
</p>

```
https://api.briq.cloud/mcp
```

A hosted, remote MCP server (Streamable HTTP). Your client signs in through the browser with MCP OAuth;
no key to copy. This repository holds the connection config for MCP registries and plugin stores. The
server itself runs at the URL above.

## Connect

Paste this into your agent. It edits its own MCP config, then tells you what is left:

```text
Add the briq MCP server to your config:
- name: "briq"
- url: https://api.briq.cloud/mcp (Streamable HTTP, OAuth)
- for all my projects

Then tell me what to do next to connect and activate it. If needed, read the setup instructions for agents: https://briq.cloud/docs/setup/agents.md
```

Or install it as a plugin:

| Client | Install |
|---|---|
| Claude Code | `/plugin marketplace add briq-cloud/briq-mcp`, then `/plugin install briq@briq` |
| Claude (web, desktop, mobile) | [Connect from Claude's connector directory](https://claude.ai/directory/e6de66f2-f44b-44ca-ba4f-fe5f9e4f0690) |
| Gemini CLI | `gemini extensions install https://github.com/briq-cloud/briq-mcp` |
| Any other client | Steps per client: [briq.cloud/docs/setup/clients](https://briq.cloud/docs/setup/clients) |

On first use, your browser opens: sign in or sign up, then pick the team and the budget the agent gets.
On a server or in CI, where no browser can open, send `Authorization: Bearer <BRIQ_API_KEY>` with a key
from the [Agents page](https://app.briq.cloud/agents).

## Try

```text
Deploy briq-cloud/wall github repo on briq (https://briq.cloud/docs/guides/run-a-github-repo.md) and give me a link to it.
```

```text
Start a sandbox on briq (https://briq.cloud/cookbook/sandbox.md), clone this project into it, run the test suite there instead of on my machine, and tell me what fails.
```

```text
Start a Postgres for this project on briq (https://briq.cloud/cookbook/postgres.md) and connect the app to it.
```

```text
Start Metabase on briq (https://briq.cloud/cookbook/metabase.md), load 'Our World in Data' energy dataset into it, generate a report on world energy generation, and share it with me.
```

## Tools

| Tool | What it does |
|---|---|
| `briq_run` | Run a recipe or any OCI image; returns connection strings |
| `briq_exec` | Run a command inside a briq |
| `briq_logs` | Read a briq's logs |
| `briq_files_put` / `briq_files_get` | Write or read a file in a briq |
| `briq_expose` | Publish a briq: an HTTPS URL, public or behind a token, or a TCP endpoint for Postgres |
| `briq_fork` | Copy a briq or a whole stack, its disk included, before a risky change |
| `briq_set_sleep` | Set when a briq sleeps (`30m`, `7d`, or `never`) |
| `briq_stop` / `briq_start` / `briq_destroy` | Lifecycle |
| `briq_list` / `briq_status` | What runs, its state, its cost so far |
| `briq_catalog` | The recipe cookbook |
| `briq_quota` | Credits, limits and the agent's budget |
| `briq_secrets` | The team's secrets by name and allowed hosts, never a value: a briq names one and the credential gateway puts the value in on the way out |
| `briq_docs` | Read briq's docs |
| `briq_feedback` | Write to the briq team |

Full reference with inputs and outputs: [briq.cloud/docs/mcp/tools](https://briq.cloud/docs/mcp/tools).

## What runs

Any public OCI image, plus ready-made [recipes](https://briq.cloud/cookbook) that return connection
strings, not Dockerfiles: Postgres, MySQL, Redis, MongoDB, MinIO, Qdrant, Neo4j, RabbitMQ, a headless
Chrome, Mailpit, Metabase, Grafana and more, and your own code in Node, Bun, Python, Go, Ruby, Rust, PHP
or a static site, from files or from a GitHub repo. Or a
[sandbox](https://briq.cloud/cookbook/sandbox): a microVM with Python, Node, git and a shell, where
the agent runs scripts, tests and builds instead of on your machine
([guide](https://briq.cloud/docs/guides/run-code-in-a-sandbox)).

- **Isolated**: each briq is its own microVM; each team has its own private network.
- **Sleeps when idle**: a briq stops when nobody uses it and wakes on the next call or request.
- **Budgets**: billed by the second, against a budget you set per agent.
- **EU-hosted** by default, with other regions available.

Start with €10 of credits. Pricing: [briq.cloud/docs/cost](https://briq.cloud/docs/cost).

## Links

- REST API: `https://api.briq.cloud/v1` ([OpenAPI](https://api.briq.cloud/v1/openapi.json))
- Docs for agents: [briq.cloud/llms.txt](https://briq.cloud/llms.txt)
- Security: [briq.cloud/docs/security](https://briq.cloud/docs/security) · Privacy: [briq.cloud/legal/privacy](https://briq.cloud/legal/privacy)
- Contact: [hello@briq.cloud](mailto:hello@briq.cloud) · Security reports: [security@briq.cloud](mailto:security@briq.cloud)

The files in this repository are MIT licensed. The briq service is operated by Uplab SAS under its
[terms](https://briq.cloud/legal/terms).
