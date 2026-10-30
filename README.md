# Codex Cloud configuration

This repository provides portable Codex instructions and shared skills for Codex Cloud.

The setup environment needs `git`, a Codex CLI with native plugin marketplace support, and network access to GitHub. From this checkout, run:

```sh
set -eu
codex_config_dir="${CODEX_HOME:-$HOME/.codex}"
mkdir -p "$codex_config_dir/agents"
cp AGENTS.md config.toml "$codex_config_dir/"
cp agents/*.toml "$codex_config_dir/agents/"
CODEX_HOME="$codex_config_dir" codex plugin marketplace upgrade alexandru
CODEX_HOME="$codex_config_dir" codex plugin marketplace upgrade mattpocock
```

The Codex settings declare and enable the latest full Alexandru and Matt Pocock plugin bundles. The refresh commands fetch them under `CODEX_HOME`; shared skills are not installed globally in `~/.agents/skills`. This copies the checked-in user instructions and Codex settings under `CODEX_HOME`; it does not write to the target project's `AGENTS.md`. Runtime credentials and machine-local configuration files are not included.

The default configuration uses `gpt-6.1-sol` at `high` for the main agent and Solo, and `gpt-6-luna` at `xhigh` for Junior. Cloud environment policy and model availability may override these defaults.

In a new Codex Cloud task, verify the config and model settings, that `alexandru-skills@alexandru` and `mattpocock-skills@mattpocock` and their bundled skills are discovered, and that Junior and Solo are available. Confirm plugin discovery in the published Codex Cloud environment. Report unavailable plugins, unsupported settings, or missing roles instead of relying on silent fallbacks.

Keep this configuration aligned with [Codex](https://github.com/alexandru/codex-config), subject to the [Cloud portability decision](https://github.com/alexandru/agents-config/blob/main/docs/adr/0020-keep-codex-cloud-aligned-with-codex.md).
