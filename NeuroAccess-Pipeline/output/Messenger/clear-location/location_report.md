# Location Report — Messenger

**Date:** 2026-09-30 · **Screens evaluated:** 85 of 86 in-app · **Scroll transitions evaluated:** 2 of 160 transitions (this phase judges scrolls only)
**Screen issues:** 47 · **Transition issues:** 0 · **By severity:** Critical 2 · High 15 · Medium 20 · Low 10
**Personas:** All four ran — Amy, Gopal, Kwame, Yuki.

## 1. Capture coverage

| Gap | Subjects | What it prevented |
|---|---|---|
| States with no screenshot | none | nothing — every in-app state has a picture |
| Transitions with no recoverable action | t2, t11, t14, t15, t31, t33, t36, t46, t49, t110, t158 | the action is named by position only; none of these is an evaluated transition |
| Self-loops | none | nothing — the capture has none |
| Excluded by the tester — no picture | none | nothing — no screen lacked a marked image |
| Excluded by the tester — system surface | none | nothing — no system overlay was in the in-app set |
| Misclassified as in-app | s55 | s55 is the in-app browser on a web page; it carries no verdict and was not shown to personas |
| Capture diverges from live app | s2, s11, s18, s25, s27, s30, s31, s52, s56, s58, s60, s61 | those screens are reported provisional; no verdict changed |
| Active state declared anywhere | yes | every active state was still read off the pixels |

## 2. Out of scope by construction

| Subject | Ids | Reason it carries no verdict |
|---|---|---|
| Out-of-app states | x1, x2, x3, x4, x5, x6, x7, x8, x9, x10 | launcher, permission dialog, system settings, Facebook, Play Store and share sheet are other apps; leaving the app is not losing your place in it |
| Exit transitions | b1, b2, b3, b4, b5, b6, b7, b8, b9 | they hand the user to another app |
| Return transitions | b10, b11, b12, b13, b14, b15, b16, b17, b18 | each lands on a judged screen: b10 on s1, b11 on s2, b12 on s27, b13 on s27, b14 on s49, b15 on s51, b16 on s5, b17 on s73, b18 on s73 |
| Touch and Back transitions | 158 ids in the JSON | they land on a different view, which is judged as a screen |
| Harness transitions | none | no in-app transition is a harness launch; the relaunches b13, b14 and b15 are listed as returns |

## 3. Attribution at a glance — screens

| Screen | What it is | Identifier on screen | Issue | Category from | Severity | Found by | Personas | Tester observed | Persona said | Recommendation | Confidence |
|---|---|---|---|---|---|---|---|---|---|---|---|
| s11 | Meta One offer page, scrolled | this is the Meta One offer page scrolled: its title is above the viewport and does not collapse into a bar | Missing View Identifier | tester verdict | Critical | both | Amy, Gopal, Kwame, Yuki | the large title scrolled off with the list | "There is no title on the screen." | pin the offer title, or collapse it into a persistent bar ("Meta One Core") when it scrolls away — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | provisional |
| s39 | GIF picker sheet | GIF picker sheet: no title | Missing View Identifier | tester verdict | Critical | both | Amy, Gopal, Kwame, Yuki | not tested on the device — opening the GIF picker on the device is forbidden after an earlier accidental send | "There is no title." | add a "GIFs" title to the sheet and draw the selected category with a clear fill and a word — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | provisional |
| s3 | side drawer (main menu) | the side drawer has the signed-in account name at the top and a list of destinations with no item drawn as… | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | drawer shows only "Ally Cooper" with a chevron and a settings gear at the top | "The only heading is a person's name." | add a visible drawer heading (the accessibility layer already says "All chats menu") and highlight the item for the page the drawer was opened from — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | confirmed |
| s17 | side drawer (main menu) | the side drawer has the signed-in account name at the top and a list of destinations with no item drawn as… | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | drawer shows only "Ally Cooper" with a chevron and a settings gear at the top | "The only heading is a person's name." | add a visible drawer heading (the accessibility layer already says "All chats menu") and highlight the item for the page the drawer was opened from — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | confirmed |
| s20 | search | the top bar holds only a back arrow and a search input "Ask Meta AI or search" | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | search screen shows back arrow + "Ask Meta AI or search" field | "There is no heading." | add a "Search" title or keep a visible label above the field — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | confirmed |
| s23 | story viewer after a reply | the story viewer's author name is replaced by "Sent to Deki", which reports an event, not a place | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | not tested on the device — replying to a story sends a message to a real contact, which is forbidden on this device | "'Sent to Deki' is a status message, not the name of the screen." | keep the story author's name in the top chrome and show "Sent" as a separate transient toast — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | provisional |
| s26 | side drawer (main menu) | the side drawer has the signed-in account name at the top and a list of destinations with no item drawn as… | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | drawer shows only "Ally Cooper" with a chevron and a settings gear at the top | "The only heading is a person's name." | add a visible drawer heading (the accessibility layer already says "All chats menu") and highlight the item for the page the drawer was opened from — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | confirmed |
| s28 | Communities intro | the only large text is the headline of the first card of an intro carousel | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | page has only a back arrow at top | "There is no heading at the top, only a back arrow." | add a persistent "Communities" title in the top bar above the carousel — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame | confirmed |
| s37 | search | same search screen as s20 | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | search screen shows back arrow + "Ask Meta AI or search" field | "There is no heading, only the search box and the unfamiliar words 'Meta AI'." | add a "Search" title or keep a visible label above the field — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | confirmed |
| s44 | thread settings | the top bar carries only Back and a menu | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | thread settings opened with a back arrow and three-dot menu only | "The top bar is empty." | put a title in the empty top bar, e.g. "Chat settings — Krishna Bharti", and keep it when the heading scrolls away — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | confirmed |
| s47 | story viewer after a reply | same reply-sent state as s23: "Sent to Krishna" replaces the author name | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | not tested on the device — replying to a story sends a message to a real contact, which is forbidden on this device | "The status message took the place of the name, so the screen no longer names whose story this is." | keep the story author's name in the top chrome and show "Sent" as a separate transient toast — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | provisional |
| s49 | thread settings | same thread-settings template as s44: empty top bar, contact name as content | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | thread settings opened with a back arrow and three-dot menu only | "Same as the other details page: the top bar has no title." | put a title in the empty top bar, e.g. "Chat settings — Krishna Bharti", and keep it when the heading scrolls away — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | confirmed |
| s53 | side drawer (main menu) | the side drawer has the signed-in account name at the top and a list of destinations with no item drawn as… | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | drawer shows only "Ally Cooper" with a chevron and a settings gear at the top | "The only heading is a person's name." | add a visible drawer heading (the accessibility layer already says "All chats menu") and highlight the item for the page the drawer was opened from — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | confirmed |
| s57 | side drawer (main menu) | the side drawer has the signed-in account name at the top and a list of destinations with no item drawn as… | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | drawer shows only "Ally Cooper" with a chevron and a settings gear at the top | "The only heading is a person's name." | add a visible drawer heading (the accessibility layer already says "All chats menu") and highlight the item for the page the drawer was opened from — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | confirmed |
| s59 | side drawer (main menu) | the side drawer has the signed-in account name at the top and a list of destinations with no item drawn as… | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | drawer shows only "Ally Cooper" with a chevron and a settings gear at the top | "The only heading is a person's name." | add a visible drawer heading (the accessibility layer already says "All chats menu") and highlight the item for the page the drawer was opened from — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | confirmed |
| s62 | side drawer (main menu) | the side drawer has the signed-in account name at the top and a list of destinations with no item drawn as… | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | drawer shows only "Ally Cooper" with a chevron and a settings gear at the top | "The only heading is a person's name." | add a visible drawer heading (the accessibility layer already says "All chats menu") and highlight the item for the page the drawer was opened from — addresses the tester's finding and the complaint held by Amy, Gopal, Kwame, Yuki | confirmed |
| s74 | cancel-invite confirmation | "Cancel invite?" names a question | Missing View Identifier | tester verdict | High | both | Kwame, Yuki | not tested on the device — reaching it requires creating a real supervision invite link, a change to the account | "The heading is a question, and the picture is a magnifying glass, which to me means search, so the picture and the words disagree." | name the flow in the title, e.g. "Cancel supervision invite?" under a "Family Center" header — addresses the tester's finding and the complaint held by Kwame, Yuki | provisional |
| s2 | Chats home | bottom bar "Chats" visibly highlighted (blue glyph and caption) | Missing View Identifier | classified from persona | Medium | persona | Gopal, Kwame, Yuki | Chats highlighted blue and stays while scrolling (wordmark stays pinned, search bar scrolls off) | "The top only tells me which program I am in, not which page of it." | from Gopal: Put a plain heading at the top that says "Chats" or "Your conversations", not only the name of the program. | provisional |
| s5 | Facebook Plus offer sheet | "Try Facebook Plus free for one week" | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "The heading is a sales pitch, not the name of a place." | from Amy: A plain title such as "Facebook Plus subscription" at the top, and a note saying whether I am still in Messenger. | confirmed |
| s6 | Meta One plan picker | "Meta One" | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Yuki | no device test — read from the marked image | "'Meta One', 'Core' and 'Premium' are invented names." | from Gopal: Put the plain words first, for example "Choose a paid plan", and explain in ordinary words what each plan is. | confirmed |
| s7 | Meta One offer page | "Try Meta One Core free for one week" | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "The heading is an offer with invented product names." | from Gopal: A plain heading such as "Paid plan offer" and a clearly labelled "Close" button. | confirmed |
| s22 | story viewer | "Deki" | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame, Yuki | Krishna Bharti's story showed "Krishna Bharti 20h" and X top-right | "The only label is a person's name." | from Amy: A label such as "Deki's story" and a visible pause control. | confirmed |
| s25 | Chats home | bottom bar "Chats" visibly highlighted (blue glyph and caption) | Missing View Identifier | classified from persona | Medium | persona | Gopal, Kwame, Yuki | no device test — read from the marked image | "The top only tells me which program I am in, not which page of it." | from Gopal: Put a plain heading at the top that says "Chats" or "Your conversations", not only the name of the program. | provisional |
| s27 | Chats home | bottom bar "Chats" visibly highlighted (blue glyph and caption) | Missing View Identifier | classified from persona | Medium | persona | Gopal, Kwame, Yuki | no device test — read from the marked image | "The top only tells me which program I am in, not which page of it." | from Gopal: Put a plain heading at the top that says "Chats" or "Your conversations", not only the name of the program. | provisional |
| s33 | New note with notes-visibility sheet | "New note" | Missing View Identifier | classified from persona | Medium | persona | Amy | no device test — read from the marked image | "The panel heading is a promotion, not a name, and it covers most of the screen." | from Amy: Give the panel a plain heading such as "About notes". | provisional |
| s36 | a conversation | "Ally" | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame | no device test — read from the marked image | "The top bar and the middle show two different strings for the same person." | from Amy: Use the same full name in the top bar, and mark it clearly if it is a chat with myself. | confirmed |
| s38 | New note with GIF-notes sheet | "New note" | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal | no device test — read from the marked image | "'for any mood' is a slogan and does not tell me where I am." | from Amy: Plain wording such as "Add a GIF to your note" and a button that names the action. | provisional |
| s46 | story viewer | "Krishna Bharti" | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "Only a person's name labels the screen." | from Amy: A label such as "Krishna Bharti's story" and a visible pause and mute control. | confirmed |
| s52 | Chats home | bottom bar "Chats" visibly highlighted (blue glyph and caption) | Missing View Identifier | classified from persona | Medium | persona | Gopal, Kwame, Yuki | no device test — read from the marked image | "The top only tells me which program I am in, not which page of it." | from Gopal: Put a plain heading at the top that says "Chats" or "Your conversations", not only the name of the program. | provisional |
| s60 | Archive | "Archive" | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "The two location signals contradict each other." | from Amy: Make the bottom bar match the page, or do not highlight any tab on a page that is not one of the tabs. | provisional |
| s63 | story viewer over People | "People" | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "Two screens are drawn at once and the story has no title of its own." | from Amy: Label the story clearly, for example "Deki's story". | confirmed |
| s72 | supervision profile picker | "Select the profiles you want to supervise" | Missing View Identifier | classified from persona | Medium | persona | Yuki | no device test — read from the marked image | "The heading tells me what to do, not where I am or how far along." | from Yuki: Add the flow name and a step count, like 'Teen supervision: step 1 of 2'. | confirmed |
| s73 | supervision invite link | title "Here's your link" plus body copy "Share this link with your teens to invite them to set up supervision" | Missing View Identifier | classified from persona | Medium | persona | Kwame, Yuki | no device test — read from the marked image | "'Here's your link' tells me what is on the page, not where I am." | from Kwame: A heading that names the process, such as 'Teen supervision: your invite link', and a step count. | provisional |
| s75 | supervision profile picker | "Select the profiles you want to supervise" | Missing View Identifier | classified from persona | Medium | persona | Yuki | no device test — read from the marked image | "Same as before: the heading is an instruction, not a place." | from Yuki: Name the flow at the top. Leave the 'Invite canceled' message up until I close it. | provisional |
| s84 | avatar onboarding | "Make your own avatar" | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Yuki | "Make your own avatar" onboarding with Close (X) top-left | "There's no title at the top, just an X." | from Yuki: Put 'Avatar' as a title at the top. Show 'Step 1 of 3' in words instead of dots. Keep the pictures still until I swipe. | confirmed |
| s85 | avatar onboarding | "Make your own avatar" | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Yuki | no device test — read from the marked image | "There's no title at the top, just an X." | from Yuki: Put 'Avatar' as a title at the top. Show 'Step 1 of 3' in words instead of dots. Keep the pictures still until I swipe. | confirmed |
| s86 | avatar onboarding | "Make your own avatar" | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Yuki | no device test — read from the marked image | "There's no title at the top, just an X." | from Yuki: Put 'Avatar' as a title at the top. Show 'Step 1 of 3' in words instead of dots. Keep the pictures still until I swipe. | confirmed |
| s8 | subscription feature-tour sheet | kicker "Meta AI" above the feature card, naming the plan whose tour this is | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "The heading names a feature for sale, not a part of the app." | from Amy: Give the panel a fixed title such as "Facebook Plus features" in the same place on every card, and show which card I am on, for example "2 of 5". | confirmed |
| s9 | subscription feature-tour sheet | kicker "Facebook Plus" above the feature card, naming the plan whose tour this is | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | sheet shows kicker "Instagram Plus" over "Get story rewatch insights" | "The heading names a feature for sale, not a part of the app." | from Amy: Give the panel a fixed title such as "Facebook Plus features" in the same place on every card, and show which card I am on, for example "2 of 5". | confirmed |
| s10 | subscription feature-tour sheet | kicker "Facebook Plus" above the feature card, naming the plan whose tour this is | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "The heading names a feature for sale, not a part of the app." | from Amy: Give the panel a fixed title such as "Facebook Plus features" in the same place on every card, and show which card I am on, for example "2 of 5". | confirmed |
| s12 | subscription feature-tour sheet | kicker "Facebook Plus" above the feature card, naming the plan whose tour this is | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "The heading names a feature for sale, not a part of the app." | from Amy: Give the panel a fixed title such as "Facebook Plus features" in the same place on every card, and show which card I am on, for example "2 of 5". | confirmed |
| s13 | subscription feature-tour sheet | kicker "Facebook Plus" above the feature card, naming the plan whose tour this is | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "The heading names a feature for sale, not a part of the app." | from Amy: Give the panel a fixed title such as "Facebook Plus features" in the same place on every card, and show which card I am on, for example "2 of 5". | confirmed |
| s14 | subscription feature-tour sheet | kicker "Facebook Plus" above the feature card, naming the plan whose tour this is | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "The heading names a feature for sale, not a part of the app." | from Amy: Give the panel a fixed title such as "Facebook Plus features" in the same place on every card, and show which card I am on, for example "2 of 5". | confirmed |
| s15 | subscription feature-tour sheet | kicker "Facebook Plus" above the feature card, naming the plan whose tour this is | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "The heading names a feature for sale, not a part of the app." | from Amy: Give the panel a fixed title such as "Facebook Plus features" in the same place on every card, and show which card I am on, for example "2 of 5". | confirmed |
| s16 | subscription feature-tour sheet | kicker "Facebook Plus" above the feature card, naming the plan whose tour this is | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "The heading names a feature for sale, not a part of the app." | from Amy: Give the panel a fixed title such as "Facebook Plus features" in the same place on every card, and show which card I am on, for example "2 of 5". | confirmed |
| s54 | subscription feature-tour sheet | kicker "Facebook Plus" above the feature card, naming the plan whose tour this is | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "The heading names a feature for sale, not a place, and nothing tells me whether I am in Messenger." | from Amy: A fixed title naming the page, for example "Facebook Plus features". | confirmed |
| s70 | Me with username sheet | "Me" | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | no device test — read from the marked image | "The panel has no heading, only 'm.me/', which is part of a web address and not a name." | from Amy: A heading on the panel such as "Username". | confirmed |

## 4. Attribution at a glance — transitions

| Transition | From → To | Action | Issue | Category from | Severity | Found by | Personas | Tester observed | Persona said | Recommendation | Confidence |
|---|---|---|---|---|---|---|---|---|---|---|---|
| none | — | — | — | — | — | — | — | — | — | — | — |

## 5. Exceptions

| Transition | Takeover excused | Way back | Persona lost anyway |
|---|---|---|---|
| s22, s46, s63 | story viewer — full-screen takeover | Close (X) top-right is visible and returned the user to People | Amy, Gopal, Kwame, Yuki |
| s84, s85, s86 | avatar onboarding — full-screen takeover | Close (X) top-left is visible and returned the user to the Avatar page | Amy, Gopal, Yuki |

## 6. Disagreements

| Subject | Tester verdict | Persona | Persona verdict | Persona said | Direction |
|---|---|---|---|---|---|
| s2 | Sufficient View Identifier | Gopal | navigate with difficulty | "The top only tells me which program I am in, not which page of it." | persona found an issue, tester did not |
| s2 | Sufficient View Identifier | Kwame | navigate with difficulty | "The only words in the top strip are the app's own name, 'messenger', which tells me which app I am in, not which part of it." | persona found an issue, tester did not |
| s2 | Sufficient View Identifier | Yuki | navigate with difficulty | "The top only says 'messenger', which is just the app's name." | persona found an issue, tester did not |
| s5 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading is a sales pitch, not the name of a place." | persona found an issue, tester did not |
| s5 | Sufficient View Identifier | Gopal | navigate with difficulty | "The heading is an advertisement, not the name of a place, and it sits halfway down the page." | persona found an issue, tester did not |
| s5 | Sufficient View Identifier | Kwame | navigate with difficulty | "The large words are a sales line, not a name for a place." | persona found an issue, tester did not |
| s5 | Sufficient View Identifier | Yuki | navigate with difficulty | "It feels like I've been dropped into an advert." | persona found an issue, tester did not |
| s6 | Sufficient View Identifier | Amy | navigate with difficulty | "'Choose your plan' is literal, but 'Meta One' is a brand name and I cannot tell what it is in relation to Messenger." | persona found an issue, tester did not |
| s6 | Sufficient View Identifier | Gopal | navigate with difficulty | "'Meta One', 'Core' and 'Premium' are invented names." | persona found an issue, tester did not |
| s6 | Sufficient View Identifier | Yuki | navigate with difficulty | "The title names what to do, not where I am." | persona found an issue, tester did not |
| s7 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading is a promotion, not a place name." | persona found an issue, tester did not |
| s7 | Sufficient View Identifier | Gopal | navigate with difficulty | "The heading is an offer with invented product names." | persona found an issue, tester did not |
| s7 | Sufficient View Identifier | Kwame | navigate with difficulty | "Like the other offer page, the large words are a sales line rather than a name for where I am." | persona found an issue, tester did not |
| s7 | Sufficient View Identifier | Yuki | navigate with difficulty | "It's another sales page with a long list." | persona found an issue, tester did not |
| s22 | Sufficient View Identifier | Amy | navigate with difficulty | "The only label is a person's name." | persona found an issue, tester did not |
| s22 | Sufficient View Identifier | Gopal | navigate with difficulty | "Only a person's name tells me anything." | persona found an issue, tester did not |
| s22 | Sufficient View Identifier | Kwame | navigate with difficulty | "The only name is the person's name and a time in small white letters over a large photo." | persona found an issue, tester did not |
| s22 | Sufficient View Identifier | Yuki | navigate with difficulty | "It's a full-screen story photo with a progress bar at the top that's ticking along, plus emoji reply bubbles and a 'Send message' box." | persona found an issue, tester did not |
| s25 | Sufficient View Identifier | Gopal | navigate with difficulty | "The top only tells me which program I am in, not which page of it." | persona found an issue, tester did not |
| s25 | Sufficient View Identifier | Kwame | navigate with difficulty | "The only words in the top strip are the app's own name, 'messenger', which tells me which app I am in, not which part of it." | persona found an issue, tester did not |
| s25 | Sufficient View Identifier | Yuki | navigate with difficulty | "The top only says 'messenger', which is just the app's name." | persona found an issue, tester did not |
| s27 | Sufficient View Identifier | Gopal | navigate with difficulty | "The top only tells me which program I am in, not which page of it." | persona found an issue, tester did not |
| s27 | Sufficient View Identifier | Kwame | navigate with difficulty | "The only words in the top strip are the app's own name, 'messenger', which tells me which app I am in, not which part of it." | persona found an issue, tester did not |
| s27 | Sufficient View Identifier | Yuki | navigate with difficulty | "The top only says 'messenger', which is just the app's name." | persona found an issue, tester did not |
| s33 | Sufficient View Identifier | Amy | navigate with difficulty | "The panel heading is a promotion, not a name, and it covers most of the screen." | persona found an issue, tester did not |
| s36 | Sufficient View Identifier | Amy | navigate with difficulty | "The top bar and the middle show two different strings for the same person." | persona found an issue, tester did not |
| s36 | Sufficient View Identifier | Gopal | navigate with difficulty | "The name is my own." | persona found an issue, tester did not |
| s36 | Sufficient View Identifier | Kwame | navigate with difficulty | "The top says only 'Ally' and the middle says 'Ally Cooper'." | persona found an issue, tester did not |
| s38 | Sufficient View Identifier | Amy | navigate with difficulty | "'for any mood' is a slogan and does not tell me where I am." | persona found an issue, tester did not |
| s38 | Sufficient View Identifier | Gopal | navigate with difficulty | "'New note' I understand." | persona found an issue, tester did not |
| s46 | Sufficient View Identifier | Amy | navigate with difficulty | "Only a person's name labels the screen." | persona found an issue, tester did not |
| s46 | Sufficient View Identifier | Gopal | navigate with difficulty | "Only a person's name tells me anything." | persona found an issue, tester did not |
| s46 | Sufficient View Identifier | Kwame | navigate with difficulty | "The only name is the person's name and a time in small white letters over a large photo." | persona found an issue, tester did not |
| s46 | Sufficient View Identifier | Yuki | navigate with difficulty | "It's a full-screen story photo with a progress bar at the top that's ticking along, plus emoji reply bubbles and a 'Send message' box." | persona found an issue, tester did not |
| s52 | Sufficient View Identifier | Gopal | navigate with difficulty | "The top only tells me which program I am in, not which page of it." | persona found an issue, tester did not |
| s52 | Sufficient View Identifier | Kwame | navigate with difficulty | "The only words in the top strip are the app's own name, 'messenger', which tells me which app I am in, not which part of it." | persona found an issue, tester did not |
| s52 | Sufficient View Identifier | Yuki | navigate with difficulty | "The top only says 'messenger', which is just the app's name." | persona found an issue, tester did not |
| s60 | Sufficient View Identifier | Amy | navigate with difficulty | "The two location signals contradict each other." | persona found an issue, tester did not |
| s60 | Sufficient View Identifier | Gopal | navigate with difficulty | "The heading and the bottom row disagree." | persona found an issue, tester did not |
| s60 | Sufficient View Identifier | Kwame | navigate with difficulty | "The top says 'Archive' but the bottom row lights up Notifications, and 'Chats' is blue as well." | persona found an issue, tester did not |
| s60 | Sufficient View Identifier | Yuki | navigate with difficulty | "The top says Archive and the bottom says Notifications, so the two disagree." | persona found an issue, tester did not |
| s63 | Sufficient View Identifier | Amy | navigate with difficulty | "Two screens are drawn at once and the story has no title of its own." | persona found an issue, tester did not |
| s63 | Sufficient View Identifier | Gopal | navigate with difficulty | "There are two headings at once: 'People' above and 'Deki' in the middle." | persona found an issue, tester did not |
| s63 | Sufficient View Identifier | Kwame | navigate with difficulty | "Two names are showing at once, 'People' and 'Deki', and the picture is half way between two pages." | persona found an issue, tester did not |
| s63 | Sufficient View Identifier | Yuki | navigate with difficulty | "There are two names: 'People' greyed at the top and 'Deki' on the story sliding up over it." | persona found an issue, tester did not |
| s72 | Sufficient View Identifier | Yuki | navigate with difficulty | "The heading tells me what to do, not where I am or how far along." | persona found an issue, tester did not |
| s73 | Sufficient View Identifier | Kwame | navigate with difficulty | "'Here's your link' tells me what is on the page, not where I am." | persona found an issue, tester did not |
| s73 | Sufficient View Identifier | Yuki | navigate with difficulty | "'Here's your link' could be any link." | persona found an issue, tester did not |
| s75 | Sufficient View Identifier | Yuki | navigate with difficulty | "Same as before: the heading is an instruction, not a place." | persona found an issue, tester did not |
| s84 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading is an instruction in the middle of the screen, not a page name." | persona found an issue, tester did not |
| s84 | Sufficient View Identifier | Gopal | navigate with difficulty | "The heading is near the bottom under a large picture, and 'avatar' is a word I do not know." | persona found an issue, tester did not |
| s84 | Sufficient View Identifier | Yuki | navigate with difficulty | "There's no title at the top, just an X." | persona found an issue, tester did not |
| s85 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading is an instruction in the middle of the screen, not a page name." | persona found an issue, tester did not |
| s85 | Sufficient View Identifier | Gopal | navigate with difficulty | "The heading is near the bottom under a large picture, and 'avatar' is a word I do not know." | persona found an issue, tester did not |
| s85 | Sufficient View Identifier | Yuki | navigate with difficulty | "There's no title at the top, just an X." | persona found an issue, tester did not |
| s86 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading is an instruction in the middle of the screen, not a page name." | persona found an issue, tester did not |
| s86 | Sufficient View Identifier | Gopal | navigate with difficulty | "The heading is near the bottom under a large picture, and 'avatar' is a word I do not know." | persona found an issue, tester did not |
| s86 | Sufficient View Identifier | Yuki | navigate with difficulty | "There's no title at the top, just an X." | persona found an issue, tester did not |
| s8 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading names a feature for sale, not a part of the app." | persona found an issue, tester did not |
| s8 | Sufficient View Identifier | Gopal | navigate with difficulty | "The large words describe a feature for sale, not a place in the program." | persona found an issue, tester did not |
| s8 | Sufficient View Identifier | Kwame | navigate with difficulty | "The large words name a feature, not a place, and the small 'Meta AI' overlaps the picture so it is hard to read." | persona found an issue, tester did not |
| s8 | Sufficient View Identifier | Yuki | navigate with difficulty | "It's a sheet on top of another sheet, plus carousel dots." | persona found an issue, tester did not |
| s9 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading names a feature for sale, not a part of the app." | persona found an issue, tester did not |
| s9 | Sufficient View Identifier | Gopal | navigate with difficulty | "The large words describe a feature for sale, not a place in the program." | persona found an issue, tester did not |
| s9 | Sufficient View Identifier | Kwame | navigate with difficulty | "The large words describe a feature being sold to me, not a place." | persona found an issue, tester did not |
| s9 | Sufficient View Identifier | Yuki | navigate with difficulty | "The bold title names one feature, and a small 'Facebook Plus' line sits above it." | persona found an issue, tester did not |
| s10 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading names a feature for sale, not a part of the app." | persona found an issue, tester did not |
| s10 | Sufficient View Identifier | Gopal | navigate with difficulty | "The large words describe a feature for sale, not a place in the program." | persona found an issue, tester did not |
| s10 | Sufficient View Identifier | Kwame | navigate with difficulty | "The large words describe a feature being sold to me, not a place." | persona found an issue, tester did not |
| s10 | Sufficient View Identifier | Yuki | navigate with difficulty | "The bold title names one feature, and a small 'Facebook Plus' line sits above it." | persona found an issue, tester did not |
| s12 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading names a feature for sale, not a part of the app." | persona found an issue, tester did not |
| s12 | Sufficient View Identifier | Gopal | navigate with difficulty | "The large words describe a feature for sale, not a place in the program." | persona found an issue, tester did not |
| s12 | Sufficient View Identifier | Kwame | navigate with difficulty | "The large words describe a feature being sold to me, not a place." | persona found an issue, tester did not |
| s12 | Sufficient View Identifier | Yuki | navigate with difficulty | "The bold title names one feature, and a small 'Facebook Plus' line sits above it." | persona found an issue, tester did not |
| s13 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading names a feature for sale, not a part of the app." | persona found an issue, tester did not |
| s13 | Sufficient View Identifier | Gopal | navigate with difficulty | "The large words describe a feature for sale, not a place in the program." | persona found an issue, tester did not |
| s13 | Sufficient View Identifier | Kwame | navigate with difficulty | "The large words describe a feature being sold to me, not a place." | persona found an issue, tester did not |
| s13 | Sufficient View Identifier | Yuki | navigate with difficulty | "The bold title names one feature, and a small 'Facebook Plus' line sits above it." | persona found an issue, tester did not |
| s14 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading names a feature for sale, not a part of the app." | persona found an issue, tester did not |
| s14 | Sufficient View Identifier | Gopal | navigate with difficulty | "The large words describe a feature for sale, not a place in the program." | persona found an issue, tester did not |
| s14 | Sufficient View Identifier | Kwame | navigate with difficulty | "The large words describe a feature being sold to me, not a place." | persona found an issue, tester did not |
| s14 | Sufficient View Identifier | Yuki | navigate with difficulty | "The bold title names one feature, and a small 'Facebook Plus' line sits above it." | persona found an issue, tester did not |
| s15 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading names a feature for sale, not a part of the app." | persona found an issue, tester did not |
| s15 | Sufficient View Identifier | Gopal | navigate with difficulty | "The large words describe a feature for sale, not a place in the program." | persona found an issue, tester did not |
| s15 | Sufficient View Identifier | Kwame | navigate with difficulty | "The large words describe a feature being sold to me, not a place." | persona found an issue, tester did not |
| s15 | Sufficient View Identifier | Yuki | navigate with difficulty | "The bold title names one feature, and a small 'Facebook Plus' line sits above it." | persona found an issue, tester did not |
| s16 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading names a feature for sale, not a part of the app." | persona found an issue, tester did not |
| s16 | Sufficient View Identifier | Gopal | navigate with difficulty | "The large words describe a feature for sale, not a place in the program." | persona found an issue, tester did not |
| s16 | Sufficient View Identifier | Kwame | navigate with difficulty | "The large words describe a feature being sold to me, not a place." | persona found an issue, tester did not |
| s16 | Sufficient View Identifier | Yuki | navigate with difficulty | "The bold title names one feature, and a small 'Facebook Plus' line sits above it." | persona found an issue, tester did not |
| s54 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading names a feature for sale, not a place, and nothing tells me whether I am in Messenger." | persona found an issue, tester did not |
| s54 | Sufficient View Identifier | Gopal | navigate with difficulty | "The large words describe a feature for sale, not a place in the program." | persona found an issue, tester did not |
| s54 | Sufficient View Identifier | Kwame | navigate with difficulty | "The large words describe a feature being sold to me, not a place." | persona found an issue, tester did not |
| s54 | Sufficient View Identifier | Yuki | navigate with difficulty | "The bold title names one feature, and a small 'Facebook Plus' line sits above it." | persona found an issue, tester did not |
| s70 | Sufficient View Identifier | Amy | navigate with difficulty | "The panel has no heading, only 'm.me/', which is part of a web address and not a name." | persona found an issue, tester did not |
| s70 | Sufficient View Identifier | Gopal | navigate with difficulty | "The card has no heading." | persona found an issue, tester did not |
| s70 | Sufficient View Identifier | Kwame | navigate with difficulty | "The panel has no heading." | persona found an issue, tester did not |
| s70 | Sufficient View Identifier | Yuki | navigate with difficulty | "The sheet at the bottom has no heading, just 'm.me/' and two options." | persona found an issue, tester did not |

## 7. Withdrawn after testing

| Subject | Who withdrew | From | To | What the test showed |
|---|---|---|---|---|
| s28 | tester | Sufficient View Identifier | Missing View Identifier | the headline is the first card of a carousel |
| s56 | Kwame | navigate with difficulty | reversed | On the phone only Notifications was coloured, so the conflict I saw in the picture was not there. |
| s58 | Kwame | navigate with difficulty | reversed | On the phone the heading and the bottom row agreed while I scrolled. |
| t132 | Amy | navigate with difficulty | reversed | Scrolling only moved the list; the "Me" title stayed and no page opened. |
| t132 | Gopal | navigate with difficulty | reversed | Trying it showed I was wrong to worry here. |
| t132 | Kwame | navigate with difficulty | reversed | On the phone, scrolling kept me on 'Me' with its name at the top; the Avatar page did not appear. |
| t132 | Yuki | navigate with difficulty | reversed | Scrolling never changes the page. |
| t133 | Amy | navigate with difficulty | reversed | Scrolling only moved the list; the "Me" title stayed and no page opened. |
| t133 | Gopal | navigate with difficulty | reversed | Trying it showed I was wrong to worry here. |
| t133 | Kwame | navigate with difficulty | reversed | On the phone, scrolling kept me on 'Me' with its name at the top; the Avatar page did not appear. |
| t133 | Yuki | navigate with difficulty | reversed | Scrolling never changes the page. |

## 8. Detection false positives

| Screen | Region | What it said | Why it names no place | Persona said the same |
|---|---|---|---|---|
| s8 | header | "More image and video creation" | title of one feature card in a swipeable carousel | Amy, Gopal, Kwame |
| s9 | header | "Get story rewatch insights" | title of one feature card in a swipeable carousel | Amy, Gopal, Kwame, Yuki |
| s10 | header | "Search your story viewer list" | title of one feature card in a swipeable carousel | Amy, Gopal, Kwame, Yuki |
| s12 | header | "Choose a custom app icon" | title of one feature card in a swipeable carousel | Amy, Gopal, Kwame, Yuki |
| s13 | header | "Choose a custom app icon" | title of one feature card in a swipeable carousel | Amy, Gopal, Kwame, Yuki |
| s14 | header | "Super react to stories" | title of one feature card in a swipeable carousel | Amy, Gopal, Kwame, Yuki |
| s15 | header | "Extend your story's expiration" | title of one feature card in a swipeable carousel | Amy, Gopal, Kwame, Yuki |
| s16 | header | "Message with custom fonts" | title of one feature card in a swipeable carousel | Amy, Gopal, Kwame, Yuki |
| s24 | header | "Siquem Lsm" | contact name repeated in the profile card at the start of the thread | none |
| s28 | header | "Build a chat-based community on Messenger" | headline of the first card of a swipeable intro carousel | Amy, Gopal, Kwame |
| s36 | header | "Ally Cooper" | contact name repeated in the profile card at the start of the thread | none |
| s42 | header | "Deki" | contact name repeated in the profile card at the start of the thread | none |
| s43 | header | "Marco Peralta" | contact name repeated in the profile card at the start of the thread | none |
| s44 | header | "Marco Peralta." | contact name heading the page | Amy, Gopal, Kwame, Yuki |
| s48 | header | "Krishna Bharti" | contact name repeated in the profile card at the start of the thread | none |
| s49 | header | "Krishna Bharti." | contact name heading the page | Gopal, Kwame, Yuki |
| s50 | header | "Krishna Bharti" | contact name repeated in the profile card at the start of the thread | none |
| s51 | header | "Krishna Bharti" | contact name repeated in the profile card at the start of the thread | none |
| s54 | header | "Preview stories" | title of one feature card in a swipeable carousel | Amy, Gopal, Kwame, Yuki |
| s61 | navigation | nav: 1 active, Friend requests, All, Current city | filter chips inside People ("1 active" selected) | none |
| s74 | header | "Cancel invite?" | names a yes/no question, not a place | Kwame, Yuki |

## 9. Summary

| Found by | Screens | Transitions |
|---|---|---|
| both | 17 | 0 |
| tester | 0 | 0 |
| persona | 30 | 0 |
| none | 38 | 2 |
| not evaluated / N/A | 1 | 158 |

| Issue | Count |
|---|---|
| Missing View Identifier | 47 |
| Disappearing View Identifier | 0 |
| Classification missing | 0 |

| Severity | Issues |
|---|---|
| Critical | 2 |
| High | 15 |
| Medium | 20 |
| Low | 10 |

| Persona | Issues held |
|---|---|
| Amy | 39 |
| Gopal | 42 |
| Kwame | 39 |
| Yuki | 43 |

| Count | Value |
|---|---|
| Exceptions upheld | 2 |
| Disagreements | 30 |
| Provisional | 20 |
| Unreachable | 0 |
| Withdrawn after testing | 11 |
| Detection false positives | 21 |
| Out-of-scope observations | 30 |
