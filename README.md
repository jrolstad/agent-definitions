# agent-definitions

Reusable agent and prompt definitions for Codex-style workflows.

This repository stores agent instructions, standalone prompts, and small supporting files that can be used to standardize how specific tasks are performed.

## Contents

- `pr-review-agent/` Codex skill for reviewing GitHub and Bitbucket pull requests
- `pr-review-agent-prompt.md` standalone prompt version of the PR review agent
- `requirements.txt` local dependency used for validating skill metadata

## PR Review Agent

The PR review agent is designed to review code changes with these priorities:

- hexagonal architecture and clear boundaries between core logic and adapters
- code to interfaces instead of concrete implementations
- expressive, intent-revealing code
- unit tests for behavior changes
- use-case-based tests that exercise end-to-end behavior within the unit boundary
- stubs and fakes preferred over mock-heavy tests

## How to use

Use the skill directly in Codex:

```text
Use $pr-review-agent to review this pull request: <PR URL>
```

You can also use the standalone prompt in [pr-review-agent-prompt.md](pr-review-agent-prompt.md) when the skill packaging is not available.

## Validation

The skill can be validated with the local skill validator:

```powershell
$env:PYTHONPATH='C:\code\github\jrolstad\agent-definitions\.python_packages'
python 'C:\Users\jrols\.codex\skills\.system\skill-creator\scripts\quick_validate.py' 'C:\code\github\jrolstad\agent-definitions\pr-review-agent'
```

`PyYAML` is installed into `.python_packages` for this local validation flow.
