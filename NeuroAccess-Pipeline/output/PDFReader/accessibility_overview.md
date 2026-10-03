# Accessibility Overview — PDFReader

**Generated:** 2026-09-30
**Screens evaluated:** 35 (Purpose, Functionality) · 37 states (Location)
**Personas:** 4 of 4 — Amy, Gopal, Kwame, Yuki.
**Total issues:** 200 — 83 Critical · 12 High · 103 Medium · 2 Low

## At a glance

| Phase | Ran | Subjects evaluated | Issues | Critical | High | Medium | Low | Tester only | Persona only | Both | Provisional |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Purpose | yes | 412 elements | 166 | 75 | 8 | 81 | 2 | 0 | 89 | 77 | 0 |
| Functionality | yes | 50 groups | 7 | 1 | 1 | 5 | 0 | 2 | 4 | 1 | 1 |
| Location | yes | 36 screens · 0 scroll transitions | 27 | 7 | 3 | 17 | 0 | 0 | 24 | 3 | 0 |
| **Total** | | | **200** | **83** | **12** | **103** | **2** | **2** | **117** | **81** | **1** |

## What each phase found

- **Purpose** — unlabeled or unclear controls on a very large scale: 95 of 99 icons and 71 of 311 buttons are issues, and the tester found none that a persona did not also hold. Critical is the largest severity band, and 45 icons the tester cleared as common convention were contested by a persona.
- **Functionality** — few groups are affected, and most conflicts are one job drawn in more than one way. The report's own by-kind counts add to 8 against 7 groups with issues, reported here as they stand.
- **Location** — every issue is a screen with no usable place identifier, and the tester held almost none of them itself (3 of 27 are shared with a persona, 24 are persona-only). No scroll transitions were captured, so the phase's central test had nothing to run on.

## Where the personas struggled

| Persona | Purpose | Functionality | Location | Total | Ran in all phases |
|---|---|---|---|---|---|
| Amy | 58 | 5 | 23 | 86 | yes |
| Gopal | 133 | 4 | 9 | 146 | yes |
| Kwame | 119 | 4 | 25 | 148 | yes |
| Yuki | 45 | 0 | 1 | 46 | yes |

## Coverage and what was not judged

| Phase | Not judged | Why | What it prevented |
|---|---|---|---|
| Purpose | 4 elements on 2 screens | system settings page, judged out of app | nothing in-app; those elements carry no verdict |
| Purpose | 188 persona observations | about contrast, target size and the like, not purpose | they are listed in the report and not counted as issues |
| Functionality | 74 elements | no function string | grouping by declared job was not possible for them; candidates were raised and settled by tapping |
| Functionality | 2 test cases | purchase flow off-limits | one group's verdict is provisional |
| Functionality | 51 persona observations | about a control's purpose, not group consistency | listed in the report and not counted as issues |
| Location | 93 of 93 transitions | the capture holds no scroll events | the scroll-persistence test did not run at all |
| Location | 1 screen, 6 out-of-app states | an ad screen, and other apps' surfaces | no verdict on any of them |
| Location | 27 exit and return transitions | not scroll moves | the screens they reach were judged as screens |

## Where to read more

| Phase | Report | Data | What is there that is not here |
|---|---|---|---|
| Purpose | `output/PDFReader/purpose-detector/purpose_report.md` | `output/PDFReader/purpose-detector/purpose_report.json` | every element with its evidence, the contested exemptions, the disagreements |
| Functionality | `output/PDFReader/functionality-detector/functionality_report.md` | `output/PDFReader/functionality-detector/functionality_report.json` | every group with what each member did, the expectation mismatches, the contested exceptions |
| Location | `output/PDFReader/location-detector/location_report.md` | `output/PDFReader/location-detector/location_report.json` | every screen with its evidence, the exceptions, the capture gaps |
