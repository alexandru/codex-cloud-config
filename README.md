# Codex Cloud

Personal Codex instructions, Main/Solo/Junior agents, and native skill plugins.

## Cloud setup

Add this repository to your Codex Cloud environment. With Git, a Codex CLI supporting plugins, and GitHub access available, run from this checkout during environment setup:

```sh
set -eu
codex_config_dir="${CODEX_HOME:-$HOME/.codex}"
mkdir -p "$codex_config_dir/agents"
cp AGENTS.md config.toml "$codex_config_dir/"
cp agents/*.toml "$codex_config_dir/agents/"
CODEX_HOME="$codex_config_dir" codex plugin marketplace upgrade alexandru
CODEX_HOME="$codex_config_dir" codex plugin marketplace upgrade mattpocock
```

Publish the environment and start a new task.
