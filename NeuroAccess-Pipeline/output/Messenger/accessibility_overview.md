# Accessibility Overview — Messenger

**Generated:** 2026-09-30
**Screens evaluated:** 35 (Purpose, Functionality) · 85 states (Location)
**Personas:** 4 of 4 — Amy, Gopal, Kwame, Yuki.
**Total issues:** 392 — 46 Critical · 99 High · 162 Medium · 85 Low

## At a glance

| Phase | Ran | Subjects evaluated | Issues | Critical | High | Medium | Low | Tester only | Persona only | Both | Provisional |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Purpose | yes | 488 elements | 335 | 41 | 83 | 136 | 75 | 1 | 237 | 97 | 70 |
| Functionality | yes | 55 groups | 10 | 3 | 1 | 6 | 0 | 2 | 7 | 1 | 5 |
| Location | yes | 85 screens · 2 scroll transitions | 47 | 2 | 15 | 20 | 10 | 0 | 30 | 17 | 20 |
| **Total** | | | **392** | **46** | **99** | **162** | **85** | **3** | **274** | **115** | **95** |

## What each phase found

- **Purpose** — most issues sit on icons and buttons with no readable name, and nearly all were raised by personas rather than the tester; 132 icons the tester cleared as common convention were contested by a persona.
- **Functionality** — few issues for the scale of the app, mostly one picture doing different jobs, and 3 of the 10 are Critical; about half of the subjects in the manifest could not be tapped, so the clean groups are thinner evidence than the count suggests.
- **Location** — every issue is a screen with no usable place identifier and none are scroll transitions, which both passed; the tester found none on its own, so all 47 rest on persona reports.

## Where the personas struggled

| Persona | Purpose | Functionality | Location | Total | Ran in all phases |
|---|---|---|---|---|---|
| Amy | 223 | 4 | 39 | 266 | yes |
| Gopal | 249 | 7 | 42 | 298 | yes |
| Kwame | 293 | 3 | 39 | 335 | yes |
| Yuki | 73 | 2 | 43 | 118 | yes |

## Coverage and what was not judged

| Phase | Not judged | Why | What it prevented |
|---|---|---|---|
| Purpose | 21 marked elements | testing showed they are not actionable (detection false positives) | nothing — removed from persona judgment, not counted as clean |
| Purpose | 27 persona observations | motion, contrast and target size, not purpose | those barriers are not in the issue counts |
| Functionality | 51 of 107 subjects not executed | friend-request controls cannot be tapped on the real account, among others | those groups carry no tested verdict |
| Functionality | 5 groups | in the manifest but never judged | they are not evidenced as clean |
| Functionality | 32 persona observations | out of scope here (control purpose, motion, overlap) | those barriers are not in the issue counts |
| Location | 158 of 160 transitions | touches and Back keys land on a different view, judged as screens | nothing — by design; the screens they reach were judged |
| Location | 10 out-of-app states | other apps and system surfaces | leaving the app is not losing your place inside it |
| Location | 1 screen | a web page inside the in-app browser, excluded by the tester | that screen has no verdict |

## Where to read more

| Phase | Report | Data | What is there that is not here |
|---|---|---|---|
| Purpose | `output/Messenger/purpose-detector/purpose_report.md` | `output/Messenger/purpose-detector/purpose_report.json` | every element with its evidence, the contested exemptions, the disagreements |
| Functionality | `output/Messenger/functionality-detector/functionality_report.md` | `output/Messenger/functionality-detector/functionality_report.json` | every group with what each member did, the expectation mismatches, the contested exceptions |
| Location | `output/Messenger/location-detector/location_report.md` | `output/Messenger/location-detector/location_report.json` | every screen and scroll transition with its evidence, the exceptions, the capture gaps |
