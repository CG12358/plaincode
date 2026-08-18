# Contributing to PlainCode

PlainCode is one markdown file. The bar for any change: **does this make the AI more useful for someone who isn't a professional programmer?**

## What makes a good contribution

- **Behavioral rule improvements** — better wording, edge case fixes, or rules that address real failure modes.
- **New evaluation scenarios** — before/after comparisons that expose a gap in the current rules.
- **Bug reports** — when an agent with PlainCode active does something the rules should prevent.
- **Platform compatibility** — install instructions or frontmatter adjustments for new agents.

## What doesn't fit

- CLI tools, runtimes, proxies, or build systems. PlainCode is a behavioral skill, not software.
- Marketing language in SKILL.md. The AI reads it, not the user.
- Changes that improve token efficiency at the cost of response clarity for non-technical users.

## How to contribute

1. Fork the repository.
2. Make your change on a branch.
3. Open a pull request with a clear description of what the change improves and why.

For behavioral rule changes, include at least one concrete example showing the before/after difference the change produces.

## Style

- SKILL.md instructions are written for the AI, not the user. Keep them direct and unambiguous.
- README.md and examples are written for the user. Keep them plain and jargon-free.
- Keep the file count minimal. Add a file only when it earns its place.
