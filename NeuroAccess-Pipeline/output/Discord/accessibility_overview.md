# Accessibility Overview — Discord

**Generated:** 2026-09-29
**Screens evaluated:** 35 (Purpose, Functionality) · 95 states (Location)
**Personas:** 4 of 4 — Amy, Gopal, Kwame, Yuki.
**Total issues:** 346 — 92 Critical · 38 High · 74 Medium · 142 Low

## At a glance

| Phase | Ran | Subjects evaluated | Issues | Critical | High | Medium | Low | Tester only | Persona only | Both | Provisional |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Purpose | yes | 388 elements | 261 | 88 | 36 | 55 | 82 | 0 | 163 | 98 | 9 |
| Functionality | yes | 378 groups | 9 | 1 | 0 | 8 | 0 | 1 | 8 | 0 | 7 |
| Location | yes | 95 screens · 0 scroll transitions | 76 | 3 | 2 | 11 | 60 | 0 | 74 | 2 | 3 |
| **Total** | | | **346** | **92** | **38** | **74** | **142** | **1** | **245** | **100** | **19** |

## What each phase found

- **Purpose** — buttons and icons with no readable purpose are the norm, 261 issues across 388 elements, and no issue was found by the tester alone: 163 were held only by personas and 98 by both. The tester also cleared 110 unlabeled icons as common convention, and 72 of those were ones a persona could not read.
- **Functionality** — a small set: 9 groups, all but one held only by personas at Medium, plus one tester-found Critical where the same picture does different jobs. Personas expected members to behave alike where they did not in 5 groups.
- **Location** — every issue is a screen with no usable place identifier, 76 in all, 60 of them Low and 74 held only by personas. No scroll transitions were in the capture, so none were evaluated.

## Where the personas struggled

| Persona | Purpose | Functionality | Location | Total | Ran in all phases |
|---|---|---|---|---|---|
| Amy | 108 | 2 | 4 | 114 | yes |
| Gopal | 245 | 7 | 71 | 323 | yes |
| Kwame | 213 | 6 | 15 | 234 | yes |
| Yuki | 79 | 1 | 5 | 85 | yes |

## Coverage and what was not judged

| Phase | Not judged | Why | What it prevented |
|---|---|---|---|
| Purpose | 105 out-of-scope observations | raised outside this phase's question | they enter no issue count |
| Functionality | 2 groups not evaluated; 20 elements with no function string | not executed on the device; no declared string to group on | those groups carry no verdict, so they are not clean |
| Functionality | 37 out-of-scope observations | persona complaints about a control's purpose belong to Purpose | they enter no issue count |
| Location | 157 of 157 transitions | all are touches, and this phase judges scrolls only | nothing by design, but no scroll persistence was tested |
| Location | 6 out-of-app states and 16 boundary transitions | outside the app package | leaving the app is not losing your place inside it |
| Location | 3 capture divergences | live app differed from the captured screens | those verdicts are provisional |

## Where to read more

| Phase | Report | Data | What is there that is not here |
|---|---|---|---|
| Purpose | `output/Discord/purpose-detector/purpose_report.md` | `purpose_report.json` | every element with its evidence, the contested exemptions, the disagreements |
| Functionality | `output/Discord/functionality-detector/functionality_report.md` | `functionality_report.json` | every group with what each member did, the expectation mismatches, the contested exceptions |
| Location | `output/Discord/location-detector/location_report.md` | `location_report.json` | every screen and scroll transition with its evidence, the exceptions, the capture gaps |
