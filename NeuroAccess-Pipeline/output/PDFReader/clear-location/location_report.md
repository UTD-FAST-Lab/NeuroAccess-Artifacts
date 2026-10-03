# Location Report — PDFReader

**Date:** 2026-09-30 · **Screens evaluated:** 36 of 37 in-app · **Scroll transitions evaluated:** 0 of 93 transitions (this phase judges scrolls only)
**Screen issues:** 27 · **Transition issues:** 0 · **By severity:** Critical 7 · High 3 · Medium 17 · Low 0
**Personas:** All four ran — Amy, Gopal, Kwame, Yuki.

## 1. Capture coverage

| Gap | Subjects | What it prevented |
|---|---|---|
| States with no screenshot | none | nothing |
| Transitions with no recoverable action | t12, t15, t25, t37, t39, t42, t51, t53, t61, t63, t71, t73, t80, t82, t88, t90 | none is evaluated in this phase, so no verdict was lost; the tap cannot be named |
| Self-loops | none | nothing |
| Excluded by the tester — no picture | none | nothing |
| Excluded by the tester — system surface | s3 | a third-party test ad was not judged and not shown to the personas |
| Misclassified as in-app | s3 | the ad network's own screen sat in the in-app set; excluded before judging |
| Capture diverges from live app | none | nothing |
| Active state declared anywhere | yes | nothing |

## 2. Out of scope by construction

| Subject | Ids | Reason it carries no verdict |
|---|---|---|
| Out-of-app states | x1, x2, x3, x4, x5, x6 | the launcher, the Play Store, system settings and the app chooser; leaving the app is not losing your place in it |
| Exit transitions | b1, b2, b3, b4, b5, b6, b7, b8, b9, b10, b11, b12, b13 | they hand the user to another app; listed, not judged |
| Return transitions | b14, b15, b16, b17, b18, b19, b20, b21, b22, b23, b24, b25, b26, b27 | each lands on a judged screen: b14 on s1, b15 on s6, b16 on s12, b17 on s17, b18 on s21, b19 on s25, b20 on s30, b21 on s34, b22 on s18, b23 on s4, b24 on s10, b25 on s15, b26 on s4, b27 on s15 |
| Touch and Back transitions | 93 ids in the JSON | a touch or Back lands on a different view, judged as a screen; this phase evaluates scrolls only, and the capture holds none |
| Harness transitions | b14, b22, b26, b27 | the crawler relaunching the app, not something a user did |

## 3. Attribution at a glance — screens

| Screen | What it is | Identifier on screen | Issue | Category from | Severity | Found by | Personas | Tester observed | Persona said | Recommendation | Confidence |
|---|---|---|---|---|---|---|---|---|---|---|---|
| s5 | the Premium plan offer (before the close X appears) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Critical | persona | Amy, Kwame | the heading names the offer; an X appeared after about 3 s and Back returned to Home | "The heading is a sales sentence, not the name of a place." | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s11 | the Premium plan offer (before the close X appears) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Critical | persona | Amy, Kwame | the heading names the offer; an X appeared after about 3 s and Back returned to Home | "The heading is a sales sentence, not the name of a place." | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s16 | the Premium plan offer (before the close X appears) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Critical | persona | Amy, Kwame | the heading names the offer; an X appeared after about 3 s and Back returned to Home | "The heading is a sales sentence, not the name of a place." | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s20 | the Premium plan offer (before the close X appears) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Critical | persona | Amy, Kwame | the heading names the offer; an X appeared after about 3 s and Back returned to Home | "The heading is a sales sentence, not the name of a place." | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s24 | the Premium plan offer (before the close X appears) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Critical | persona | Amy, Kwame | the heading names the offer; an X appeared after about 3 s and Back returned to Home | "The heading is a sales sentence, not the name of a place." | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s29 | the Premium plan offer (before the close X appears) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Critical | persona | Amy, Kwame | the heading names the offer; an X appeared after about 3 s and Back returned to Home | "The heading is a sales sentence, not the name of a place." | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s33 | the Premium plan offer (before the close X appears) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Critical | persona | Amy, Kwame | the heading names the offer; an X appeared after about 3 s and Back returned to Home | "The heading is a sales sentence, not the name of a place." | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s1 | the launch screen | only the app's name | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | only the app's name and an ads notice appeared at any moment of the live launch screen | "That tells me which app I opened, not where I am in it." | label the progress indicator, e.g. "Starting PDF Reader..." or "Loading" -- this resolves the tester's finding and the personas' alike | confirmed |
| s2 | the launch screen | only the app's name | Missing View Identifier | tester verdict | High | both | Gopal, Kwame | the app's name is the only text and the progress bar has no label | "Nothing says 'starting' or 'please wait'." | label the progress indicator, e.g. "Starting PDF Reader..." or "Loading" -- this resolves the tester's finding and the personas' alike | confirmed |
| s27 | the set-as-default sheet over Home | a slogan, with the app's name behind | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | no visible heading named the sheet and the tab bar was covered | "is a slogan, not a name for this panel" | head the sheet "Set as default reader" instead of "The fastest way to read PDF files" -- this resolves the tester's finding and all four personas' alike | confirmed |
| s6 | the Premium plan offer (close X shown) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Medium | persona | Amy, Kwame | the X returned to Home with the tab highlight as before | "the heading is a slogan, not a name for this place" | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s8 | the rate-this-app dialog over Settings | "Settings" behind the dialog | Missing View Identifier | classified from persona | Medium | persona | Gopal, Kwame | "Settings" stayed legible behind the dialog and Back returned to Settings | "They do not say what the box is for." | head the dialog with its task, such as "Rate this app", with the thank-you beneath it | confirmed |
| s9 | the Add widget sheet over Settings | "Add widget" | Missing View Identifier | classified from persona | Medium | persona | Gopal | the heading matched the tapped Settings row and tapping outside returned to Settings | "the heading names the place in a word that means nothing to me" | name the sheet in ordinary words, such as "Add a shortcut to your home screen" | confirmed |
| s10 | Home, the file list (HWP filter) | "Home" tab highlight; header is the app's name | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame | the Home tab highlight moved with the user and stayed on screen while scrolling | "the biggest words and the selected pill say two different things" | name the chosen file type in words in the title or a line such as "Showing HWP files", rather than leaving "PDF Reader" and a coloured pill to disagree | confirmed |
| s12 | the Premium plan offer (close X shown) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Medium | persona | Amy, Kwame | the X returned to Home with the tab highlight as before | "the heading is a slogan, not a name for this place" | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s14 | the Add widget sheet over Settings | "Add widget" | Missing View Identifier | classified from persona | Medium | persona | Gopal | "Add widget" stayed put while the carousel was swiped | "the heading names the place in a word that means nothing to me" | name the sheet in ordinary words, such as "Add a shortcut to your home screen" | confirmed |
| s15 | Home, the file list (Word filter) | "Home" tab highlight; header is the app's name | Missing View Identifier | classified from persona | Medium | persona | Amy, Kwame | the Home tab highlight moved with the user and stayed on screen while scrolling | "the biggest words and the selected pill say two different things" | name the chosen file type in words in the title or a line such as "Showing HWP files", rather than leaving "PDF Reader" and a coloured pill to disagree | confirmed |
| s17 | the Premium plan offer (close X shown) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Medium | persona | Amy, Kwame | the X returned to Home with the tab highlight as before | "the heading is a slogan, not a name for this place" | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s19 | Home, the file list (Excel filter) | "Home" tab highlight; header is the app's name | Missing View Identifier | classified from persona | Medium | persona | Amy, Kwame | the Home tab highlight moved with the user and stayed on screen while scrolling | "the biggest words and the selected pill say two different things" | name the chosen file type in words in the title or a line such as "Showing HWP files", rather than leaving "PDF Reader" and a coloured pill to disagree | confirmed |
| s21 | the Premium plan offer (close X shown) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Medium | persona | Amy, Kwame | the X returned to Home with the tab highlight as before | "the heading is a slogan, not a name for this place" | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s23 | Home, the file list (PPT filter) | "Home" tab highlight; header is the app's name | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame | the Home tab highlight moved with the user and stayed on screen while scrolling | "the biggest words and the selected pill say two different things" | name the chosen file type in words in the title or a line such as "Showing HWP files", rather than leaving "PDF Reader" and a coloured pill to disagree | confirmed |
| s25 | the Premium plan offer (close X shown) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Medium | persona | Amy, Kwame | the X returned to Home with the tab highlight as before | "the heading is a slogan, not a name for this place" | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s30 | the Premium plan offer (close X shown) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Medium | persona | Amy, Kwame | the X returned to Home with the tab highlight as before | "the heading is a slogan, not a name for this place" | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s32 | Home, the file list (HWP filter) | "Home" tab highlight; header is the app's name | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame | the Home tab highlight moved with the user and stayed on screen while scrolling | "the biggest words and the selected pill say two different things" | name the chosen file type in words in the title or a line such as "Showing HWP files", rather than leaving "PDF Reader" and a coloured pill to disagree | confirmed |
| s34 | the Premium plan offer (close X shown) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Medium | persona | Amy, Kwame | the X returned to Home with the tab highlight as before | "the heading is a slogan, not a name for this place" | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |
| s36 | Home, the file list (Word filter) | "Home" tab highlight; header is the app's name | Missing View Identifier | classified from persona | Medium | persona | Amy, Kwame | the Home tab highlight moved with the user and stayed on screen while scrolling | "the biggest words and the selected pill say two different things" | name the chosen file type in words in the title or a line such as "Showing HWP files", rather than leaving "PDF Reader" and a coloured pill to disagree | confirmed |
| s37 | the Premium plan offer (before the close X appears) | "Try the Premium plan completely free" | Missing View Identifier | classified from persona | Medium | persona | Amy, Kwame | the X returned to Home with the tab highlight as before | "the heading is a slogan, not a name for this place" | give the offer page a plain title naming it, such as "Premium plan", instead of the sales line as its only heading | confirmed |

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
| s5 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading is a sales sentence, not the name of a place." | persona found an issue, tester did not |
| s5 | Sufficient View Identifier | Kwame | cannot handle it at all | "it tells me what is being offered but not where I am" | persona found an issue, tester did not |
| s11 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading is a sales sentence, not the name of a place." | persona found an issue, tester did not |
| s11 | Sufficient View Identifier | Kwame | cannot handle it at all | "it tells me what is being offered but not where I am" | persona found an issue, tester did not |
| s16 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading is a sales sentence, not the name of a place." | persona found an issue, tester did not |
| s16 | Sufficient View Identifier | Kwame | cannot handle it at all | "it tells me what is being offered but not where I am" | persona found an issue, tester did not |
| s20 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading is a sales sentence, not the name of a place." | persona found an issue, tester did not |
| s20 | Sufficient View Identifier | Kwame | cannot handle it at all | "it tells me what is being offered but not where I am" | persona found an issue, tester did not |
| s24 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading is a sales sentence, not the name of a place." | persona found an issue, tester did not |
| s24 | Sufficient View Identifier | Kwame | cannot handle it at all | "it tells me what is being offered but not where I am" | persona found an issue, tester did not |
| s29 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading is a sales sentence, not the name of a place." | persona found an issue, tester did not |
| s29 | Sufficient View Identifier | Kwame | cannot handle it at all | "it tells me what is being offered but not where I am" | persona found an issue, tester did not |
| s33 | Sufficient View Identifier | Amy | navigate with difficulty | "The heading is a sales sentence, not the name of a place." | persona found an issue, tester did not |
| s33 | Sufficient View Identifier | Kwame | cannot handle it at all | "it tells me what is being offered but not where I am" | persona found an issue, tester did not |
| s6 | Sufficient View Identifier | Amy | navigate with difficulty | "the heading is a slogan, not a name for this place" | persona found an issue, tester did not |
| s6 | Sufficient View Identifier | Kwame | navigate with difficulty | "I know what is being offered, not where I am in the app" | persona found an issue, tester did not |
| s8 | Sufficient View Identifier | Gopal | navigate with difficulty | "They do not say what the box is for." | persona found an issue, tester did not |
| s8 | Sufficient View Identifier | Kwame | navigate with difficulty | "a thank-you message, not a name for where I am" | persona found an issue, tester did not |
| s9 | Sufficient View Identifier | Gopal | navigate with difficulty | "the heading names the place in a word that means nothing to me" | persona found an issue, tester did not |
| s10 | Sufficient View Identifier | Amy | navigate with difficulty | "the biggest words and the selected pill say two different things" | persona found an issue, tester did not |
| s10 | Sufficient View Identifier | Gopal | navigate with difficulty | "I do not know what those letters stand for" | persona found an issue, tester did not |
| s10 | Sufficient View Identifier | Kwame | navigate with difficulty | "Those two statements pull against each other" | persona found an issue, tester did not |
| s12 | Sufficient View Identifier | Amy | navigate with difficulty | "the heading is a slogan, not a name for this place" | persona found an issue, tester did not |
| s12 | Sufficient View Identifier | Kwame | navigate with difficulty | "I know what is being offered, not where I am in the app" | persona found an issue, tester did not |
| s14 | Sufficient View Identifier | Gopal | navigate with difficulty | "the heading names the place in a word that means nothing to me" | persona found an issue, tester did not |
| s15 | Sufficient View Identifier | Amy | navigate with difficulty | "the biggest words and the selected pill say two different things" | persona found an issue, tester did not |
| s15 | Sufficient View Identifier | Kwame | navigate with difficulty | "Those two statements pull against each other" | persona found an issue, tester did not |
| s17 | Sufficient View Identifier | Amy | navigate with difficulty | "the heading is a slogan, not a name for this place" | persona found an issue, tester did not |
| s17 | Sufficient View Identifier | Kwame | navigate with difficulty | "I know what is being offered, not where I am in the app" | persona found an issue, tester did not |
| s19 | Sufficient View Identifier | Amy | navigate with difficulty | "the biggest words and the selected pill say two different things" | persona found an issue, tester did not |
| s19 | Sufficient View Identifier | Kwame | navigate with difficulty | "Those two statements pull against each other" | persona found an issue, tester did not |
| s21 | Sufficient View Identifier | Amy | navigate with difficulty | "the heading is a slogan, not a name for this place" | persona found an issue, tester did not |
| s21 | Sufficient View Identifier | Kwame | navigate with difficulty | "I know what is being offered, not where I am in the app" | persona found an issue, tester did not |
| s23 | Sufficient View Identifier | Amy | navigate with difficulty | "the biggest words and the selected pill say two different things" | persona found an issue, tester did not |
| s23 | Sufficient View Identifier | Gopal | navigate with difficulty | "Those are initials, and I have to stop and try to work out what they stand for." | persona found an issue, tester did not |
| s23 | Sufficient View Identifier | Kwame | navigate with difficulty | "Those two statements pull against each other" | persona found an issue, tester did not |
| s25 | Sufficient View Identifier | Amy | navigate with difficulty | "the heading is a slogan, not a name for this place" | persona found an issue, tester did not |
| s25 | Sufficient View Identifier | Kwame | navigate with difficulty | "I know what is being offered, not where I am in the app" | persona found an issue, tester did not |
| s30 | Sufficient View Identifier | Amy | navigate with difficulty | "the heading is a slogan, not a name for this place" | persona found an issue, tester did not |
| s30 | Sufficient View Identifier | Kwame | navigate with difficulty | "I know what is being offered, not where I am in the app" | persona found an issue, tester did not |
| s32 | Sufficient View Identifier | Amy | navigate with difficulty | "the biggest words and the selected pill say two different things" | persona found an issue, tester did not |
| s32 | Sufficient View Identifier | Gopal | navigate with difficulty | "I do not know what those letters stand for" | persona found an issue, tester did not |
| s32 | Sufficient View Identifier | Kwame | navigate with difficulty | "Those two statements pull against each other" | persona found an issue, tester did not |
| s34 | Sufficient View Identifier | Amy | navigate with difficulty | "the heading is a slogan, not a name for this place" | persona found an issue, tester did not |
| s34 | Sufficient View Identifier | Kwame | navigate with difficulty | "I know what is being offered, not where I am in the app" | persona found an issue, tester did not |
| s36 | Sufficient View Identifier | Amy | navigate with difficulty | "the biggest words and the selected pill say two different things" | persona found an issue, tester did not |
| s36 | Sufficient View Identifier | Kwame | navigate with difficulty | "Those two statements pull against each other" | persona found an issue, tester did not |
| s37 | Sufficient View Identifier | Amy | navigate with difficulty | "the heading is a slogan, not a name for this place" | persona found an issue, tester did not |
| s37 | Sufficient View Identifier | Kwame | navigate with difficulty | "I know what is being offered, not where I am in the app" | persona found an issue, tester did not |

## 7. Withdrawn after testing

| Subject | Who withdrew | From | To | What the test showed |
|---|---|---|---|---|
| s5 | Yuki | navigate with difficulty | reversed | the close X was already there on the phone and returned her to where she had been |
| s11 | Yuki | navigate with difficulty | reversed | the close X was already there on the phone and returned her to where she had been |
| s16 | Yuki | navigate with difficulty | reversed | the close X was already there on the phone and returned her to where she had been |
| s20 | Yuki | navigate with difficulty | reversed | the close X was already there on the phone and returned her to where she had been |
| s24 | Yuki | navigate with difficulty | reversed | the close X was already there on the phone and returned her to where she had been |
| s29 | Yuki | navigate with difficulty | reversed | the close X was already there on the phone and returned her to where she had been |
| s33 | Yuki | navigate with difficulty | reversed | the close X was already there on the phone and returned her to where she had been |

## 8. Detection false positives

| Screen | Region | What it said | Why it names no place | Persona said the same |
|---|---|---|---|---|
| s1 | header | "PDF Reader, PDF Viewer" | names the app, not any part of it | yes -- Amy, Gopal, Kwame said the app's name does not say where they are |
| s2 | header | "PDF Reader, PDF Viewer" | names the app, not any part of it | yes -- Gopal, Kwame said the app's name does not say where they are |
| s4 | navigation | the PDF / HWP / Word / Excel / PPT pill row | a file-type filter on the list; its selection says which files are listed, not which section you are in | no -- Amy and Kwame read the selected pill as the section they were in; Gopal could not read its initials as a name |
| s8 | header | "Thank you for using PDF Reader, PDF Viewer! We would be very grateful if you could rate us." | a thank-you addressed by the app's name; names content, not a place | yes -- Gopal and Kwame said the thank-you does not say what the box is |
| s10 | navigation | the PDF / HWP / Word / Excel / PPT pill row | a file-type filter on the list; its selection says which files are listed, not which section you are in | no -- Amy and Kwame read the selected pill as the section they were in; Gopal could not read its initials as a name |
| s15 | navigation | the PDF / HWP / Word / Excel / PPT pill row | a file-type filter on the list; its selection says which files are listed, not which section you are in | no -- Amy and Kwame read the selected pill as the section they were in; Gopal could not read its initials as a name |
| s19 | navigation | the PDF / HWP / Word / Excel / PPT pill row | a file-type filter on the list; its selection says which files are listed, not which section you are in | no -- Amy and Kwame read the selected pill as the section they were in; Gopal could not read its initials as a name |
| s23 | navigation | the PDF / HWP / Word / Excel / PPT pill row | a file-type filter on the list; its selection says which files are listed, not which section you are in | no -- Amy and Kwame read the selected pill as the section they were in; Gopal could not read its initials as a name |
| s27 | header | "The fastest way to read PDF files" | a claim about the app, not the name of a place | yes -- all four said it is a slogan or boast, not a name |
| s27 | navigation | the PDF / HWP / Word / Excel / PPT pill row | a file-type filter on the list; its selection says which files are listed, not which section you are in | partly -- Kwame said the row no longer showed which one was chosen; none used it as a place |
| s28 | navigation | the PDF / HWP / Word / Excel / PPT pill row | a file-type filter on the list; its selection says which files are listed, not which section you are in | no -- Amy and Kwame read the selected pill as the section they were in; Gopal could not read its initials as a name |
| s32 | navigation | the PDF / HWP / Word / Excel / PPT pill row | a file-type filter on the list; its selection says which files are listed, not which section you are in | no -- Amy and Kwame read the selected pill as the section they were in; Gopal could not read its initials as a name |
| s36 | navigation | the PDF / HWP / Word / Excel / PPT pill row | a file-type filter on the list; its selection says which files are listed, not which section you are in | no -- Amy and Kwame read the selected pill as the section they were in; Gopal could not read its initials as a name |

## 9. Summary

| Found by | Screens | Transitions |
|---|---|---|
| both | 3 | 0 |
| tester | 0 | 0 |
| persona | 24 | 0 |
| none | 9 | 0 |
| not evaluated / N/A | 1 | 93 |

| Issue | Count |
|---|---|
| Missing View Identifier | 27 |
| Disappearing View Identifier | 0 |
| Classification missing | 0 |

| Severity | Issues |
|---|---|
| Critical | 7 |
| High | 3 |
| Medium | 17 |
| Low | 0 |

| Persona | Issues held |
|---|---|
| Amy | 23 |
| Gopal | 9 |
| Kwame | 25 |
| Yuki | 1 |

| Count | Value |
|---|---|
| Exceptions upheld | 0 |
| Disagreements | 24 |
| Provisional | 0 |
| Unreachable | 0 |
| Withdrawn after testing | 7 |
| Detection false positives | 13 |
| Out-of-scope observations | 16 |
