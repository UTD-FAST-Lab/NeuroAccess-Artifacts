# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.


**This file is the orchestrator.** It owns the workflow: which agents run, in what order, on what inputs, and where their outputs land. The agents in `.claude/agents/` own the *how* — do not restate their internal steps here, and do not let this file and an agent file disagree about paths or verdict vocabulary.

## Project Purpose

NeuroAccess is a UI accessibility auditor with three testers that check for issues that affect neurodivergent users. Each tester of this pipeline looks for issues of a specific category, and the input given varies according to the category being addressed. However, all of the testers are corroborated against feedback from a group of neurodivergent users (the COGA personas in `.claude/agents/personas/` — four of COGA's ten: Amy, Gopal, Kwame, and Yuki) as to elements that cause a problem to them when using the app under evaluation.

The inputs live in `inputs/<AppName>/` and the audit results go in `output/<AppName>/`, one folder per phase plus a one-page `accessibility_overview.md` across all of them.

An app's input folder holds **one capture folder per harness**, and each phase reads only its own:

```
inputs/<AppName>/
├── groundhog_output/    # screenN_actionables.png/.jsonl + screenN_talkback_labels.jsonl
│                        #   → Purpose and Functionality read this
└── droidbot_output/     # utg.js + states/  → Location reads this
```

**Capture folders are read-only.** Every derived artifact a detector produces — highlighted images, group sheets, marked screens, manifests — is written to a *sibling* folder under `inputs/<AppName>/`, never inside a capture folder. A phase ignores the capture that is not its own.

## Audit phases

| Phase | Category | Status |
|---|---|---|
| Purpose | Actionable elements whose purpose is missing or unclear | **implemented — see below** |
| Functionality | Icons and buttons whose functionality is not consistent across the app | **implemented — see below** |
| Location | Screens the user cannot locate themselves in | **implemented — see below** |

All three phases run. They are independent of each other and may run in any order, or alone — no phase consumes another's output. Each phase has its own agents in its own folder under `.claude/agents/`, its own verdict vocabulary, and its own output tree under `output/<AppName>/<phase>/`.

Every phase has the same four-step shape: **detect → tester audit → persona sessions → compile.** The personas and their vocabulary are shared across all three; nothing else is.

**Then one thing runs across all of them** — the overview, at the end of this file. It is the only stage that reads more than one phase, and it reads only their finished reports.

---

# Phase — Purpose

Identifies every actionable element in the app under evaluation — input fields, icons, and buttons — and decides whether a first-time user can tell what each one does.

**Verdict vocabulary — the tester uses exactly these three:** `"Missing Purpose"`, `"Unclear Purpose"`, `"Clear Purpose"`.
**Persona vocabulary — the personas use exactly these three:** `"no problem"`, `"navigate with difficulty"`, `"cannot handle it at all"`.

Run the four steps in order. Each step depends on the one before it, so do not start a step until the previous one has written its files.

## Step 1 — Detect and mark the actionable elements

Run `.claude/agents/clear-purpose/actionable-elements-annotator.md` over `inputs/<AppName>/groundhog_output/`.

It finds every actionable element across every screen — anything the user can type into, choose from, toggle, or tap — de-duplicates them, classifies each as an **input field**, an **icon**, or a **button**, assigns each a stable id (`screenN-aM`), and writes:
- `inputs/<AppName>/actionable-elements-highlighted/screenN_actionable_elements.png` — each screenshot with its elements boxed and labeled, colour-coded by kind
- `inputs/<AppName>/actionable-elements-highlighted/actionable_elements.json` — the manifest

It goes beyond the harness's own highlighting: Step 3 hunts for actionable elements the accessibility tree missed entirely.

**Only what can be seen is marked.** The screenshot decides whether an element is there; the records decide only whether a visible element is actionable. An element the records list but the picture does not show — covered, scrolled off, clipped, collapsed, transparent — is **never marked**, whatever its flags say and whether or not the harness boxed it; it goes to `excluded` with the reason. Anything visible that the records missed is added.

**Floating elements.** Where a dialog, sheet, popup, or menu is drawn over the screen, the elements underneath it are **excluded** — the user cannot see or reach them in that state — and the overlay's **own** controls are detected and marked instead, recovered from the image where the tree omits them.

Detection and classification only — this agent emits no verdicts and never names a glyph's function. Those element ids are the join key for everything downstream; nothing later re-keys on bounds or descriptions.

## Step 2 — The software engineer's audit

Run `.claude/agents/clear-purpose/se-tester.md` over the highlighted images and manifest from Step 1.

It judges every marked element on one question — can a first-time user tell what this does? — and what it examines depends on the kind:
- **input fields** — is the expected content, format, and constraint conveyed?
- **buttons** — does the visible text say what will happen?
- **icons** — is there a label, and if not, is the glyph a **common enough convention to stand alone**? A widely-known glyph that behaves as its convention promises is `"Clear Purpose"` and not a finding. A familiar glyph that does something else is `"Unclear Purpose"` — being misled is worse than being told nothing.

For every element it suspects is a problem it writes one or two test cases and **executes them on the live app through the mobile MCP**, then confirms or overturns its initial judgment on what the test showed. Writes to `output/<AppName>/purpose-detector/se-tester/`.

**Every verdict rests on what is visible on the screen and on what the element did when tested — nothing else.** `content_desc` and `talkback_label` help the tester understand the app and decide what to test for; the tester never asks whether they are sufficient, and they never move a verdict in either direction. A word that exists only in the records is not visible text.

**A marked element that testing shows is not actionable** — it does nothing and carries no state, or nothing is visible in its box — is a detection false positive, and the personas are told to ignore it.

## Step 3 — The persona sessions

Still inside `se-tester` (its Phases 5–6), and only after Step 2's own findings are on disk.

The tester meets each persona in `.claude/agents/personas/` — all four unless the run names a subset, launched per the concurrency rule at the end of this file — and with each one:

1. Shows them the marked screenshots from Step 1 — and nothing else — and explains what they are looking at: screens of the app with every actionable element boxed and tagged with a short id, colour-coded by kind. **A persona sees only the screen**: they never see a label that is not drawn there, never learn what a `content_desc` or `talkback_label` says, and are never told an element's name by the tester. On the device they look at screenshots, not the element listing.
2. Tells them, once and flatly, which marked elements to **ignore** because testing showed they are not actionable — and nothing else the tester concluded.
3. Asks, for each element, the same fixed questions in the same words and order: what they think it does (or what goes in it), what on the screen told them, then their verdict, why, and what would make it easier — recorded as `expectation`, `confidence`, `cue`, `verdict`, `why`, `solution`, with `where` in their own words.
4. For every element the persona flags, acts as their test engineer — proposes **one or two** concrete things to try, aimed at the barrier that persona actually described, with what result would mean the problem is real and what result would mean it is not.
5. The persona runs the test themselves through the mobile MCP and reports what happened.
6. The persona then says whether their opinion stands: `unchanged`, `hardened`, `softened`, or `reversed`.

Writes one file per persona to `output/<AppName>/purpose-detector/personas/persona-<name>.json`.

**Then the tester classifies the persona-only issues (its Phase 6).** The personas answer in their own vocabulary, which says *that* they struggled, not which kind of purpose failure they hit. So for every element a persona flagged and the tester did not, the tester reads what the persona actually said and labels it `"Missing Purpose"` (nothing told them what it does) or `"Unclear Purpose"` (what was there did not help them). **This is translation, not agreement** — the tester's own verdict on that element stays `"Clear Purpose"`, and the disagreement is preserved and reported.

**The tester's findings and the personas' findings stay independent** — see the common rules at the end of this file.

## Step 4 — Compile

Run `.claude/agents/clear-purpose/purpose-compiler.md`.

It joins the tester's report and the persona sessions on element id and produces the phase's deliverable: `output/<AppName>/purpose-detector/purpose_report.json` and `purpose_report.md`. Every issue carries a category — the tester's verdict where the tester found it, the tester's classification of the persona's words where only a persona did.

Every issue in that report carries **who found it** — `"tester"`, `"persona"` (naming which personas), or `"both"` — plus the disagreements, where one side found a problem and the other did not. The compiler never adjudicates a disagreement and never invents a finding.

It also surfaces the **contested exemptions**: unlabeled icons the tester cleared as common convention that a persona could not read. That is this phase's sharpest recurring result — the exemption meeting a user it does not serve — and it gets its own table rather than a buried row.

**The `.md` deliverable is short, table-first, and the same form for every app**: `purpose-compiler` fills in a fixed template — a three-line header, one attribution table carrying every finding with what the test showed, and a handful of focused tables — and the JSON has a fixed key set. No methodology section, no per-screen walk, no patterns or synthesis essay, and no narration of the pipeline's own state. Full detail lives in the JSON.

## Output layout

```
output/<AppName>/purpose-detector/
├── se-tester/
│   ├── screenN_purpose.json           # one per screen
│   └── se_tester_report.json          # the tester's aggregate, incl. persona_issue_classifications
├── personas/
│   └── persona-<name>.json            # one per persona
├── purpose_report.json                # ← the phase deliverable
└── purpose_report.md
```

## Requirements

See **Rules common to every phase** at the end of this file. They govern this phase in full; nothing here overrides them.

# Phase — Functionality

Decides whether the relationship between what a control **looks like** and what it **does** holds still across the app — for icons and buttons alike.

Whether a single control conveys its purpose on its own — whether it has a label, and whether an unlabeled glyph is a common enough convention to stand without one — is the **Purpose** phase's question, not this one's. This phase asks what a one-element-at-a-time audit cannot: a control can be perfectly legible on every screen it sits on and still mislead a user who learned it somewhere else, or hide a job the user is looking for behind a picture they never learned.

Two questions, and the phase exists for both:
1. **Same appearance, different functionality** — does the same picture do the same thing everywhere? Unless the view's own context makes the difference plain, it does not.
2. **Same functionality, different appearance** — where one job is drawn more than one way, does the variety help the user or confuse them?

**Verdict vocabulary — the tester uses exactly these two:** `"Inconsistent Functionality"`, `"Consistent Functionality"`.
**Persona vocabulary — the personas use exactly these three:** `"no problem"`, `"navigate with difficulty"`, `"cannot handle it at all"`.

Run the four steps in order. Each step depends on the one before it, so do not start a step until the previous one has written its files.

## Step 1 — Detect the controls and build the groups

Run `.claude/agents/consistent-functionality/functionality-group-annotator.md` over `inputs/<AppName>/groundhog_output/`.

Same capture as the Purpose phase — `groundhog_output/screenN_actionables.png`, `screenN_actionables.jsonl`, `screenN_talkback_labels.jsonl` — but what it marks is icons **and buttons**, text-only buttons included, because a shared job routinely appears as a glyph on one screen and a worded button on another. It de-duplicates them, assigns each a stable id (`screenN-fM`), and sorts them on two independent axes:

- **glyph groups** (`ggN`) — elements that *look* the same. The detector first builds an **appearance catalogue** — one canonical description per distinct visible face, written from the crops seen side by side — and every element carries its entry verbatim, so grouping is an exact match. **Every element with the same appearance is in the same glyph group, and no element is in two.** Visual state (outline vs. filled) stays inside the group and is recorded per member.
- **function groups** (`fgN`) — elements *declared* to do the same thing, grouped from strings the app supplies: the visible label, the TalkBack label, the content description, the resource id, each normalized into a `function_key`. **Every element whose function is certain is in exactly one function group** (or recorded as unique), all elements sharing a function are in the same one, and no two function groups share a key. Groups whose members are drawn differently are marked `mixed_appearance`.
- **candidate function groups** (`cfgN`) — raised **only for elements whose function the detector is unsure of** (`function_status: "uncertain"`): no string, a string too thin to trust, or a string that may or may not name an existing group's job. Such an element sits in no function group and is handed to the tester as a candidate — possibly more than one, one per plausible job. **That uncertainty is the only reason an element may appear in more than one function-axis document**; a candidate's other members can only be the members of the one group it extends. Each is marked `status: "unconfirmed"` and exists to be settled by the tester, never by the detector.

A validator script checks all of this — every element exactly once per axis, same appearance ⇔ same glyph group, one group per function key, every candidate holding an uncertain element, no two groups with the same membership — and nothing is drawn until it passes.

It writes, under `inputs/<AppName>/functionality-groups/`:
- `screenN_glyph_groups.png` and `screenN_function_groups.png` — the screens boxed and coloured by group, one image per axis, a group's colour stable across every screen
- `groups/<groupid>.png` — a contact sheet per group: every member cropped **with its surrounding context** and captioned with its id, so a group can be seen as a group. These sheets carry the group id and member count and **nothing else** — no explanation of why the members are together, because the personas read them.
- `functionality_groups.json` — the manifest

Detection and grouping only — this agent emits no verdicts and never asserts that a group *ought* to behave alike. Appearance comes from the image; a **confirmed** function group comes only from strings the app itself supplies, and an element with no such string gets `function_key: null`.

**A confirmed function group is a declaration, not a resemblance.** Runs before this one shipped groups whose members plainly did different jobs, joined by a normalized key that named neither of them well — a bare verb (`open`, `save`, `more`) that two unrelated controls can each honestly carry, an object that normalization threw away ("Share this photo" and "Share profile" both reduced to `share`), a key derived only from a `resource_id` or from a descendant's string. Downstream that costs more than a missed pairing: the tester's Phase 3 starts from *this group is real* and asks only whether the mixed appearance helps, and the personas are shown the sheet as a set of things that belong together. So Step 1 now runs a **sanity check over every group before any of them is confirmed**, and **demotes rather than confirms whenever the strings are thin** — the pairing becomes a `cfgN` with `evidence: "demoted_fg"`, recorded in `function_group_demotions` for the tester to settle by tapping. On this axis the asymmetry runs the other way from detection: a wrong candidate costs one tap, a wrong confirmation is inherited as fact by every stage after it. **When in doubt, nominate.**

**One subject, one group.** Being exhaustive and not duplicating are the same obligation seen from both sides: the tester and the personas must see every subject in the app, and see each one once. No two groups on an axis share a membership set, no element carries two `gg` or two `fg` ids, and **a candidate never duplicates a group that already exists** — a `cfg` whose membership is the same set as a `gg`'s is not a candidate at all, since those elements already look alike, already travel together, and are already tapped and shown as that glyph group. Every candidate fills in an `adds` field naming what it proposes that no existing group says; one that cannot is dropped.

**Only actionable elements are marked, and the capture's own highlighting is not a warrant.** The harness boxes headings, photos, paragraphs and layout wrappers as readily as controls, and **an element being already marked is no reason to mark it**. Every candidate faces three questions independently — a `clickable`/`focusable` record at its bounds, a clickable ancestor containing it, or state it conveys — and where all three fail it is excluded on the `harness_marked_not_actionable` ground rather than carried in. A non-control in a group is a crop on a contact sheet and a persona asked in earnest what happens when they press something inert.

**A half-drawn control is a question, not a difference.** Where the picture shows a placeholder, a shimmer, or an empty slot that the sibling screens fill, the crawler most likely photographed the screen before it finished loading. The detector flags `render_state: "suspected_incomplete"` and records it in `render_anomalies`; it never splits a group, removes a member, or decides which case it is. The tester settles it on the live app.

**Reading those strings correctly is the whole ballgame.** Several records routinely share one set of bounds and most of them are empty, and a control's label routinely sits on a descendant rather than on the control itself. Merge them carelessly and an element that the capture labels plainly is recorded as having no function string — and a job drawn two ways then reaches no group, no contact sheet, no test case and no persona. So Step 1 takes a populated field over an empty one always, walks *down* into descendants as well as up to clickable ancestors, and reconciles per screen: every non-empty label in the capture reaches an element or is accounted for.

**What is genuinely stringless is then nominated, not parked.** For the residue — image-only controls, custom-drawn toolbars, pairings whose two strings are too far apart to join — the detector runs four sweeps and raises a `cfgN`, and here, and only here, a recognized glyph may raise its hand. A candidate is a question, not a claim: it gets a contact sheet like any other group, it is never resolved by the detector, and the tester settles it by tapping. Nominating wrongly costs one tap; not nominating costs the finding entirely. But a candidate is never a substitute for a string that was there to be read — nominating on convention what the capture already spelled out launders a lost string as a hunch. Step 5E closes the arithmetic: every element with no function string is either in a candidate or in `function_unresolved` with what was checked. Every synonym join and declined near-miss is recorded so the tester can reverse it.

**Only what can be seen is marked.** The screenshot decides whether an element is there; the records decide only whether a visible element is actionable. An element covered by a dialog or sheet, scrolled off, clipped, collapsed or transparent is **never marked** — no box, no group, no crop — and goes to `excluded` with the reason; the overlay's own controls are marked instead. Anything visible that the records missed is added.

## Step 2 — The software engineer's audit

Run `.claude/agents/consistent-functionality/se-tester.md` (agent name `functionality-se-tester`) over the group sheets and manifest from Step 1.

Its Phase 1 establishes what each element actually does — from its declared string, or from its own judgement of common glyph convention (there is no icon library; every such reading is recorded as the tester's, with a confidence) — and records the **context** the view supplies around it, before any tap. Phase 2 then takes every glyph group and asks whether the same picture does the same thing everywhere; Phase 3 first **resolves every candidate group on the device**, then takes every mixed-appearance function group, surviving candidates included, and asks whether the variation helps or confuses. A candidate with `resolution: null` never reaches a finding or a persona. Both **execute test cases on the live app through the mobile MCP**. Writes to `output/<AppName>/functionality-detector/se-tester/`.

**A candidate and the function group it overlaps are one subject, and only one survives.** A candidate usually holds a function group's members plus the one or two elements whose function was unknown. The tester taps those elements and decides which set is the correct function group: if they do the group's job the candidate survives and the function group is marked `superseded`; if not, the candidate is dissolved and the function group stands. The loser gets no verdict and is **never shown to a persona** — a persona is never shown two groups that differ only by uncertain elements.

**The context exception** is this phase's sharpest instrument and its likeliest loophole. Members of a glyph group that genuinely do different things are not a finding when the view itself makes that plain — but only when the distinguishing context is visible on screen before the tap, is available before acting rather than after, belongs to the control visually, and works for someone meeting the screen for the first time. The tester must quote the context it relied on and name which criterion it declined. "Context makes it clear" with no named context is a shrug, not a judgment.

**A mixed appearance is not automatically a fault.** A glyph in a terse toolbar and a worded button in a full-page form can be the same job well served. The verdict turns on surface, scope, explicitness, and whether a user who learned one rendering could recognize the other — argued, not assumed.

Consistency is an empirical claim: no glyph group is called inconsistent without tapping **every** member in it.

**Every group the detector built is evaluated, and the arithmetic is stated.** The tester builds a subject ledger from the manifest — every glyph group, every function group including the ones whose members all look alike, every candidate, every element with no function string — and each entry leaves it with a verdict, a resolution, or a `not_executed` with a reason. A group missing from the aggregate is not a group that passed; the compiler joins on group id, so it simply is not in the report, while the marked screenshots still show its boxes to a reader who will assume it was cleared.

**And the tester does not under-call.** It holds this phase's definitions, and both shapes of failure are issues by definition once the behaviour is established: different jobs behind one appearance, and one job behind appearances different enough that a user who learned one would not recognize the other. The exceptions — the context exception, and the surface/scope/explicitness argument — are cases the tester *argues*, with the context quoted and the criterion named. A clearance with no reasoning is recorded as a finding, because it is indistinguishable from a group nobody thought about.

**Two things about the pictures are settled on the device and then explained to the personas.** Both are facts about the capture rather than findings about the app, and withholding either one makes a persona answer a question the app never asked:
- **A member caught mid-load.** The tester reaches the screen live, lets it settle, and decides whether the odd appearance is a loading artifact or a real difference. Where it is an artifact the member **stays in its group** — nothing is removed to tidy a sheet — the difference carries no weight in the verdict, and the personas are told plainly that this crop had not finished drawing and how it looks on the running app. Where it is real, it is judged as an ordinary appearance difference and nothing is said.
- **A member that is not a control.** Where tapping shows a marked element takes no action and carries no state, it is detector feedback — and the personas are told to leave it out of their answers, because that element is still cropped on the sheet they are shown, and a member that does nothing changes how the group looks and how many things they think they are being asked about.

Both disclosures are stated flatly, recorded verbatim in the session file's `disclosures`, and carry no verdict, no explanation of why they matter, and none of the words the briefing forbids.

## Step 3 — The persona sessions

Inside `functionality-se-tester` (its Phases 6–7), and only after Step 2's own findings are on disk.

The tester shows each persona in `.claude/agents/personas/` the sheets of the **surviving** groups and asks what they expect — but the whole difficulty here is that the sets exist *because the tester suspects something*, so a briefing that leaks why the members are together plants the answer. The protocol therefore asks about each member alone before it asks about the group, in fixed words and a fixed order:

- **Q1** — each member, one at a time, in screen order: *"If you pressed this one, what do you think would happen?"*
- **Q2–Q3** — the group, once each: *"Would you expect the same thing to happen from all of these?"* and *"If they turned out not to all do the same thing, would that change how you get around the app?"*
- **Q4–Q6** — the verdict, why, and what would make it easier — the same three questions every phase asks.

There is no open "anything you'd say about these together?" question: the contact sheet already shows the members together, so its answers were never unprompted, and Q2 collects the same signal in a comparable form.

Every surviving group is shown, not only the suspect ones — a persona shown only suspect groups learns the game by the third. The words *inconsistent*, *consistent*, *problem*, *issue*, *confusing*, *mismatch*, *wrong*, and *should* appear nowhere in the briefing outside the fixed questions. **Two things about the pictures are disclosed** — a crop the capture caught mid-load, and a member that turned out not to be a control — because both change what the sheet shows rather than what the app does; each is stated flatly, recorded verbatim in the session file, and carries no verdict and no explanation of why it matters. Then the same test-and-revisit protocol as the other phases: the persona runs one or two things on the device themselves and says whether their view stands.

**A persona who does not understand what a control does has raised a Purpose question, not a Functionality one.** Where a persona's reasoning — their `why` and their `solution` — is that they cannot tell what a button or icon is for, what it will do, or what its picture or word means, the tester recognises it as out of scope for this phase: it is routed to `out_of_scope_observations` with that reason, it gets no device test in this phase, it is never classified, and it is never counted as a persona-held issue or a disagreement — even though the persona flagged it with a difficulty verdict on a group sheet. This phase's question is only whether the relationship between controls holds: the same picture doing different jobs, or one job drawn in ways the persona could not connect. A complaint enters this phase only when its reasoning is about that relationship.

**Then the tester classifies the persona-only issues (its Phase 7).** The personas answer in their own vocabulary, which says *that* a group defeated them, not which inconsistency did it. So for every group a persona flagged and the tester did not — once the out-of-scope complaints above are set aside — the tester reads **the persona's own reasoning — their `why` and their `solution`** — and labels it `"Inconsistent Functionality"` with the conflict kind that reasoning describes: `same_appearance_different_functionality` where one picture meant two things to them, `same_functionality_different_appearance` where they could not recognize one job drawn twice. A persona describing the fix usually names the category outright. Where their reasoning supports neither, it is recorded as unclassified rather than forced. **This is translation, not agreement** — the tester's own verdict on that group stays `"Consistent Functionality"`, and the disagreement is preserved and reported.

Writes one file per persona to `output/<AppName>/functionality-detector/personas/persona-<name>.json`, keyed by group.

## Step 4 — Compile

Run `.claude/agents/consistent-functionality/functionality-compiler.md`.

It joins the tester's report and the persona sessions on **group id**, and on element id for the per-screen view, producing `output/<AppName>/functionality-detector/functionality_report.json` and `.md`. Findings are group-level: reported once as a group **and** carried onto each member, so a conflict never dissolves into scattered per-element entries and no element's row hides the group implicating it.

Every issue carries a category and a conflict kind — the tester's where the tester found it, the tester's reading of the persona's words where only a persona did, and recorded as missing rather than guessed where the persona's reasoning supported none.

It also surfaces two things no per-element table can:
- the **expectation mismatches** — where a persona expected the members to behave alike and they did not, and the reverse;
- the **contested exceptions** — groups the tester cleared on the context exception that a persona could not use. The tester can be entirely right that the heading is there and a persona still be stranded by it; that pairing gets its own section rather than a buried row.

Out-of-scope observations — including every persona complaint that a control's purpose was unclear — are listed separately and never enter the issue counts, the attribution, or the disagreements.

Grouping corrections, dissolved candidates, superseded function groups, function-group demotions, capture render artifacts, and detection false positives are feedback to `functionality-group-annotator` or to the capture, not findings about the app, and none of them enter the issue counts. A group in the manifest that the tester never judged is reported as `not_evaluated` — never omitted, and never counted as clean. All but one stay in the JSON; **detection false positives are reported in the `.md` as their own table**, because a reader of the marked screenshots needs to know which boxes were wrong. Like every phase here, that `.md` is short, table-first, and the same form for every app — a fixed template filled in: a three-line header, one attribution table carrying every finding with what each member did, and a few focused tables; no methodology, no per-screen walk, no patterns section. The JSON has a fixed key set.

## Output layout

```
output/<AppName>/functionality-detector/
├── se-tester/
│   ├── screenN_functionality.json          # one per screen
│   └── functionality_se_tester_report.json # the tester's aggregate, incl. glyph_groups and function_groups
├── personas/
│   └── persona-<name>.json                 # one per persona
├── sheets/                                 # contact sheets redrawn by the tester, only where a group's final membership changed
├── functionality_report.json               # ← the phase deliverable
└── functionality_report.md
```

---

# Phase — Location

Decides whether a user can tell where they are in the app on any given screen, and whether that sense of place survives **while they stay on that screen and its content moves under them**.

**This phase evaluates scroll transitions and nothing else.** A touch or a Back key lands the user on a *different view*, and a different view is judged on its own terms as a screen — not as a move. What a per-screen check cannot see is the identifier that exists in the state dump and has scrolled out of the viewport: it abandons the user exactly as completely as one that was never there, and it does it to the user who is deepest into a long screen and least able to re-orient. Every other edge is recorded so the map is complete, and marked `evaluated: false`. Expect a small evaluated set — a crawl typically records far fewer scrolls than touches — and expect every stage to say that count plainly, so a short list is not misread as skipped work.

This phase reads a different input from the others: **`inputs/<AppName>/droidbot_output/`**, the DroidBot capture of a crawl through the app. Two parts of it matter — `utg.js`, the UI Transition Graph, which says which state leads to which and what event caused the move; and `states/`, holding one `state_<tag>.json` view hierarchy and one `screen_<tag>.png` screenshot per captured state. Those are the same two files DroidBot's own `index.html` is built from; the phase reads them directly rather than the viewer.

Without the capture the phase cannot run at all: the screens come from `states/` and the transitions come from `utg.js`.

**Verdict vocabulary — the tester uses exactly these three:** `"Missing View Identifier"`, `"Disappearing View Identifier"`, `"Sufficient View Identifier"`. The first and third are verdicts about a screen; the second is a verdict about a scroll transition. A scroll transition whose identifier survives is not a finding and is recorded as the pass, `"Identifier Persists"`. There is no "Unclear" verdict in this phase: a region that is present but does not locate the user — the app's own name, a word that names content rather than a place, a nav highlight that cannot be seen — is not an identifier, so the screen it sits on is `"Missing"`.
**Persona vocabulary — the personas use exactly these three:** `"no problem"`, `"navigate with difficulty"`, `"cannot handle it at all"`.

**A persona-only issue is translated into the same two failures.** Where a persona holds an issue that the tester does not, the tester translates their words into this phase's vocabulary in its own Phase 7 — a screen `"Missing View Identifier"` where their reasoning is that nothing on the screen told them where they are, including when what was there did not locate them; a scroll transition `"Disappearing View Identifier"` where their reasoning is that the place name left them when the content moved. Where the reasoning supports neither, it is recorded as unclassified rather than forced. That label lives in `persona_issue_classifications` and never touches the tester's own verdict, which stays the pass it already reached. Translation, not agreement — the disagreement is the finding.

## Step 1 — Read the graph and mark the header and navigation regions

Run `.claude/agents/clear-location/location-graph-annotator.md` over `inputs/<AppName>/droidbot_output/`.

It parses `utg.js` (a JavaScript file, not JSON — `var utg = ` then an object), loads every state dump, and writes `inputs/<AppName>/location-graph/graph.json` — nodes and transitions with stable ids (`tN`), each transition's recovered action, an `evaluated` flag with a reason when false, and a `validation` block. It also writes `inputs/<AppName>/location-graph/marked/<sid>_header_nav.png`: every screen with its header region and/or navigation-bar region boxed and labeled where either is present, and written out unmarked where neither is — nothing else is marked, and no in-app screen is missing from the set. Those marked images are what the tester and the personas both look at.

**A header is wherever the place is named, not wherever a geometric rule expects it.** The detector no longer gates on the top 12% of the screen: a mid-screen title, a bottom-sheet heading, a name centred on an empty state all get marked, each flagged `unconventional_position` with a `why_marked` line addressed to the tester. It is told to **mark generously and leave the call downstream** — a region marked and then dismissed costs the tester a sentence and is a recorded result; a region never marked is invisible to the tester and to every persona, and the screen enters the report as bare when it was not. The tester judges each one, and the personas see it as an ordinary box with no hint that anyone was unsure.

**Every in-app screen the capture holds is marked, and identical screens are marked identically.** The states it marks are the phase's entire subject list — the tester judges what is marked and the personas see what is marked — so a state it skipped is a screen that leaves the audit silently, and a location signal it noticed on one visit and missed on the next manufactures a contradiction out of one screen: one located, one bare. So every in-app node with a screenshot gets a marked image, marked or bare; a bare one carries a `no_region_reason` naming what was actually looked at, because "nothing to mark" with no reason is indistinguishable from a state nobody read. And before drawing, the detector groups the states that are the same screen — by screenshot hash and by `structure_str` — reconciles their regions, and re-marks whichever member it read less carefully, with the reconciliation recorded in `consistency_groups`.

**Out-of-app states are never marked at all**, because the marked folder is exactly the set of pictures the tester judges and the personas see: another app's chrome boxed as a "header" is a browser being audited as though it were this app. And **no screen is ever named that cannot be shown** — a state with no screenshot gets `marked_image: null` and a place in `validation`, never a plausible path, and every path is verified on disk before the manifest is final.

**A scroll edge is same-view because it is a scroll**, never because its endpoints' structure hashes match — scrolling reattaches views, so the hash moves even though the user has not. Scroll edges routinely have differing `structure_str`, so a structural test would reject the very edges this phase evaluates. The structural check survives only as `structural_same_view_candidates`: non-scroll edges that look like the user never moved (a keyboard, a toast, a sheet), advisory only, which the **tester** may promote after confirming on the device and the detector never promotes itself.

Four things it must get right, because each one silently corrupts everything downstream:

- **The ids.** UTG nodes are keyed by a 32-hex content hash. The detector assigns readable ids `sN` in capture order and keeps `state_str` as the identity of record.
- **The bounds.** DroidBot writes `[[x1,y1],[x2,y2]]`, where every other phase here uses `[left, top, right, bottom]`. It is flattened once, at load, so nothing downstream has to know.
- **The action labels.** An edge's `event_str` carries `view=<hash>`, which resolves against the `view_str` of a record in the `from` state — that is how the phase recovers *what the user actually tapped* and can say "the header disappears when you tap Share". Where it does not resolve, the transition is marked `action_present: false` and nobody guesses.
- **The package partition.** A crawl wanders into the browser, the photo picker, the Play Store. Those states are recorded separately as `out_of_app_nodes` and never judged: leaving the app is not losing your place inside it.

It classifies every event — `touch` and `key` are navigation, `scroll` is the user staying put while content moves, `intent` is the harness launching the app — and it judges nothing. It never infers a location signal from a picture and never treats `foreground_activity` as one.

## Step 2 — The software engineer's audit

Run `.claude/agents/clear-location/se-tester.md` (agent name `location-se-tester`) over the graph manifest and the marked images.

It judges every in-app screen for a header or navigation identifier, and every **scroll** transition for whether that identifier survives the content moving, then **executes test cases on the live app through the mobile MCP**. Writes to `output/<AppName>/location-detector/se-tester/`.

**The subject list has two hard edges, and they are checked before anything is judged.** Only screens **inside the app under evaluation**: the `out_of_app_nodes` are a browser, the launcher, the photo picker, a billing sheet — no verdict, and never shown to a persona, since asking someone where they are in the app while showing them Chrome's address bar files an answer about Chrome against this app. Where the package partition put another app's surface in the in-app set, the tester excludes it and reports it as detector feedback rather than judging it. And only screens that **exist as a picture**: every screen id the tester names anywhere is a node in the manifest with a marked image on disk. Nothing is invented, merged, split or renamed; a state the capture does not hold is an input gap, not a row in a report.

**A marked region is not an identifier.** The detector found where a header or nav bar sits; the tester reads what each one actually says. A header carrying only the app's own name tells the user which app they are in, not which part of it — and that is this phase's most common failure shape, so it is counted separately.

**`foreground_activity` is never an identifier.** It sits in every state dump, and in a single-activity app it is the same string on every screen. The user cannot see it in any case. The same goes for `resource_id` and the crawler's own hashes.

**A navigation region's `contains_selected_view` is the app's own declaration of which nav item is current** — the mechanized form of the active state this phase cares most about. It is strong evidence, and still not sufficient: a region flagged this way whose pixels look identical across its items is a Missing View Identifier with an unusually cheap fix. Where the flag appears nowhere in a capture, the tester says so once and reads every active state off the pixels. Wordless nav items arrive carrying the detector's own reading of the glyph, labelled as its reading — there is no icon library behind it, and a bar the tester reads fluently may still tell a persona nothing.

**A Missing screen that a confirmed Disappearing transition also lands on keeps its `"Missing View Identifier"` verdict.** Screens and transitions are separate subjects: the screen's write-up names the transition that lands on it, and the transition's names the screen, so a reader sees the connection without either verdict being rewritten.

The scroll test is the phase's central one, and it has three parts: is the identifier still on screen, does it return on scrolling back, and — for a nav bar — did its *active state* survive as well as the bar. The tester scrolls **past** the distance the crawl recorded, since a user does. Direction matters and is recorded: a vertical scroll can push a top header out of the viewport, a horizontal one usually moves a carousel instead, and neither is assumed. A screenshot is one frozen moment, so the tester scrolls and acts before declaring an identifier absent; where the live app has diverged from the capture it records the divergence and goes provisional rather than judging a stale screenshot as current.

## Step 3 — The persona sessions

Inside `location-se-tester` (its Phases 6–7), after Step 2's findings are on disk.

Personas get the same input the tester did — the marked screens, shown individually, and then in from/to pairs for the **scroll** transitions with the plain-language action that connects them — and are asked the same fixed questions, in the same words and order, for each: where in the app do you think you are, what on the screen told you that, then their verdict, why, and what would make it easier. For a scroll pair the questions are about the second picture, after the fixed sentence *"You stayed on this screen and scrolled <direction>."* They are given the marked images and nothing else. A scroll is described for exactly what it is (*"you stayed on this screen and scrolled down"*) and never as going somewhere, which would invent a move they did not make and ask them the wrong question. Harness launches are never shown at all, and touch and Back edges are not shown as transitions, since this phase does not evaluate them — the screens they lead to are shown individually like any other.

The briefing must say that a box marks *a place a name could be*, not that the name is any good, or the marks read as an answer key. **A region marked in an unconventional position is shown without comment** — no mention that it is unusual, that the detector was unsure, or that anyone doubted it. A persona saying unprompted that a marked region names a piece of content rather than a place is the most useful thing this phase can collect, and a leading question destroys it.

Same test-and-revisit protocol as the other phases. Writes one file per persona to `output/<AppName>/location-detector/personas/persona-<name>.json`, with separate `screens` and `transitions` blocks.

**Then the tester classifies the persona-only issues (its Phase 7).** The personas answer in their own vocabulary, which says *that* they lost their place, not which kind of failure did it. So for every screen or transition a persona flagged and the tester did not, the tester reads **the persona's own reasoning — their `why` and their `solution`** — and labels it — a screen `"Missing View Identifier"` (nothing located them, whether nothing was there or what was there did not help), a transition `"Disappearing View Identifier"`, or unclassified where their reasoning supports neither. **This is translation, not agreement** — the tester's own verdict stays the pass it already reached, and the disagreement is preserved and reported.

## Step 4 — Compile

Run `.claude/agents/clear-location/location-compiler.md`.

It joins both sides on node id and transition id and produces `output/<AppName>/location-detector/location_report.json` and `.md`. Every issue carries a category — the tester's verdict where the tester found it, the tester's classification of the persona's words where only a persona did, and `classification_missing` where one is absent rather than a guess. **Every screen in the report is a node in the manifest with a marked image behind it**; screens with no picture, and the subjects the tester took out of scope, are reported as capture coverage with their reason instead. **Screens and transitions stay separate throughout** — a screen can name itself perfectly while the move into it strands the user, and the reverse. The capture's own gaps are carried forward as input gaps, distinct from findings about the app.

It also shows what was deliberately never judged — out-of-app states, exit and return transitions, harness moves, and every edge marked `evaluated: false` — with the reason each carries no verdict, because a subject that silently vanishes from a report reads as a subject that passed. Every return transition is cross-referenced to the in-app screen it lands on, since that arrival *was* judged.

**The `.md` deliverable is short, table-first, and the same form for every app**: a fixed template filled in — a three-line header, two attribution tables (screens and transitions) carrying every finding with what the test showed, and a few focused tables, every section present even when empty. The JSON has a fixed key set. No methodology section, no per-screen walk and no patterns section. Detector feedback stays in the JSON, with one exception reported as its own table: the **detection false positives** — regions the detector boxed that the tester judged to name a piece of content rather than a part of the app, since the personas and the reader both look at those marked images.

## Output layout

```
output/<AppName>/location-detector/
├── se-tester/
│   ├── <sid>_location.json             # one per screen
│   └── location_se_tester_report.json  # the tester's aggregate, incl. every transition
├── personas/
│   └── persona-<name>.json             # one per persona
├── location_report.json                # ← the phase deliverable
└── location_report.md
```

---

# Final step — The overview

Run `.claude/agents/accessibility-report-compiler.md` **after** every phase that this run includes has compiled. It is the last thing to run and the only stage that looks at more than one phase.

It reads the three phase deliverables — `purpose_report.json`, `functionality_report.json`, `location_report.json` — and writes **one page**: `output/<AppName>/accessibility_overview.md`.

**It is a summariser, not a fourth auditor.** Its entire job is to tell a reader what they are about to find and which report to open first: how much each phase evaluated, how many issues it found, how those split by severity and by who found them, which personas the app actually fails across all three phases at once, and what was deliberately not judged. One line per phase says what the recurring failure shape is; everything else is a table.

Three things it must not do, because each one would quietly make it a fourth opinion:

- **It never re-derives a number.** Every count comes from the phase report's own summary block, never recounted from a findings array. A summary that disagrees with the report it summarises is worse than no summary.
- **It never re-judges.** It does not upgrade a severity, merge two phases' findings, resolve a tester/persona disagreement, or decide which side was right. The phases preserved those disagreements on purpose.
- **It carries no phase detail** — no element, group, screen or transition ids, no recommendations, no persona quotes, no evidence. That is what the individual reports are for, and its last table says where each one is.

**A phase that did not run reads `not run`, never `0`.** A subset run is legitimate — one phase or two — but an absent phase keeps its row in every table and is excluded from the totals with that stated. An absent phase must never be readable as a phase that found nothing.

---

# Rules common to every phase

These apply to Purpose, Functionality, and Location alike.

- **The mobile MCP must be reachable** for the tester audit and the persona sessions — both drive the live app. If it is not, every test is recorded as `not_executed` with a reason and every verdict is carried as `provisional`. Nobody fabricates a result, and nobody silently skips a test.
- **Do not sample.** Every screen in the app folder, every subject in the manifest, every persona the run calls for.
- **The tester's findings and the personas' findings stay independent.** The personas are never told what the tester concluded, and the tester never revises its own verdicts because a persona disagreed. Agreement between them only means something if neither was told the other's answer.
- **A persona is never told a finding, and that holds while the tester is changing what they see.** Every phase's tester has reasons to alter the set it hands over — a subject it removed from scope, a member that turned out not to be a control, a crop the capture caught mid-load — and each of those *is* disclosed where it changes what the picture shows, because otherwise the persona is judging something the app never did. What is never disclosed is the tester's own side of it: no verdict, no exception it upheld, no region it dismissed, no account of why a subject was removed or what its removal meant. A removed subject is simply absent from the set. The permitted form is *what this picture shows and what the app shows*; the forbidden form is *why that mattered to me*.
- **A persona-only issue is classified from the persona's own reasoning.** Each phase's tester translates every issue a persona holds and it does not into that phase's vocabulary, using the persona's `why` and `solution` and nothing else — their description of the fix usually names the category. The tester's own verdict never moves, a classification never implies agreement, and where the reasoning supports no category it is recorded as unclassified rather than guessed.
- **Persona concurrency follows the hardware.** Launch the personas in parallel only when each has its own device. Sharing one emulator, run them one at a time — several agents contending for a single device deadlock and lose their sessions. Independence is about what each persona is *told*, not about when they run.
- **A subset of personas is a legitimate run, and must be declared.** When fewer than the four run, the compiler names the absent ones on one line in the report header — the reports carry no methodology section — and never counts them as `"no problem"` votes.
- **No evidence is gathered.** Test cases are run and their outcomes are recorded in words in the reports; no screenshot, recording or file is saved from a test, no `evidence/` folder is created, and no JSON carries a `screenshot` field.
- **Only what can be seen is marked.** A detector marks an element only if it is visible in the screenshot; hidden elements — covered, off-screen, clipped, collapsed — are excluded with the reason, never boxed and never shown to a persona. Visible elements the records missed are added.
- **Personas perceive only the screen.** They are given the marked pictures and nothing else — never a manifest, a capture file, or an accessibility string — the tester names things only by tag and position, and on the device they act on screenshots, not the element listing.
- **Persona questions are asked in fixed words, in a fixed order.** Every phase asks what the persona expects, what on the screen told them, then their verdict, why, and what would make it easier — exactly as each tester's protocol words it, once each, answers recorded verbatim.
- **One form per phase, for every app.** Every report of a phase — the `.md`, the `.json`, the tester's files and the persona files — follows that phase's fixed template and key set. Two apps' reports for the same phase differ only in their values and rows; no section, column or key is added, dropped, renamed or reordered.
- **No agent carries another app's findings.** Agent instructions, templates and worked examples use placeholders (`<AppName>`, `com.example.app`, generic control descriptions) and never cite a specific application or an issue found in one. Each run judges the app in front of it; a finding from a previous app is not a precedent, a hint, or an example.
- **Withdrawals are findings too.** An instinct the tester overturned and a complaint a persona reversed after testing are reported as plainly as confirmations. They are how this method shows its work.
