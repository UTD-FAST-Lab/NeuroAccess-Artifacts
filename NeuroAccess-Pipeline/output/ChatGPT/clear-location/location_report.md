# Location Report — ChatGPT

**Date:** 2026-09-30 · **Screens evaluated:** 44 of 44 in-app · **Scroll transitions evaluated:** 2 of 104 transitions (this phase judges scrolls only)
**Screen issues:** 27 · **Transition issues:** 1 · **By severity:** Critical 2 · High 17 · Medium 6 · Low 3
**Personas:** All four ran — Amy, Gopal, Kwame, Yuki.

## 1. Capture coverage

| Gap | Subjects | What it prevented |
|---|---|---|
| States with no screenshot | none | nothing |
| Transitions with no recoverable action | t14, t16, t32, t41, t43, t46, t67, t99, t103 | the touched or scrolled control cannot be named; t32 and t43, the two evaluated scrolls, were described by direction only and neither reproduced as a scroll on the device |
| Self-loops | none | nothing |
| Excluded by the tester — no picture | none | nothing |
| Excluded by the tester — system surface | none | nothing |
| Misclassified as in-app | none | nothing |
| Capture diverges from live app | s1, s2, s11, s15, s23, s24, s25 | the live app no longer matches the capture (home voice-chat row gone, template sheet replaced by a dialog, Library tab names, a new project); s2 could not be reached live; issues on s1, s2 and s11 are provisional |
| Active state declared anywhere | yes | declared on the Library, Projects and gallery tab rows; the side menu and the Go/Plus switcher declare none, so their active states were read off the pixels |

## 2. Out of scope by construction

| Subject | Ids | Reason it carries no verdict |
|---|---|---|
| Out-of-app states | x1, x2, x3, x4, x5, x6, x7 | another app's surface (launcher, Play Store billing, system settings, share sheet, photo picker, browser); leaving the app is not losing your place in it |
| Exit transitions | b1, b2, b3, b4, b5, b6, b7 | the move hands the user to another app; listed, not judged |
| Return transitions | b8, b9, b10, b11, b12, b13, b14, b15 | Back or a relaunch into the app; each lands on a screen judged on its own: b8 on s1; b9 on s5; b10 on s6; b11 on s5; b12 on s1; b13 on s11; b14 on s13; b15 on s43 |
| Touch and Back transitions | 102 ids in the JSON | a move to a different view is judged as a screen, not as a move; the two scroll edges are the only evaluated transitions |
| Harness transitions | b8, b15 | the crawler launching the app, not a user action; b8 lands on s1, b15 lands on s43, each judged as a screen |

## 3. Attribution at a glance — screens

| Screen | What it is | Identifier on screen | Issue | Category from | Severity | Found by | Personas | Tester observed | Persona said | Recommendation | Confidence |
|---|---|---|---|---|---|---|---|---|---|---|---|
| s10 | the drawing sheet over the image gallery | "Trending" tab with a filled pill, fully legible above the drawing sheet; the sheet itself (pen / shapes / eraser tools, colour row) has no... | Missing View Identifier | classified from persona | Critical | persona | Amy, Gopal, Kwame, Yuki | the drawing sheet opened over the lower two-thirds; "Trending" (filled pill) and "Templates" stayed fully legible and undimmed above it in every gesture; each swipe drew a stroke on the... | Gopal: "This panel has no heading and no words of any kind. The only marked box is the 'Trending' and 'Templates' row behind it, which belongs to the page underneath, not to the thing I am looking at" | give the sheet a title such as "Sketch" so the tool names itself | confirmed |
| s22 | the Library in selection mode ("1 selected", "Files" tab) | none that names the section; "1 selected" replaces the "Library" title and the highlighted tab names a filter ("Files") | Missing View Identifier | tester verdict | Critical | both | Amy, Gopal, Kwame, Yuki | no test of its own: entering selection mode replaces the section name with "1 selected"; a filter tab ("Files") does not name the part of the app | Gopal: "The heading says I have chosen one thing, and the page shows nothing at all. I would not remember that I had chosen a picture on a different tab, so the heading contradicts what is in front of me" | keep the section in the title while selecting, e.g. "Library — 1 selected" | confirmed |
| s1 | the new-chat home screen | none; the top bar holds "Get Plus" (an upgrade button) and two icon buttons; the rest is suggestion rows and the "Ask ChatGPT" composer | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no title in any state; the top bar stays "Get Plus" plus two icon buttons; the live home no longer shows the "Start a voice chat" row (capture divergence) — the answer is unchanged | Amy: "There is no title anywhere. The top bar has a three-line button, 'Get Plus' and a speech-bubble icon, none of which says what this screen is" | give the home a visible title in the top bar, e.g. "New chat", so the start screen names itself | provisional |
| s2 | the microphone-access dialog over a dimmed home screen | none; the dialog has body copy "Please enable microphone access in System Settings to use Voice." and buttons "Cancel" / "Open settings"... | Missing View Identifier | tester verdict | High | both | Gopal, Kwame, Yuki | not tested on the device: the live home screen no longer shows the "Start a voice chat" row that opened this dialog, and reaching it by another route would... | Gopal: "I can work it out by reading, but the box has no title. It warns me I will be sent away to 'Android settings' and must 'return to ChatGPT to continue' — that is exactly the sort of thing I would forget halfway through..." | give the dialog a title that says where it belongs, e.g. "Voice — microphone access", and keep the home screen behind it less heavily dimmed | provisional |
| s9 | the side menu (opened from the home screen) | none that names the section; the header is the app wordmark "ChatGPT" and no section entry is highlighted | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | no section entry (Images, Library, Projects, Scheduled, Plugins) was ever highlighted, whichever section the menu was opened from; the only highlight the menu ever showed was a grey fill on... | Amy: "'ChatGPT' is the name of the app, not of this menu or of where I am. I know it is a menu only from its shape" | highlight the current section in the menu (it already highlights the current chat row) and replace the wordmark with a menu heading such as "Menu" | confirmed |
| s17 | the full-screen image viewer | none; top row is an X, a ⋮, a download icon and "Share"; bottom row "Edit" / "Resize" / "Remove"; the rest is the photo | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no title in any state; a downward swipe dismissed the viewer back to Library, and the X also returned to Library — the way back is visible and works | Amy: "There is no title. I can tell it is an image viewer only from the picture and the buttons" | add a small caption naming the image or its source ("Library") in the top row | confirmed |
| s19 | the Library in selection mode ("Select items", "Images" tab) | none that names the section; "Select items" replaces the "Library" title and the highlighted tab names a filter ("Images") | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | in selection mode the top bar reads "Select items" with an X; at the top the tab row is visible, scrolled down only "Select items" remains; "Library" appears nowhere | Amy: "The heading changed from 'Library' to 'Select items'. That describes what I am doing, not where" | keep the section in the title while selecting, e.g. "Library — select items" | confirmed |
| s20 | the Library in selection mode ("Select items", "Files" tab) | none that names the section; "Select items" replaces the "Library" title and the highlighted tab names a filter ("Files") | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | no test of its own: entering selection mode replaces the section name with "Select items"; a filter tab ("Files") does not name the part of the app | Amy: "Same as s19: the place name 'Library' is gone and only the action is shown" | keep the section in the title while selecting, e.g. "Library — select items" | confirmed |
| s21 | the Library in selection mode ("1 selected", "All" tab) | none that names the section; "1 selected" replaces the "Library" title and the highlighted tab names a filter ("All") | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | no test of its own: entering selection mode replaces the section name with "1 selected"; a filter tab ("All") does not name the part of the app | Amy: "The heading is now a count. A count is not a place" | keep the section in the title while selecting, e.g. "Library — 1 selected" | confirmed |
| s35 | a chat conversation | none; the top bar holds a back arrow and two icon buttons; everything else is the conversation (the user's "@Create image" bubble, the... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no test of its own: the chat's own title exists only in the drawer's history list; nothing on the chat screen shows it | Amy: "There is no title. I can tell it is a conversation only from the reply field" | show the chat's title (the one listed in the side menu, e.g. "Create red apple image") in the top bar | confirmed |
| s36 | a chat conversation | none; the top bar holds a back arrow and two icon buttons; everything else is the conversation (the user's "@Create image" bubble, the... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | neither chat showed its name anywhere on screen in any scroll position; the top bar held only the menu, new-chat and ⋮ icons | Amy: "No title. I know it is a conversation from the message bubble and the reply field, not from anything that names it" | show the chat's title (the one listed in the side menu, e.g. "Create red apple image") in the top bar | confirmed |
| s37 | a chat conversation | none; the top bar holds a back arrow and two icon buttons; everything else is the conversation (the user's "@Create image" bubble, the... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no test of its own: the chat's own title exists only in the drawer's history list; nothing on the chat screen shows it | Amy: "Same as s36. The status sentence changed from 'Sketching it out' to 'Making the first draft' — those are figures of speech, and they do not tell me where I am either" | show the chat's title (the one listed in the side menu, e.g. "Create red apple image") in the top bar | confirmed |
| s38 | a chat conversation | none; the top bar holds a back arrow and two icon buttons; everything else is the conversation (the user's "@Create image" bubble, the... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no test of its own: the chat's own title exists only in the drawer's history list; nothing on the chat screen shows it | Amy: "Same as s36. No name for the conversation" | show the chat's title (the one listed in the side menu, e.g. "Create red apple image") in the top bar | confirmed |
| s39 | a chat conversation | none; the top bar holds a back arrow and two icon buttons; everything else is the conversation (the user's "@Create image" bubble, the... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no test of its own: the chat's own title exists only in the drawer's history list; nothing on the chat screen shows it | Amy: "Same as s36. No name for the conversation" | show the chat's title (the one listed in the side menu, e.g. "Create red apple image") in the top bar | confirmed |
| s40 | a chat conversation | none; the top bar holds a back arrow and two icon buttons; everything else is the conversation (the user's "@Create image" bubble, the... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no test of its own: the chat's own title exists only in the drawer's history list; nothing on the chat screen shows it | Amy: "Still no title. And now there is an advert in the middle of the conversation, which is clutter between me and my own content" | show the chat's title (the one listed in the side menu, e.g. "Create red apple image") in the top bar | confirmed |
| s41 | a chat conversation | none; the top bar holds a back arrow and two icon buttons; everything else is the conversation (the user's "@Create image" bubble, the... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no test of its own: the chat's own title exists only in the drawer's history list; nothing on the chat screen shows it | Amy: "Identical to s40: no name for the conversation" | show the chat's title (the one listed in the side menu, e.g. "Create red apple image") in the top bar | confirmed |
| s42 | a chat conversation | none; the top bar holds a back arrow and two icon buttons; everything else is the conversation (the user's "@Create image" bubble, the... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no test of its own: the chat's own title exists only in the drawer's history list; nothing on the chat screen shows it | Amy: "No title. The feedback message tells me what I just did, not where I am" | show the chat's title (the one listed in the side menu, e.g. "Create red apple image") in the top bar | confirmed |
| s43 | a chat conversation | none; the top bar holds a back arrow and two icon buttons; everything else is the conversation (the user's "@Create image" bubble, the... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no test of its own: the chat's own title exists only in the drawer's history list; nothing on the chat screen shows it | Amy: "No title for the conversation" | show the chat's title (the one listed in the side menu, e.g. "Create red apple image") in the top bar | confirmed |
| s44 | the side menu (opened from the "Schedule a task" screen) | none that names the section; the header is the app wordmark "ChatGPT" and no section entry is highlighted | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | no section entry (Images, Library, Projects, Scheduled, Plugins) was ever highlighted, whichever section the menu was opened from; the only highlight the menu ever showed was a grey fill on... | Amy: "Same as s9: 'ChatGPT' is the app name, and no entry is marked as current, even though the screen behind is the image section. The list below now shows 'Create image' twice and 'Schedule a task' twice, so I cannot tell..." | highlight the current section in the menu (it already highlights the current chat row) and replace the wordmark with a menu heading such as "Menu" | confirmed |
| s3 | the image-creation gallery opened from the home screen | "Trending" tab drawn with a filled grey pill beside "Templates", above a grid of image templates, with a "Create image" composer | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame | the grey pill moved to "Templates" and the grid changed to Poster / Interior design / Logo / Illustration; the highlight tracks the section | Amy: "The tabs tell me which list I am on, not which part of the app I am in. 'Trending' is a filter, not a place" | Amy: Add a title above the tabs that names the section, for example 'Images' | confirmed |
| s12 | the image gallery ("Images") opened from the side menu, scrolled slightly | "Trending" tab with a filled pill; a back arrow; the notice "Your generated images moved to Library" overlapping the top bar | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame, Yuki | at the very top the gallery shows a centred "Images" title in the top bar above the notice card; a short scroll (the state this capture holds) slides the notice card over it and the title... | Amy: "The notice is drawn on top of the status bar and the back arrow, so the text overlaps them and part of it is hidden. There is still no name for the section" | pin the "Images" title in the top bar rather than letting the notice card slide over it | confirmed |
| s13 | the image gallery ("Images") opened from the side menu, scrolled slightly | "Trending" tab with a filled pill; a back arrow; the notice "Your generated images moved to Library" overlapping the top bar | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame, Yuki | at the very top the gallery shows a centred "Images" title in the top bar above the notice card; a short scroll (the state this capture holds) slides the notice card over it and the title... | Amy: "Same problems: the notice overlaps the back arrow and the clock, and nothing names the section" | pin the "Images" title in the top bar rather than letting the notice card slide over it | confirmed |
| s27 | the project icon-and-colour picker over New Project | dimmed "New Project" title behind the untitled picker | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame | no test of its own: the title behind the modal picker stays legible; the picker returns to the form on OK | Amy: "The box has no title and no text except 'OK'. I know I am still in New Project because of the dimmed heading behind it, but what this box is for I have to guess from the icons" | give the picker its own title ("Icon and colour") | confirmed |
| s31 | the project icon-and-colour picker over New Project | dimmed "New Project" title behind the untitled picker | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame | no test of its own: the title behind the modal picker stays legible; the picker returns to the form on OK | Amy: "Same as s27: the box has no name of its own" | give the picker its own title ("Icon and colour") | confirmed |
| s34 | Schedule a task | "Schedule a task" title | Missing View Identifier | classified from persona | Medium | persona | Amy | the screen shows "Schedule a task" with "ChatGPT can take care of ongoing tasks so you don't have to."; the menu entry is worded "Scheduled", the title "Schedule a task" | Amy: "'Schedule a task' is an instruction, like a button label, not the name of a place. I cannot tell if this is a list of my scheduled tasks or a form for making one" | Amy: Use a noun as the heading, for example 'Scheduled tasks', and put it in the top bar | confirmed |
| s6 | the ChatGPT Go plan page | "ChatGPT Go" title | Missing View Identifier | classified from persona | Low | persona | Gopal | no test of its own: title present in the image; template carry from s5 (same structure d268e893, same title position; only the plan name differs, and... | Gopal: "'Go' is not a name I recognise; to me 'Go' is an instruction, like a button to press. Reading the heading, I would think I was being told to go somewhere" | Gopal: Name the plan in ordinary words, for instance 'Basic paid plan', and mark the chosen option with a tick or the word 'Selected' rather than a change of grey | confirmed |
| s11 | a template detail sheet over the image gallery | the dimmed "Trending" tab behind the sheet; the sheet title names the template | Missing View Identifier | classified from persona | Low | persona | Amy, Kwame | not tested on the device: the live Trending gallery no longer carries an "Underwater" card and photo templates now open a centred dialog rather than this... | Amy: "'See yourself underwater' is an invitation, not the name of a place. I understand what the template produces from the paragraph, but nothing says this is a template or where it came from" | keep the gallery name visible above the sheet (e.g. "Images · Trending") | provisional |

## 4. Attribution at a glance — transitions

| Transition | From → To | Action | Issue | Category from | Severity | Found by | Personas | Tester observed | Persona said | Recommendation | Confidence |
|---|---|---|---|---|---|---|---|---|---|---|---|
| t43 | s17 → s10 | you stayed on this screen and scrolled down | — | classified from persona | Low | persona | Amy, Gopal, Kwame | the downward swipe dismissed the viewer and returned to Library (a navigation, not a scroll in place); the drawing sheet s10 recorded as this edge's to-state never appeared | Amy: "The tabs are back, so I know which list I am on. But scrolling down should not make a drawing panel appear, and that panel has no name" | Amy: Give the section a fixed title above the tabs, and give the drawing panel its own title so I know it is a separate thing that opened | confirmed |

## 5. Exceptions

| Transition | Takeover excused | Way back | Persona lost anyway |
|---|---|---|---|
| none | — | — | — |

## 6. Disagreements

| Subject | Tester verdict | Persona | Persona verdict | Persona said | Direction |
|---|---|---|---|---|---|
| s3 | Sufficient View Identifier | Amy | navigate with difficulty | "The tabs tell me which list I am on, not which part of the app I am in. 'Trending' is a filter, not a place" | persona found an issue, tester did not |
| s3 | Sufficient View Identifier | Gopal | navigate with difficulty | "'Trending' and 'Templates' are not names of a place; they are sorting words, and 'Trending' in particular is a fashionable term I would have to learn. Nothing at the top says 'Pictures' or 'Make a picture'" | persona found an issue, tester did not |
| s3 | Sufficient View Identifier | Kwame | navigate with difficulty | "The shaded 'Trending' tab does tell me which list I am on, and I can see it is chosen. But 'Trending' names a list, not a place" | persona found an issue, tester did not |
| s6 | Sufficient View Identifier | Gopal | navigate with difficulty | "'Go' is not a name I recognise; to me 'Go' is an instruction, like a button to press. Reading the heading, I would think I was being told to go somewhere" | persona found an issue, tester did not |
| s10 | Sufficient View Identifier | Amy | navigate with difficulty | "The panel has no title at all. I am guessing it is for drawing only because the icons look like drawing tools" | persona found an issue, tester did not |
| s10 | Sufficient View Identifier | Gopal | cannot handle it at all | "This panel has no heading and no words of any kind. The only marked box is the 'Trending' and 'Templates' row behind it, which belongs to the page underneath, not to the thing I am looking at" | persona found an issue, tester did not |
| s10 | Sufficient View Identifier | Kwame | navigate with difficulty | "The panel that fills most of the screen has no title at all; every control on it is a picture without a word. I have to recognise the pencil and the eraser to guess this is for drawing, and recognising pictures is..." | persona found an issue, tester did not |
| s10 | Sufficient View Identifier | Yuki | navigate with difficulty | "The panel that takes up most of the screen has no name at all. I'm guessing 'drawing' from the pencil and the colours" | persona found an issue, tester did not |
| s11 | Sufficient View Identifier | Amy | navigate with difficulty | "'See yourself underwater' is an invitation, not the name of a place. I understand what the template produces from the paragraph, but nothing says this is a template or where it came from" | persona found an issue, tester did not |
| s11 | Sufficient View Identifier | Kwame | navigate with difficulty | "The heading is clear and matches the buttons. But more than half of the screen is a large close-up photograph of a face, which takes my attention and tells me nothing I can use" | persona found an issue, tester did not |
| s12 | Sufficient View Identifier | Amy | navigate with difficulty | "The notice is drawn on top of the status bar and the back arrow, so the text overlaps them and part of it is hidden. There is still no name for the section" | persona found an issue, tester did not |
| s12 | Sufficient View Identifier | Gopal | navigate with difficulty | "Once again there is no name for the page, only 'Trending' and 'Templates'. Worse, the faint message at the top is printed on top of the back arrow and the clock, so the one place a heading ought to be is a jumble of..." | persona found an issue, tester did not |
| s12 | Sufficient View Identifier | Kwame | navigate with difficulty | "The notice is printed on top of the back arrow and the clock, so the one place a title could be is covered with overlapping text I have to untangle. The notice is about a different place, the Library, which makes me..." | persona found an issue, tester did not |
| s12 | Sufficient View Identifier | Yuki | navigate with difficulty | "That message is jammed on top of the back button and the status bar, so the top of the screen is a jumble of overlapping text. My attention went straight to trying to read it and I lost the rest" | persona found an issue, tester did not |
| s13 | Sufficient View Identifier | Amy | navigate with difficulty | "Same problems: the notice overlaps the back arrow and the clock, and nothing names the section" | persona found an issue, tester did not |
| s13 | Sufficient View Identifier | Gopal | navigate with difficulty | "The same as before: no page name, only the two sorting words, and the faint message sitting over the back arrow at the top. The blue 'Create image' at the bottom is the best clue, and it is at the wrong end of the screen" | persona found an issue, tester did not |
| s13 | Sufficient View Identifier | Kwame | navigate with difficulty | "Same reasons: the top of the screen is a jumble of the notice over the back arrow, and no title says which part of the app this is. The only thing that changed from the previous screen is the text in the box, from..." | persona found an issue, tester did not |
| s13 | Sufficient View Identifier | Yuki | navigate with difficulty | "Same problem — the overlapping message at the top grabs me and it's hard to read, and it covers the back arrow. I can get there from the bottom box, but the top of the screen is messy" | persona found an issue, tester did not |
| s27 | Sufficient View Identifier | Amy | navigate with difficulty | "The box has no title and no text except 'OK'. I know I am still in New Project because of the dimmed heading behind it, but what this box is for I have to guess from the icons" | persona found an issue, tester did not |
| s27 | Sufficient View Identifier | Gopal | navigate with difficulty | "The box that is in front of me has no heading at all — just thirty-odd symbols and some colours. The only name I can see belongs to the page behind it, and it is greyed out" | persona found an issue, tester did not |
| s27 | Sufficient View Identifier | Kwame | navigate with difficulty | "The box has no heading and no words apart from 'OK'. It is thirty small pictures with no labels, and I cannot read pictures reliably; a grid like this overloads me very quickly" | persona found an issue, tester did not |
| s31 | Sufficient View Identifier | Amy | navigate with difficulty | "Same as s27: the box has no name of its own" | persona found an issue, tester did not |
| s31 | Sufficient View Identifier | Gopal | navigate with difficulty | "As before, the box has no heading; the only name belongs to the page behind. A grid of unlabelled symbols with no title is not something I could pick up again after an interruption" | persona found an issue, tester did not |
| s31 | Sufficient View Identifier | Kwame | navigate with difficulty | "Still no heading on the box and still thirty unlabelled pictures. The chosen symbol is only slightly darker than the rest, which I had to hunt for" | persona found an issue, tester did not |
| s34 | Sufficient View Identifier | Amy | navigate with difficulty | "'Schedule a task' is an instruction, like a button label, not the name of a place. I cannot tell if this is a list of my scheduled tasks or a form for making one" | persona found an issue, tester did not |

## 7. Withdrawn after testing

| Subject | Who withdrew | From | To | What the test showed |
|---|---|---|---|---|
| s10 | tester | Missing View Identifier | Sufficient View Identifier | the drawing sheet opened over the lower two-thirds; "Trending" (filled pill) and "Templates" stayed fully legible and undimmed above it in every gesture; each swipe drew... |
| t32 | tester | Disappearing View Identifier | Identifier Persists | every swipe drew a stroke on the canvas; nothing scrolled; the user stayed on the drawing sheet and "Trending" (filled pill) / "Templates" stayed legible and undimmed... |
| t32 | Amy | cannot handle it at all | no problem | When I swiped up on the drawing panel, I stayed on the same panel |
| t32 | Gopal | cannot handle it at all | no problem | When I swiped on the drawing panel it did not take me anywhere — it simply drew a line and everything stayed put |
| t32 | Kwame | cannot handle it at all | no problem | When I swiped up on the drawing panel myself, I stayed on the same panel and it only drew a line |
| t32 | Yuki | cannot handle it at all | no problem | When I swiped up on the drawing panel it just drew a line and I stayed exactly where I was |
| t43 | Yuki | navigate with difficulty | no problem | Same swipe, same panel, nothing changed under me |

## 8. Detection false positives

| Screen | Region | What it said | Why it names no place | Persona said the same |
|---|---|---|---|---|
| s9 | header | "ChatGPT" | the app's own wordmark; names the app, not the place | Amy, Gopal, Kwame, Yuki |
| s11 | header | "See yourself underwater" | unconventional (bottom band) — the name of one template, i.e. a piece of content; dismissed as a place identifier | Amy |
| s14 | header | "Underwater" | unconventional (middle band) — the name of the chosen template; content, dismissed | — |
| s19 | header | "Select items" | names a selection mode/count, not a place; the "Library" title it replaced is gone | Amy, Gopal, Kwame, Yuki |
| s19 | navigation | "All / Images / Files (Images selected)" | visible pill on a filter tab; names a content type, not the section | — |
| s20 | header | "Select items" | names a selection mode/count, not a place; the "Library" title it replaced is gone | Amy, Gopal, Kwame |
| s20 | navigation | "All / Images / Files (Files selected)" | visible pill on a filter tab; names a content type, not the section | — |
| s21 | header | "1 selected" | names a selection mode/count, not a place; the "Library" title it replaced is gone | Amy, Gopal, Kwame, Yuki |
| s21 | navigation | "All / Images / Files (All selected)" | visible pill on a filter tab; names a content type, not the section | — |
| s22 | header | "1 selected" | names a selection mode/count, not a place; the "Library" title it replaced is gone | Yuki |
| s22 | navigation | "All / Images / Files (Files selected)" | visible pill on a filter tab; names a content type, not the section | — |
| s44 | header | "ChatGPT" | the app's own wordmark; names the app, not the place | Amy, Gopal, Kwame, Yuki |

## 9. Summary

| Found by | Screens | Transitions |
|---|---|---|
| both | 18 | 0 |
| tester | 0 | 0 |
| persona | 9 | 1 |
| none | 17 | 1 |
| not evaluated / N/A | 0 | 102 |

| Issue | Count |
|---|---|
| Missing View Identifier | 27 |
| Disappearing View Identifier | 0 |
| Classification missing | 4 |

| Severity | Issues |
|---|---|
| Critical | 2 |
| High | 17 |
| Medium | 6 |
| Low | 3 |

| Persona | Issues held |
|---|---|
| Amy | 26 |
| Gopal | 26 |
| Kwame | 26 |
| Yuki | 16 |

| Count | Value |
|---|---|
| Exceptions upheld | 0 |
| Disagreements | 9 |
| Provisional | 3 |
| Unreachable | 0 |
| Withdrawn after testing | 7 |
| Detection false positives | 12 |
| Out-of-scope observations | 3 |
