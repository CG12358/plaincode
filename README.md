# PlainCode

**Think technically. Talk like a co-founder.**

An open-source AI coding skill for non-technical founders, entrepreneurs, creators, students, and vibe coders. PlainCode makes AI assistants reason with full engineering rigor while communicating in plain English.

It does not dumb down the engineering. It simplifies the conversation.

---

## See It

<table>
<tr>
<th width="50%">Default agent</th>
<th width="50%">PlainCode</th>
</tr>
<tr>
<td valign="top">

> Sure! I'd be happy to help you add payments to your application. There are several payment providers you could consider, including Stripe, PayPal, Square, and Braintree. Each has its own advantages. Stripe is widely used and has excellent documentation. PayPal has broad consumer recognition. Could you tell me which provider you'd prefer? Also, will you need subscription billing or one-time payments? What currency should I set as default? And should I implement webhooks for payment status updates?

</td>
<td valign="top">

> Added Stripe checkout for one-time payments. Test card works — try it with 4242 4242 4242 4242.
>
> Stripe charges 2.9% + 30¢ per transaction. No monthly fee at your current stage.
>
> Do you also need recurring subscriptions, or just one-time purchases?

</td>
</tr>
</table>

Same engineering quality. Fewer words. Zero jargon. One relevant question instead of five.

---

## Install

Works with any agent that supports skills or system-level instructions.

**Skills-compatible agents** (Claude Code, Codex, Cursor, Windsurf, Cline, and others):

```bash
npx skills add CG12358/plaincode
```

**Gemini CLI:**

```bash
gemini extensions install https://github.com/CG12358/plaincode
```

**Manual install** for any agent:

Copy the contents of [`SKILL.md`](./SKILL.md) into your agent's custom instructions, system prompt, or skills directory.

<details>
<summary>Common skill directory locations</summary>

| Agent | Location |
|---|---|
| Antigravity | `~/.gemini/config/skills/plaincode/SKILL.md` |
| Claude Code | `~/.claude/skills/plaincode/SKILL.md` |
| Cursor | Project `.cursor/rules/` or global settings |
| Windsurf | Project rules or global instructions |
| Cline | Custom instructions in settings |

</details>

---

## Philosophy

Most AI coding tools default to one of two modes: over-explain everything (tutorial mode) or strip language down to fragments (terse mode). Neither works well for non-technical builders.

PlainCode takes a different approach:

- **Internal complexity is allowed; user-facing complexity is not.** The AI reasons with full engineering depth. The user sees plain English.
- **Minimize tokens, not information.** Every filler word is cut. Every important fact stays.
- **Do not make the user choose things they don't understand.** Smart defaults first. Questions only when the answer materially changes the product.

### Priority chain

When rules conflict, PlainCode resolves in this order:

1. Technical competence
2. User simplicity
3. Action
4. Smart defaults
5. Decision boundary
6. Risk awareness
7. Token efficiency
8. Honesty

Full behavioral specification: [`SKILL.md`](./SKILL.md)

---

## Examples

See [`examples/comparisons.md`](./examples/comparisons.md) for 10 side-by-side comparisons covering:

- Building features from vague prompts
- Handling errors and failures
- Security and cost risk surfacing
- Scaling and architecture questions

---

## Contributing

See [`CONTRIBUTING.md`](./CONTRIBUTING.md).

PlainCode is one markdown file. Contributions that improve the behavioral rules, add evaluation scenarios, or fix edge cases are welcome. The bar: does this change make the AI more useful for someone who isn't a professional programmer?

---

## License

[MIT](./LICENSE)

---

<p align="center">
  <strong>PlainCode</strong> — Think technically. Talk like a co-founder.
</p>
