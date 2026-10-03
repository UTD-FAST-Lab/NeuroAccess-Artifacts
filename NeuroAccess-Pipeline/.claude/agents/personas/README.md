# COGA Persona Agents

Four roleplay agents, drawn from the personas in the W3C *Making Content Usable for People with
Cognitive and Learning Disabilities* (COGA) document, section 6:
<https://www.w3.org/TR/coga-usable/#persona>

COGA defines ten personas; this pipeline uses four of them — Amy, Gopal, Kwame, and Yuki. The
other six (6.1, 6.3, 6.5, 6.7, 6.8, 6.9) have no agent here and are never part of a run.

Each agent answers **in the first person, in character**. They are users, not auditors —
they do not cite WCAG success criteria. Use them to get lived-experience reactions to the
screens in `inputs/`, alongside the rule-based detectors in `.claude/agents/`.

## The four

| Agent | Persona | COGA § | Primary sensitivity |
|---|---|---|---|
| `persona-amy`      | Amy, autistic computer scientist                  | 6.2  | Inconsistent layout, autoplay/motion, metaphors and abstract icons |
| `persona-gopal`    | Gopal, retired lawyer with dementia               | 6.4  | New terms, unrecognized icons, disappearing labels, losing his place |
| `persona-kwame`    | Kwame, traumatic brain injury survivor            | 6.6  | Cognitive overload, orientation, ambiguity, back navigation |
| `persona-yuki`     | Yuki, yoga teacher with AD(H)D                    | 6.10 | Carousels and motion, dense text, unfinished multi-step tasks |

## Using them

Ask for one by name, or fan several out at once:

```
Ask persona-gopal and persona-kwame to look at inputs/<AppName>/groundhog_output/screen1_actionables.png
and tell me whether they could complete the sign-in.
```

Every persona ends its answer with a short structured block (verdict + the barriers
specific to that persona), so responses across personas can be collated into a report.

## In the pipeline: facilitated test sessions

Inside an audit phase the personas are not asked for an opinion and left there. `se-tester`
(`.claude/agents/clear-purpose/se-tester.md`) runs its own audit first, then launches all four
personas — in parallel only when each has its own device, otherwise one at a time — shows them the marked screens, and collects a verdict per element —
`no problem`, `navigate with difficulty`, or `cannot handle it at all`.

For every element a persona flags, the tester acts as their test engineer: it proposes one or
two concrete things to try, aimed at the barrier that persona actually described. **The persona
runs the test themselves on the device, through the mobile MCP**, and then says whether their
opinion is `unchanged`, `hardened`, `softened`, or `reversed`.

Every phase's tester asks its questions in fixed words, in a fixed order — what the persona expects,
what on the screen told them, then their verdict — so answers are comparable across personas and apps.

**The personas perceive only the screen.** They are given the marked pictures and nothing else: never
a manifest, a capture file, or an accessibility string. On the device they look at screenshots and tap
what they see; they never use the device's element listing, which exposes names the screen does not show.

The personas are never told what the tester concluded, so agreement between the two sides is real
corroboration. `purpose-compiler` merges both and records, per issue, whether it was found
by the tester, by a persona (naming which), or by both.

Each persona file's *"When the tester asks me to try something"* section carries this protocol.

## Design notes

- **Grounded, not improvised.** Each file quotes the persona's "Problem" / "Works well"
  statements and all of their COGA scenarios verbatim, so the agent reasons from the
  source rather than from a generic stereotype.
- **Honest verdicts.** Every file instructs the persona to say plainly when a screen works.
  A persona that always finds a problem is useless as a test instrument.
- **Bounded disabilities.** Each file lists the disabilities that persona does *not* have,
  to stop the four agents from converging on one generic "impaired user".
- **Voice matched to the disability.** Kwame, Gopal, and Amy are articulate and precise —
  because their difficulty is not language. Yuki's difficulty is attention, not language: she
  reports her ten-second pass before any careful reading, and what she did not reach stays unread.
- **Tools.** They inspect screens, drive the app through the mobile MCP during a facilitated test
  session, and write up their own answers. They do not modify the pipeline — the only file a
  persona writes is its own. Once the mobile MCP server is registered, each persona's `tools:`
  can be tightened back to `Read, Glob, Grep, Write, mcp__<server>__*`.
