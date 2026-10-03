# Location Report — Claude

**Date:** 2026-09-30 · **Screens evaluated:** 52 of 52 in-app · **Scroll transitions evaluated:** 0 of 113 transitions (this phase judges scrolls only)
**Screen issues:** 23 · **Transition issues:** 0 · **By severity:** Critical 0 · High 6 · Medium 10 · Low 7
**Personas:** All four ran — Amy, Gopal, Kwame, Yuki.

## 1. Capture coverage

| Gap | Subjects | What it prevented |
|---|---|---|
| States with no screenshot | none | nothing |
| Transitions with no recoverable action | t7, t8, t9, t18, t44, t58, t87, t103 | the tapped control cannot be named on these touch edges; none is evaluated, so no verdict depends on them |
| Self-loops | none | nothing |
| Excluded by the tester — no picture | none | nothing |
| Excluded by the tester — system surface | none | nothing |
| Misclassified as in-app | none | nothing |
| Capture diverges from live app | s1, s2, s5, s6, s8, s16, s29 | content only (greeting wording, drawer Recents list, chat count, extra sheet rows, model names, Capabilities rows); titles unchanged and no verdict went provisional |
| Active state declared anywhere | yes | declared on the drawer opened from Chats (s9) and from Code (s44); the drawer opened from the home screen (s2) declares none |

## 2. Out of scope by construction

| Subject | Ids | Reason it carries no verdict |
|---|---|---|
| Out-of-app states | x1, x2, x3, x4, x5, x6, x7, x8, x9, x10 | another app's surface (launcher, camera, photo picker, files, Play Store billing, browser, permission prompt, system settings); leaving the app is not losing your place in it |
| Exit transitions | b1, b2, b3, b4, b5, b6, b7, b8, b9 | the move hands the user to another app; listed, not judged |
| Return transitions | b10, b11, b12, b13, b14, b15, b16, b17, b18, b19 | Back or a relaunch into the app; each lands on a screen judged on its own: b10 on s1; b11 on s5; b12 on s5; b13 on s5; b14 on s4; b15 on s4; b16 on s16; b17 on s38; b18 on s1; b19 on s1 |
| Touch and Back transitions | 113 ids in the JSON | a move to a different view is judged as a screen, not as a move; the capture holds no scroll edges, so no transition is evaluated |
| Harness transitions | b10, b17, b18, b19 | the crawler launching the app, not a user action; b10, b18 and b19 land on s1, b17 on s38, each judged as a screen |

## 3. Attribution at a glance — screens

| Screen | What it is | Identifier on screen | Issue | Category from | Severity | Found by | Personas | Tester observed | Persona said | Recommendation | Confidence |
|---|---|---|---|---|---|---|---|---|---|---|---|
| s1 | the new-chat home screen with the greeting and the composer | none; a mid-screen greeting and an empty top bar with two glyphs | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | the screen does not scroll; the top bar shows only the menu and ghost glyphs and the only large text is a greeting | Amy: "'Back at it, Ally Cooper' is a greeting to a person, not the name of a place" | add a visible title to the empty top bar, e.g. "New chat" | confirmed |
| s2 | the side menu opened from the home screen | none; the drawer head is the app name "Claude" and no item is highlighted | Missing View Identifier | tester verdict | High | both | Gopal, Kwame, Yuki | opened from the home screen the drawer shows "Claude" at the head and no highlighted item | Gopal: "'Claude' tells me the program, not the place. None of the four items is highlighted" | show which place the user came from, e.g. a highlighted "New chat" entry, rather than the bare app name | confirmed |
| s14 | the voice-input page with the language list dropped down | none; the open language list covers the page headline | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | the list covered the headline in every scroll position; Back closed it and the headline returned | Gopal: "The list has no heading of its own, and it covers the sentence that told me what the page was" | open the language list below the field or as a titled sheet so the headline stays visible | confirmed |
| s16 | the home screen with a microphone-permission banner | none; greeting only, plus a permission banner | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no test of its own: same home screen as s1 with a banner that names a permission, not a place | Gopal: "As before, the only large words are a greeting. The warning tells me what went wrong, not where I am" | add a visible title such as "New chat" | confirmed |
| s20 | the Code section (an upgrade prompt for Claude Code) | none that names the section; the only heading is an upsell halfway down | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no title in any position; the drawer opened from here highlights "Code", but the screen itself never says so | Kwame: "Nothing at the top tells me this is the Code section" | put "Code" as the top-bar title, keeping the upsell below it | confirmed |
| s28 | the upgrade page scrolled down to the Max plan | none; the "Get more Claude" title has scrolled off the top | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | the title scrolled out with the content, no collapsed bar replaced it, and a partial scroll back did not return it | Yuki: "The title has scrolled away. All I've got is an X and a price box called 'Max'" | pin "Get more Claude" (or a short "Plans" title) in the top bar beside the close X | confirmed |
| s7 | the voice-input introduction page | "Send messages to Claude using your voice." headline (self-evident body copy) | Missing View Identifier | classified from persona | Medium | persona | Kwame | the headline and three feature bullets make the page self-evidently the voice-input set-up; a close X is visible | Kwame: "The large words are a sentence describing a feature, not the name of a page" | Kwame: a short name at the top such as 'Voice mode', and 'Step 1 of 2' if it is a sequence | confirmed |
| s15 | the voice-input introduction page after choosing English (India) | the voice-input headline (self-evident body copy) | Missing View Identifier | classified from persona | Medium | persona | Kwame | no test of its own: same page and headline as s7; only the chosen language differs | Kwame: "the big words describe a feature rather than name a place" | Kwame: a short page name at the top, such as 'Voice mode', and a step indicator | confirmed |
| s19 | the Projects list filtered to archived | "Projects" title plus "No archived projects" | Missing View Identifier | classified from persona | Medium | persona | Kwame | "Projects" stayed in the top bar and "No archived projects" named the archived view below it | Kwame: "the heading does not tell me I am now in the archived section" | Kwame: change the heading to 'Archived projects', or add 'Showing: Archived' in words | confirmed |
| s21 | the Artifacts list | "Artifacts" title | Missing View Identifier | classified from persona | Medium | persona | Gopal | no test of its own: a conventional title in the top bar | Gopal: "To me an artifact is something in a museum" | Gopal: a heading in ordinary words, e.g. 'Things Claude has made for you' | confirmed |
| s22 | the Artifacts list with its source-filter menu open | "Artifacts" title, visible beside the open filter menu | Missing View Identifier | classified from persona | Medium | persona | Gopal | no test of its own: the title stays unobscured beside the menu | Gopal: "The page name is a word I do not know, and the box that opened has no title of its own" | Gopal: a plain page heading, and a heading on the little box saying what it chooses | confirmed |
| s23 | the Artifacts list filtered to Chat | "Artifacts" title | Missing View Identifier | classified from persona | Medium | persona | Gopal | no test of its own: a conventional title in the top bar | Gopal: "Same unfamiliar page name, and now the word 'Chat' by the search box" | Gopal: a plain heading and 'Showing: things made during chats' | confirmed |
| s41 | Voice settings with the language menu open | "Voice settings" title, partly overlapped by the menu | Missing View Identifier | classified from persona | Medium | persona | Gopal | no test of its own: the title stays legible above the menu | Gopal: "The list sits over the heading and cuts it in half" | Gopal: give the list its own heading, 'Choose a language', and do not cover the page heading | confirmed |
| s45 | the Artifacts list with its ownership-filter menu open | "Artifacts" title, visible beside the open filter menu | Missing View Identifier | classified from persona | Medium | persona | Gopal | no test of its own: the title stays unobscured beside the menu | Gopal: "The page name is a word I cannot learn, and the box is untitled" | Gopal: a plain page heading and a heading on the box | confirmed |
| s46 | the Artifacts list filtered to Pinned | "Artifacts" title | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame | no test of its own: a conventional title in the top bar | Amy: "The written word says 'All', while the blue pin picture suggests 'Pinned'" | Amy: write the active filter in words, e.g. 'Artifacts: Pinned' | confirmed |
| s47 | the Artifacts list filtered to Code | "Artifacts" title | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame | no test of its own: a conventional title in the top bar | Amy: "there seem to be two filters on at once, and only one of them is written in words" | Amy: show every active filter as text in one place, e.g. 'Pinned, Code' | confirmed |
| s6 | the Select model sheet over the home screen | "Select model" sheet title with a close X | Missing View Identifier | classified from persona | Low | persona | Gopal | "Select model" centred in the sheet header beside a close X | Gopal: "'model' is not a word I understand in this sense" | Gopal: a heading in ordinary words, e.g. 'Choose which version of the assistant answers you' | confirmed |
| s9 | the side menu opened from Chats, with Chats highlighted | "Chats" highlighted in the drawer | Missing View Identifier | classified from persona | Low | persona | Gopal, Kwame | the light grey pill moved to Chats, Projects or Code with the section the drawer was opened from | Gopal: "The shading is so pale I nearly missed it" | Gopal: a strong, obvious mark on the current item, and a heading for the menu | confirmed |
| s10 | the Chats list with its filter menu open | "Chats" title, visible beside the open filter menu | Missing View Identifier | classified from persona | Low | persona | Gopal | no test of its own: the title stays unobscured beside the menu | Gopal: "the small box does not say what it is for" | Gopal: give the little box a heading, e.g. 'Show which chats' | confirmed |
| s18 | the Projects list with its filter menu open | "Projects" title, visible beside the open filter menu | Missing View Identifier | classified from persona | Low | persona | Gopal | no test of its own: the title stays unobscured beside the menu | Gopal: "The page is named, but the box that has opened is not" | Gopal: a heading on the little box, e.g. 'Show which projects' | confirmed |
| s44 | the side menu opened from Code, with Code highlighted | "Code" highlighted in the drawer | Missing View Identifier | classified from persona | Low | persona | Gopal, Kwame | opened from the Code screen, the drawer carried the light grey pill on the Code row | Kwame: "the shading is so faint that I had to look carefully to see it" | Kwame: a strong, obvious marker on the current row, not only a pale tint | confirmed |
| s51 | Connectors with discovery on | "Connectors" title | Missing View Identifier | classified from persona | Low | persona | Gopal | no test of its own as a screen; flipping the discovery switch kept the user on Connectors with the title unchanged | Gopal: "The name is a term I would have to learn" | Gopal: a heading in ordinary words, e.g. 'Link to your other apps' | confirmed |
| s52 | Connectors with discovery off | "Connectors" title | Missing View Identifier | classified from persona | Low | persona | Gopal | no test of its own as a screen; flipping the discovery switch kept the user on Connectors with the title unchanged | Gopal: "Same unfamiliar term as the heading" | Gopal: a heading in ordinary words, e.g. 'Link to your other apps' | confirmed |

## 4. Attribution at a glance — transitions

| Transition | From → To | Action | Issue | Category from | Severity | Found by | Personas | Tester observed | Persona said | Recommendation | Confidence |
|---|---|---|---|---|---|---|---|---|---|---|---|
| none | — | — | — | — | — | — | — | — | — | — | — |

## 5. Exceptions

| Transition | Takeover excused | Way back | Persona lost anyway |
|---|---|---|---|
| none | — | — | — |

## 6. Disagreements

| Subject | Tester verdict | Persona | Persona verdict | Persona said | Direction |
|---|---|---|---|---|---|
| s6 | Sufficient View Identifier | Gopal | navigate with difficulty | "The heading exists, but 'model' is not a word I understand in this sense, and the names Fable, Opus, Sonnet and Haiku are invented" | persona found an issue, tester did not |
| s7 | Sufficient View Identifier | Kwame | navigate with difficulty | "The large words are a sentence describing a feature, not the name of a page" | persona found an issue, tester did not |
| s9 | Sufficient View Identifier | Gopal | navigate with difficulty | "The shading is so pale I nearly missed it. I would not trust it to tell me where I am" | persona found an issue, tester did not |
| s9 | Sufficient View Identifier | Kwame | navigate with difficulty | "The shading behind 'Chats' is so faint that I first read it as nothing, the same as the other rows" | persona found an issue, tester did not |
| s10 | Sufficient View Identifier | Gopal | navigate with difficulty | "I know the page from its heading, but the small box does not say what it is for" | persona found an issue, tester did not |
| s15 | Sufficient View Identifier | Kwame | navigate with difficulty | "Same as the first time I saw this page: the big words describe a feature rather than name a place, and I cannot tell whether this is a settings page or a first step" | persona found an issue, tester did not |
| s18 | Sufficient View Identifier | Gopal | navigate with difficulty | "The page is named, but the box that has opened is not. If interrupted I would not know what I was choosing between" | persona found an issue, tester did not |
| s19 | Sufficient View Identifier | Kwame | navigate with difficulty | "The top still says only 'Projects', exactly as it did before, so the heading does not tell me I am now in the archived section" | persona found an issue, tester did not |
| s21 | Sufficient View Identifier | Gopal | navigate with difficulty | "I can read the name, but the name is a term I would have to learn, and I cannot" | persona found an issue, tester did not |
| s22 | Sufficient View Identifier | Gopal | navigate with difficulty | "The page name is a word I do not know, and the box that opened has no title of its own" | persona found an issue, tester did not |
| s23 | Sufficient View Identifier | Gopal | navigate with difficulty | "Same unfamiliar page name, and now the word 'Chat' by the search box, which confuses me further, because I thought chats were elsewhere" | persona found an issue, tester did not |
| s41 | Sufficient View Identifier | Gopal | navigate with difficulty | "The list sits over the heading and cuts it in half. The list itself does not say what it is for" | persona found an issue, tester did not |
| s44 | Sufficient View Identifier | Gopal | navigate with difficulty | "The shading is faint, and 'Code' is not a place I understand in this program" | persona found an issue, tester did not |
| s44 | Sufficient View Identifier | Kwame | navigate with difficulty | "As with the Chats version, the shading is so faint that I had to look carefully to see it, and the large word at the top is just the app's name 'Claude'" | persona found an issue, tester did not |
| s45 | Sufficient View Identifier | Gopal | navigate with difficulty | "The page name is a word I cannot learn, and the box is untitled" | persona found an issue, tester did not |
| s46 | Sufficient View Identifier | Amy | navigate with difficulty | "I know I am in Artifacts, but I cannot tell which list I am looking at" | persona found an issue, tester did not |
| s46 | Sufficient View Identifier | Gopal | navigate with difficulty | "The page name is unfamiliar, and it says 'All' yet nothing matches; the blue pin suggests something else is chosen" | persona found an issue, tester did not |
| s46 | Sufficient View Identifier | Kwame | navigate with difficulty | "The small word beside the search box says 'All', but the blue pin button suggests only pinned ones are showing, and the message says nothing matches" | persona found an issue, tester did not |
| s47 | Sufficient View Identifier | Amy | navigate with difficulty | "Again I know it is Artifacts, but there seem to be two filters on at once, and only one of them is written in words" | persona found an issue, tester did not |
| s47 | Sufficient View Identifier | Gopal | navigate with difficulty | "Same as before: unfamiliar page name and two separate things narrowing it that I cannot hold together" | persona found an issue, tester did not |
| s47 | Sufficient View Identifier | Kwame | navigate with difficulty | "The page name is clear, but there seem to be two filters on at once, one shown only as a blue pin picture and one as a small grey word" | persona found an issue, tester did not |
| s51 | Sufficient View Identifier | Gopal | navigate with difficulty | "The name is a term I would have to learn. The sentence in the middle helps, but the heading alone would not tell me where I am if I came back to it" | persona found an issue, tester did not |
| s52 | Sufficient View Identifier | Gopal | navigate with difficulty | "Same unfamiliar term as the heading" | persona found an issue, tester did not |

## 7. Withdrawn after testing

| Subject | Who withdrew | From | To | What the test showed |
|---|---|---|---|---|
| none | — | — | — | — |

## 8. Detection false positives

| Screen | Region | What it said | Why it names no place | Persona said the same |
|---|---|---|---|---|
| s1 | header | "Back at it, Ally Cooper" | a greeting to the signed-in user; names a person, not a place | Amy, Gopal, Kwame, Yuki |
| s2 | header | "Claude" | the app's own name at the head of the drawer; names the app, not a place in it | Amy, Gopal, Kwame, Yuki |
| s5 | header | "Back at it, Ally Cooper" | the greeting dimmed behind the sheet; names the user, not a place | — |
| s6 | header | "Back at it, Ally Cooper" | the greeting dimmed behind the sheet; names the user, not a place | — |
| s9 | header | "Claude" | the app's own name at the head of the drawer; names the app, not a place in it | Gopal, Kwame |
| s11 | header | "Back at it, Ally Cooper" | the greeting dimmed behind the sheet; names the user, not a place | — |
| s13 | header | "Back at it, Ally Cooper" | the greeting dimmed behind the sheet; names the user, not a place | — |
| s16 | header | "Back at it, Ally Cooper" | a greeting to the signed-in user; names a person, not a place | Amy, Gopal, Kwame, Yuki |
| s20 | header | "Upgrade for Claude Code" | an upsell headline naming a product offer, not the section the user is in | — |
| s25 | header | "Account Actions" | a section heading over one row; names a group of controls, not the screen | — |
| s29 | header | "Memory" | a section heading within the page; names a group of settings, not the screen | — |
| s29 | header | "Tool access" | a section heading within the page; names a group of settings, not the screen | — |
| s30 | header | "Memory" | a section heading within the page; names a group of settings, not the screen | — |
| s30 | header | "Tool access" | a section heading within the page; names a group of settings, not the screen | — |
| s31 | header | "Memory" | a section heading within the page; names a group of settings, not the screen | — |
| s31 | header | "Tool access" | a section heading within the page; names a group of settings, not the screen | — |
| s32 | header | "Memory" | a section heading within the page; names a group of settings, not the screen | — |
| s33 | header | "Memory" | a section heading within the page; names a group of settings, not the screen | — |
| s34 | header | "Memory" | a section heading within the page; names a group of settings, not the screen | — |
| s44 | header | "Claude" | the app's own name at the head of the drawer; names the app, not a place in it | Gopal, Kwame |

## 9. Summary

| Found by | Screens | Transitions |
|---|---|---|
| both | 6 | 0 |
| tester | 0 | 0 |
| persona | 17 | 0 |
| none | 29 | 0 |
| not evaluated / N/A | 0 | 113 |

| Issue | Count |
|---|---|
| Missing View Identifier | 23 |
| Disappearing View Identifier | 0 |
| Classification missing | 0 |

| Severity | Issues |
|---|---|
| Critical | 0 |
| High | 6 |
| Medium | 10 |
| Low | 7 |

| Persona | Issues held |
|---|---|
| Amy | 7 |
| Gopal | 20 |
| Kwame | 13 |
| Yuki | 6 |

| Count | Value |
|---|---|
| Exceptions upheld | 0 |
| Disagreements | 17 |
| Provisional | 1 |
| Unreachable | 0 |
| Withdrawn after testing | 0 |
| Detection false positives | 20 |
| Out-of-scope observations | 7 |
