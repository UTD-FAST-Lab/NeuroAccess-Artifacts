# Accessibility Overview — Duolingo

**Generated:** 2026-09-30
**Screens evaluated:** 35 (Purpose, Functionality) · 89 states (Location)
**Personas:** 4 of 4 — Amy, Gopal, Kwame, Yuki.
**Total issues:** 350 — 164 Critical · 92 High · 35 Medium · 59 Low

## At a glance

| Phase | Ran | Subjects evaluated | Issues | Critical | High | Medium | Low | Tester only | Persona only | Both | Provisional |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Purpose | yes | 405 elements | 289 | 158 | 74 | 11 | 46 | 2 | 103 | 184 | 10 |
| Functionality | yes | 76 groups | 10 | 0 | 0 | 10 | 0 | 0 | 10 | 0 | 3 |
| Location | yes | 89 screens · 1 scroll transitions | 51 | 6 | 18 | 14 | 13 | 0 | 27 | 24 | 15 |
| **Total** | | | **350** | **164** | **92** | **35** | **59** | **2** | **140** | **208** | **28** |

## What each phase found

- **Purpose** — icons dominate: most icons on most screens carry a purpose problem, split almost evenly between nothing telling the user what a control does and what is there not helping, and more than half the issues are Critical.
- **Functionality** — a small set: every issue is held by personas alone, all Medium, and the tester found none; the recurring shapes are one picture doing different jobs and one job drawn different ways.
- **Location** — every issue is a screen with no identifier that tells the user where they are; only one scroll transition was in scope and it produced no issue.

## Where the personas struggled

| Persona | Purpose | Functionality | Location | Total | Ran in all phases |
|---|---|---|---|---|---|
| Amy | 219 | 3 | 27 | 249 | yes |
| Gopal | 271 | 3 | 45 | 319 | yes |
| Kwame | 234 | 9 | 43 | 286 | yes |
| Yuki | 116 | 1 | 14 | 131 | yes |

## Coverage and what was not judged

| Phase | Not judged | Why | What it prevented |
|---|---|---|---|
| Purpose | 17 marked elements | detection false positives, not actionable when tested | nothing — personas were told to ignore them |
| Purpose | 53 persona observations | out of scope for this phase | they never enter the issue counts |
| Functionality | 1 group | not evaluated by the tester | that group carries no verdict |
| Functionality | 4 subjects | not executed | their verdicts or resolutions are missing |
| Functionality | 16 elements | no function string | their function grouping rests on candidates and testing |
| Functionality | 44 persona observations | out of scope for this phase | they never enter the issue counts |
| Location | 150 of 151 transitions | touches and Back keys land on a different view, judged as screens | nothing — by design; the screens they reach were judged |
| Location | 23 states | outside the app package | leaving the app is not losing your place inside it |
| Location | 1 of 90 screens | excluded by the tester | that screen carries no verdict |

## Where to read more

| Phase | Report | Data | What is there that is not here |
|---|---|---|---|
| Purpose | `output/Duolingo/purpose-detector/purpose_report.md` | `purpose_report.json` | every element with its evidence, the contested exemptions, the disagreements |
| Functionality | `output/Duolingo/functionality-detector/functionality_report.md` | `functionality_report.json` | every group with what each member did, the expectation mismatches, the contested exceptions |
| Location | `output/Duolingo/location-detector/location_report.md` | `location_report.json` | every screen and scroll transition with its evidence, the exceptions, the capture gaps |
