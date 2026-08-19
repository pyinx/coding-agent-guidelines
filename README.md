# Coding Agent Guidelines

A concise baseline for reliable coding work with Codex and Claude Code.

These rules constrain agent behavior without prescribing tools, workflows, or project architecture.

## Why

Coding agents usually fail through poor judgment, not missing instructions.

This project focuses on four durable behaviors:

1. Understand the goal before changing code.
2. Understand the existing system before designing a solution.
3. Make the smallest coherent change that preserves contracts.
4. Verify outcomes with fresh evidence before claiming success.

## Files

| File | Purpose |
| --- | --- |
| `AGENTS.md` | Canonical guidelines for Codex and other compatible agents. |
| `CLAUDE.md` | Claude Code entry point that imports `AGENTS.md`. |

Keep `AGENTS.md` authoritative. Keep `CLAUDE.md` as a compatibility shim.

## Installation

Clone the repository:

```sh
mkdir -p ~/.config
git clone https://github.com/pyinx/coding-agent-guidelines.git ~/.config/coding-agent-guidelines
```

### Project Scope

Copy both files into a new project root:

```sh
cp -n ~/.config/coding-agent-guidelines/AGENTS.md ./AGENTS.md
cp -n ~/.config/coding-agent-guidelines/CLAUDE.md ./CLAUDE.md
```

Commit the files so every contributor receives the same guidance.

### Global Scope

Link the guidelines into both agent configuration directories:

```sh
mkdir -p ~/.codex ~/.claude
ln -s ~/.config/coding-agent-guidelines/AGENTS.md ~/.codex/AGENTS.md
ln -s ~/.config/coding-agent-guidelines/AGENTS.md ~/.claude/AGENTS.md
ln -s ~/.config/coding-agent-guidelines/CLAUDE.md ~/.claude/CLAUDE.md
```

The Claude link preserves the relative `@AGENTS.md` import.

If a target file exists, merge its content instead. Never overwrite existing instructions blindly.

Start a new agent session after changing instruction files.

## Customization

Keep global rules universal. Put project commands and architecture boundaries in each repository.

Add a rule only when its absence causes a concrete, recurring failure.

Prefer principles over tool names. Prefer constraints over procedural checklists.

Remove rules that repeat platform defaults or cannot change a meaningful decision.

## Contributing

Keep changes small and defensible.

Explain the failure mode addressed by every new rule.

Update `AGENTS.md` only. Preserve `CLAUDE.md` as the import shim.

## License

No license has been declared yet.
