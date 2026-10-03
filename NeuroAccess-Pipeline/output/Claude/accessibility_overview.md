# Accessibility Overview — Claude

**Generated:** 2026-09-30
**Screens evaluated:** 35 (Purpose, Functionality) · 52 states (Location)
**Personas:** 4 of 4 — Amy, Gopal, Kwame, Yuki.
**Total issues:** 144 — 42 Critical · 28 High · 67 Medium · 7 Low

## At a glance

| Phase | Ran | Subjects evaluated | Issues | Critical | High | Medium | Low | Tester only | Persona only | Both | Provisional |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Purpose | yes | 218 elements | 114 | 42 | 20 | 52 | 0 | 1 | 58 | 55 | 10 |
| Functionality | yes | 161 groups | 7 | 0 | 2 | 5 | 0 | 0 | 6 | 1 | 6 |
| Location | yes | 52 screens · 0 scroll transitions | 23 | 0 | 6 | 10 | 7 | 0 | 17 | 6 | 1 |
| **Total** | | | **144** | **42** | **28** | **67** | **7** | **1** | **81** | **62** | **17** |

## What each phase found

- **Purpose** — unclear or missing purpose is widespread, concentrated in icons (65 of 80 icons carry an issue) and in persona reports: 58 issues were raised by personas alone against 1 by the tester alone, and 46 icons the tester cleared as common convention were contested by a persona.
- **Functionality** — a small set: 7 groups with issues, 4 where one picture does different jobs and 3 where one job is drawn differently, nearly all held by personas alone and none Critical.
- **Location** — every issue is a screen with no usable place identifier, mostly persona-only and mostly Medium or Low; the capture holds no scroll transitions, so no transition was evaluated.

## Where the personas struggled

| Persona | Purpose | Functionality | Location | Total | Ran in all phases |
|---|---|---|---|---|---|
| Amy | 67 | 2 | 7 | 76 | yes |
| Gopal | 91 | 2 | 20 | 113 | yes |
| Kwame | 88 | 6 | 13 | 107 | yes |
| Yuki | 35 | 2 | 6 | 43 | yes |

## Coverage and what was not judged

| Phase | Not judged | Why | What it prevented |
|---|---|---|---|
| Purpose | 4 of 35 screens | two carry the Android system permission dialog, two are out-of-app (billing sheet, browser) | nothing in-app — the 6 buttons marked on the dialog screens were recorded as detection false positives |
| Functionality | 6 subjects | recorded as not executed by the tester | those groups carry no verdict, so a clean row is not implied for them |
| Location | 113 of 113 transitions | the capture holds no scroll transitions; touch and Back key edges land on a different view and were judged as screens | scroll persistence of place identifiers was not tested at all |
| Location | 10 states | outside the app package | nothing — leaving the app is not losing your place inside it |

## Where to read more

| Phase | Report | Data | What is there that is not here |
|---|---|---|---|
| Purpose | `output/Claude/purpose-detector/purpose_report.md` | `purpose_report.json` | every element with its evidence, the contested exemptions, the disagreements |
| Functionality | `output/Claude/functionality-detector/functionality_report.md` | `functionality_report.json` | every group with what each member did, the expectation mismatches, the contested exceptions |
| Location | `output/Claude/location-detector/location_report.md` | `location_report.json` | every screen with its evidence, the exceptions, the capture gaps |
