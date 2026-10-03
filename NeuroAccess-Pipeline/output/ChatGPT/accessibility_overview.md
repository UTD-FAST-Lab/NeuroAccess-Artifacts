# Accessibility Overview — ChatGPT

**Generated:** 2026-09-30
**Screens evaluated:** 34 (Purpose) · 35 (Functionality) · 44 states (Location)
**Personas:** 4 of 4 — Amy, Gopal, Kwame, Yuki.
**Total issues:** 280 — 76 Critical · 73 High · 126 Medium · 5 Low

## At a glance

| Phase | Ran | Subjects evaluated | Issues | Critical | High | Medium | Low | Tester only | Persona only | Both | Provisional |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Purpose | yes | 329 elements | 241 | 72 | 54 | 113 | 2 | 1 | 128 | 112 | 7 |
| Functionality | yes | 299 elements · 61 groups | 11 | 2 | 2 | 7 | 0 | 0 | 9 | 2 | 1 |
| Location | yes | 44 screens · 2 scroll transitions | 28 | 2 | 17 | 6 | 3 | 0 | 10 | 18 | 3 |
| **Total** | | | **280** | **76** | **73** | **126** | **5** | **1** | **147** | **132** | **11** |

## What each phase found

- **Purpose** — issues are pervasive: most icons and every input field carry one, mostly held by personas alone or by both sides, and 87 icons the tester cleared as common convention were contested by a persona.
- **Functionality** — a small set of groups (11 of 61) carries the issues, split evenly between one picture doing different jobs and one job drawn different ways, and nearly all are held by personas only.
- **Location** — a missing header or navigation identifier is the recurring failure: 27 of 44 screens, plus 1 of the 2 scroll transitions judged, with most issues High and held by both sides or personas alone.

## Where the personas struggled

| Persona | Purpose | Functionality | Location | Total | Ran in all phases |
|---|---|---|---|---|---|
| Amy | 121 | 8 | 26 | 155 | yes |
| Gopal | 206 | 8 | 26 | 240 | yes |
| Kwame | 183 | 10 | 26 | 219 | yes |
| Yuki | 76 | 6 | 16 | 98 | yes |

## Coverage and what was not judged

| Phase | Not judged | Why | What it prevented |
|---|---|---|---|
| Purpose | 1 screen, 11 elements | Android Settings, outside the app package | nothing in-app; those boxes are listed as detection false positives |
| Functionality | 11 elements | no function string, handled through candidate groups | their grouping rests on device testing, 4 subjects were not executed |
| Location | 102 of 104 transitions | touches and Back keys land on a different view, judged as screens | nothing — by design; the screens they reach were judged |
| Location | 7 states | outside the app package | leaving the app is not losing your place inside it |
| Location | 9 transitions | no recoverable action in the capture | the touched or scrolled control cannot be named, including both evaluated scrolls |

## Where to read more

| Phase | Report | Data | What is there that is not here |
|---|---|---|---|
| Purpose | `output/ChatGPT/purpose-detector/purpose_report.md` | `output/ChatGPT/purpose-detector/purpose_report.json` | every element with its evidence, the contested exemptions, the disagreements |
| Functionality | `output/ChatGPT/functionality-detector/functionality_report.md` | `output/ChatGPT/functionality-detector/functionality_report.json` | every group with what each member did, the expectation mismatches, the contested exceptions |
| Location | `output/ChatGPT/location-detector/location_report.md` | `output/ChatGPT/location-detector/location_report.json` | every screen and scroll transition with its evidence, the exceptions, the capture gaps |
