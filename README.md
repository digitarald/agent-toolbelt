# Agent Toolbelt

Personal agent plugins that earn their place in the toolbelt.

This is the curated counterpart to [Agent Parts Bin](https://github.com/digitarald/agent-parts-bin).
Parts Bin is for rough experiments. Toolbelt is for plugins I actually reach
for, with documented workflows, limitations, and evidence that they work.
Useful doesn't mean infallible. Review a plugin before trusting it with your
files or credentials.

## Plugins

<!-- plugin-table -->
| Plugin | Try it | Purpose |
|---|---|---|
| None yet | | |

The marketplace starts empty. No plugins have been promoted from Parts Bin yet.

## Install plugins

Add the marketplace in Copilot CLI:

```sh
copilot plugin marketplace add digitarald/agent-toolbelt
copilot plugin marketplace browse agent-toolbelt
```

Once plugins are listed, install one with
`copilot plugin install <plugin-name>@agent-toolbelt`, then start a new session.

In VS Code, run **Chat: Install Plugin from Source** and enter
`digitarald/agent-toolbelt`, or add it to `chat.plugins.marketplaces`.
Enable `chat.plugins.enabled` and start a new chat.
See [host support](docs/customization-types.md#where-each-type-works).

Hooks, MCP servers, and extensions can execute code on your machine.
Install only what you need. See [Security](SECURITY.md).

## Requirements

Using plugins requires a current Copilot CLI, the GitHub Copilot app, or
VS Code with agent plugins enabled, and a GitHub Copilot plan.
Maintaining this repository requires Node.js 22.14 or newer and npm.

```sh
npm ci
npm run verify
```

## Add a plugin

```sh
npm run new-plugin -- my-plugin
npm run verify
```

The scaffold includes a skill, manifest, README, changelog, and eval cases.
Use `--with agent`, `--with mcp`, `--with hook`, or `--with extension` for
other components, and `--no-skill` for a plugin without a skill.
Replace the scaffold with a real workflow before publishing.
See [Contributing](CONTRIBUTING.md) and [Customization types](docs/customization-types.md).

Before a plugin belongs here, document what it does, its risks and
limitations, and the hosts checked by hand. Keep behavioral evals that assert
invocation and outcomes, including a negative control. Record what actually
ran and what passed. An eval definition alone is not evidence of quality.

## Remove a plugin

```sh
npm run remove-plugin -- my-plugin
npm run verify
```

Use the scripts to keep the catalog, repository overlay, docs, and eval
registrations consistent.

## Evals

`npm run verify` checks types, manifests, generated files, tests, eval coverage,
and linting without calling a model. It does not prove a plugin works.

Behavioral evals use real Copilot sessions and cost AI credits. Run them only
when explicitly requested. List the selection first:

```sh
npm run eval:list -- --plugin my-plugin
```

See [Evals](docs/evals.md) and [Write an eval](docs/eval-authoring.md).

## Continuous integration

Model-free verification runs on pull requests and pushes to `main`.
Paid behavioral evals are opt-in, with pull-request runs disabled unless
`ENABLE_EVALS` is set to `true`. No behavioral evals have been run as part of
this repository's initialization.
See [CI setup](docs/ci.md).

## Licensing

[MIT](LICENSE). The original template's copyright notice is preserved.
The root license covers the repository and its plugins.

## References

- [Local development and installation checks](docs/local-development.md)
- [Security and data handling](docs/security.md)
- [Remote plugins](docs/remote-plugins.md)
- [Agent Plugins standard](https://agent-plugins.org/)
- [Agent Parts Bin](https://github.com/digitarald/agent-parts-bin)
