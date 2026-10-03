# Location Report — Duolingo

**Date:** 2026-09-30 · **Screens evaluated:** 89 of 90 in-app · **Scroll transitions evaluated:** 1 of 151 transitions (this phase judges scrolls only)
**Screen issues:** 51 · **Transition issues:** 0 · **By severity:** Critical 6 · High 18 · Medium 14 · Low 13
**Personas:** All four ran — Amy, Gopal, Kwame, Yuki.

## 1. Capture coverage

| Gap | Subjects | What it prevented |
|---|---|---|
| States with no screenshot | none | nothing |
| Transitions with no recoverable action | t29, t32, t35, t36, t37, t42, t43, t47, t64, t66, t85, t86, t88, t93, t102, t140, t149 | the tapped control cannot be named for these touches; none is a judged subject in this phase |
| Self-loops | none | nothing |
| Excluded by the tester — no picture | none | nothing |
| Excluded by the tester — system surface | s67 | no verdict and not shown to a persona; the picture is the device launcher with the app's launch animation, not a surface of the app |
| Misclassified as in-app | s67 | the package partition put a launcher frame in the in-app set; excluded from the audit |
| Capture diverges from live app | s1, s14, s17, s19, s35, s39, s40, s41, s70, s71, s72, s80, t18 | the live app no longer shows what the capture shows (splash art, Super trial frames, ad creative, quest reward, friend suggestions, the Streak scroll); issues on these subjects are provisional |
| Active state declared anywhere | yes | declared only on worded top tab rows; the bottom tab bar is never declared, so its active state was read off the pixels |

## 2. Out of scope by construction

| Subject | Ids | Reason it carries no verdict |
|---|---|---|
| Out-of-app states | 23 ids in the JSON | another app's surface (launcher, Play Store billing, permission prompt, browser); leaving the app is not losing your place in it; 20 further edges run between these states and are recorded only |
| Exit transitions | b1, b2, b3, b4, b5, b6, b7 | the move hands the user to another app; listed, not judged |
| Return transitions | b8, b9, b10, b11, b12, b17, b34, b35 | Back, a tap or a relaunch into the app; each lands on a screen judged on its own: b8 on s1; b9 on s15; b10 on s83; b11 on s20; b12 on s35; b17 on s67 (excluded, not judged); b34 on s40; b35 on s40 |
| Touch and Back transitions | 150 ids in the JSON | a move to a different view is judged as a screen, not as a move; the one scroll edge is the only evaluated transition |
| Harness transitions | b8, b16, b20, b23, b29, b34, b35 | the crawler launching the app, not a user action; b8 lands on s1, b34 lands on s40, b35 lands on s40, each judged as a screen; b16, b20, b23, b29 ran while another app stayed in front and are recorded only |

## 3. Attribution at a glance — screens

| Screen | What it is | Identifier on screen | Issue | Category from | Severity | Found by | Personas | Tester observed | Persona said | Recommendation | Confidence |
|---|---|---|---|---|---|---|---|---|---|---|---|
| s17 | the Super subscription offer | none that names a place: a 'SUPER' wordmark top-right, an X top-left, and a marketing headline | Missing View Identifier | tester verdict | Critical | both | Amy, Gopal, Kwame, Yuki | not tested on the device: reaching this frame requires tapping START MY FREE WEEK (a free-trial start), which the run forbids... | Amy: "The only boxed thing is a brand logo, there is no text, and the picture is an abstract character, so nothing tells me what this screen is" | give the page a plain title such as 'Super subscription' next to the X | provisional |
| s39 | a full-screen video advert | none: an advertiser's video with a countdown ring or an X and an advertiser strip | Missing View Identifier | tester verdict | Critical | both | Amy, Gopal, Kwame, Yuki | a different advertiser's video ('Disney+ Hulu', live app diverges from capture) with only a countdown ring and a sound icon — no close control for ~25 s... | Amy: "A video with sound on that I did not start, no text naming where I am in the app, and a loading circle where the close control would be..." | show a thin app bar ('Free chest — ad') with the remaining time over the video | provisional |
| s40 | a full-screen video advert | none: an advertiser's video with a countdown ring or an X and an advertiser strip | Missing View Identifier | tester verdict | Critical | both | Amy, Gopal, Kwame, Yuki | a different advertiser's video ('Disney+ Hulu', live app diverges from capture) with only a countdown ring and a sound icon — no close control for ~25 s... | Amy: "Nothing names where I am, the video is moving, the speaker icon shows sound is on..." | show a thin app bar ('Free chest — ad') with the remaining time over the video | provisional |
| s41 | a full-screen video advert | none: an advertiser's video with a countdown ring or an X and an advertiser strip | Missing View Identifier | tester verdict | Critical | both | Amy, Gopal, Kwame, Yuki | a different advertiser's video ('Disney+ Hulu', live app diverges from capture) with only a countdown ring and a sound icon — no close control for ~25 s... | Gopal: "Nothing on the screen names the app or the place I was; if I looked away I would have no idea how I got here or how to get back" | show a thin app bar ('Free chest — ad') with the remaining time over the video | provisional |
| s80 | the Super subscription offer | none that names a place: a 'SUPER' wordmark top-right, an X top-left, and a marketing headline | Missing View Identifier | tester verdict | Critical | both | Amy, Gopal, Kwame, Yuki | not tested on the device: reaching this frame requires tapping START MY FREE WEEK (a free-trial start), which the run forbids... | Amy: "The only boxed thing is a brand logo, which names a product, not a place; the picture is abstract and there is no text saying what this screen is" | give the page a plain title such as 'Super subscription' next to the X | provisional |
| s88 | a full-screen video advert | none: an advertiser's video with a countdown ring or an X and an advertiser strip | Missing View Identifier | tester verdict | Critical | both | Amy, Gopal, Kwame, Yuki | identifier read: none: an advertiser's video with a countdown ring or an X and an advertiser strip | Amy: "A video with sound that I did not start, and nothing names where I am in the app" | show a thin app bar ('Free chest — ad') with the remaining time over the video | confirmed |
| s1 | the launch splash | none: the owl logo on green (live: the 'duolingo' wordmark on green) | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame, Yuki | green splash with the 'duolingo' wordmark (the capture showed the owl instead — live app diverges), then the Learn path | Amy: "There is no text, so I have to assume from the empty screen and the logo that the app is starting; nothing says loading" | none needed beyond keeping it brief; if it lingers, show 'Loading your course…' | provisional |
| s12 | the Super subscription offer | none that names a place: a 'SUPER' wordmark top-right, an X top-left, and a marketing headline | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | the page showed 'Power up your learning with unlimited energy on Super!' under the SUPER wordmark; nothing changed while waiting or on tapping the illustration... | Amy: "The boxed region is a logo, not a name for this place; I work out it is a sales page from the button, and 'Power up' is a figure of speech" | give the page a plain title such as 'Super subscription' next to the X | confirmed |
| s14 | the Super subscription offer | none that names a place: a 'SUPER' wordmark top-right, an X top-left, and a marketing headline | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | not tested on the device: reaching this frame requires tapping START MY FREE WEEK (a free-trial start), which the run forbids... | Amy: "Again only a logo is boxed; 'fly through your lessons' is a metaphor and the picture is an abstract creature, so nothing literal names the screen" | give the page a plain title such as 'Super subscription' next to the X | provisional |
| s15 | the widget offer over the Shop | none that names a place: headline 'Add the Duolingo widget to your home screen to earn an XP Boost.' with ADD... | Missing View Identifier | tester verdict | High | both | Gopal, Kwame | the offer filled the screen with no title and no X; the Shop header was hidden; MAYBE LATER returned to the Shop | Gopal: "There is no title, only an offer; 'widget' and 'XP Boost' are terms I do not know, and there is no cross to go back" | keep the Shop top bar (with its X) visible above the offer, or title it 'Widget reward' | confirmed |
| s19 | the Super subscription offer | none that names a place: a 'SUPER' wordmark top-right, an X top-left, and a marketing headline | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | not tested on the device: reaching this frame requires tapping START MY FREE WEEK (a free-trial start), which the run forbids... | Amy: "Only a logo is boxed; I deduce it is a sales page from the button, not from any name for the screen" | give the page a plain title such as 'Super subscription' next to the X | provisional |
| s27 | the Learn path with no tab highlighted | none: the bottom bar shows no highlighted item; the only header is the unit banner 'SECTION 1... | Missing View Identifier | tester verdict | High | both | Gopal, Kwame | from Learn the house stayed boxed while the Profile/Video Call menu slid up; from Feed the menu opened with no tab boxed at all (neither the heart nor the ⋯)... | Gopal: "Nothing marks which part of the app I am in this time, and the band names a lesson, not a place" | keep the current tab highlighted until the next screen has drawn, and give the ⋯/Profile destination its own highlighted state | confirmed |
| s28 | the user's own Profile | the account holder's name 'Ally Cooper' top-left with share and settings icons... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | 'Create your avatar!' sheet covered the lower half (no tab bar); MAYBE LATER revealed the profile with the tab bar and no tab boxed... | Amy: "The top shows only a person's name; I infer it is my own profile from the settings gear and the empty avatar..." | title the screen 'Profile' (or 'Your profile') and highlight the ⋯ tab while it is shown | confirmed |
| s29 | the user's own Profile | the account holder's name 'Ally Cooper' top-left with share and settings icons... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | identifier read: the account holder's name 'Ally Cooper' top-left with share and settings icons... | Amy: "Only a name names the page, and none of the bottom-bar items is highlighted, so the bar does not tell me which section I am in either" | title the screen 'Profile' (or 'Your profile') and highlight the ⋯ tab while it is shown | confirmed |
| s32 | the user's own Profile | the account holder's name 'Ally Cooper' top-left with share and settings icons... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | identifier read: the account holder's name 'Ally Cooper' top-left with share and settings icons... | Amy: "Same as the other picture of this page: only a name, and no bottom-bar item is highlighted" | title the screen 'Profile' (or 'Your profile') and highlight the ⋯ tab while it is shown | confirmed |
| s42 | the free-chest reward screen | none that names a place: 'You earned 6 gems!' / 'Next free chest will be available in 1 minute' / DONE | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | 'You earned 6 gems!' with the chest picture and DONE; no title; DONE returned to the Shop | Amy: "The boxed text tells me what happened, not where I am, and nothing says where DONE will return me" | add the Shop top bar or a 'Free chest' title above the reward | confirmed |
| s45 | the unit Guidebook | none that names a place: X, mascot, 'SECTION 1, UNIT 1 / Order at a café', 'KEY PHRASES' | Missing View Identifier | tester verdict | High | both | Kwame | no 'Guidebook' anywhere; on scrolling, a collapsing title appeared in the top bar reading 'Section 1, Unit 1' — the unit again, not the screen; X returned to Learn | Kwame: "I can tell it is about this unit, but not what kind of page it is; there is no word like 'Guide'" | title the screen 'Guidebook — Section 1, Unit 1' | confirmed |
| s60 | an achievement detail | none that names a place: X top-left, a badge, a date and a headline describing one award | Missing View Identifier | tester verdict | High | both | Gopal, Kwame | not tested on the device: the other user's profile could not be reached: the live Find-your-friends screen shows no suggestions... | Gopal: "There is no title, only a sentence halfway down on a dark page; I would not know how I got here" | add a small title such as 'Achievement' beside the X | provisional |
| s61 | an achievement detail | none that names a place: X top-left, a badge, a date and a headline describing one award | Missing View Identifier | tester verdict | High | both | Gopal, Kwame | not tested on the device: the other user's profile could not be reached: the live Find-your-friends screen shows no suggestions... | Gopal: "No title, and 'Pearl League' is a name I cannot learn" | add a small title such as 'Achievement' beside the X | provisional |
| s70 | a quest-reward sequence | none that names a place: 'Quest complete!' / 'You earned a Double XP Boost…' / 'XP Boost activated!…' with CON... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | not tested on the device: the one-time 'Follow your first friend' quest reward has been consumed, and completing another would require adding a friend (forbidden)... | Amy: "It tells me an event happened, not where I am, and CONTINUE does not say where it goes" | add a 'Quests' title bar over the reward sequence | provisional |
| s71 | a quest-reward sequence | none that names a place: 'Quest complete!' / 'You earned a Double XP Boost…' / 'XP Boost activated!…' with CON... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | not tested on the device: the one-time 'Follow your first friend' quest reward has been consumed, and completing another would require adding a friend (forbidden)... | Amy: "The sentence describes a reward, not a place, and there is no title or bar to say which part of the app I am in" | add a 'Quests' title bar over the reward sequence | provisional |
| s72 | a quest-reward sequence | none that names a place: 'Quest complete!' / 'You earned a Double XP Boost…' / 'XP Boost activated!…' with CON... | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | not tested on the device: the one-time 'Follow your first friend' quest reward has been consumed, and completing another would require adding a friend (forbidden)... | Amy: "It describes a state change, not a place, and there is nothing else on the screen to locate me" | add a 'Quests' title bar over the reward sequence | provisional |
| s82 | the widget offer over the Shop | none that names a place: headline 'Add the Duolingo widget to your home screen to earn an XP Boost.' with ADD... | Missing View Identifier | tester verdict | High | both | Gopal, Kwame | identifier read: none that names a place: headline 'Add the Duolingo widget to your home screen to earn an XP Boost.' with ADD NOW / MAYBE LATER | Gopal: "There is no title, only an offer; 'widget' and 'XP Boost' are terms I do not know, and there is no cross to go back" | keep the Shop top bar (with its X) visible above the offer, or title it 'Widget reward' | confirmed |
| s89 | the free-chest reward screen | none that names a place: 'You earned 6 gems!' / 'Next free chest will be available in 1 minute' / DONE | Missing View Identifier | tester verdict | High | both | Amy, Gopal, Kwame | identifier read: none that names a place: 'You earned 6 gems!' / 'Next free chest will be available in 1 minute' / DONE | Amy: "It names what happened, not where I am, and DONE does not say where it goes" | add the Shop top bar or a 'Free chest' title above the reward | confirmed |
| s3 | the Learn path (home) | the house tab drawn inside a light-blue rounded box; the pink unit banner 'SECTION 1... | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame | identifier read: the house tab drawn inside a light-blue rounded box; the pink unit banner 'SECTION 1... | Amy: "The house tells me this is home, but the unit name is the name of a song and a person, not a description of what I am learning..." | Amy: "A unit title that says literally what the unit teaches, and content on the page, or a 'Loading' message while it fills" | confirmed |
| s5 | the Learn path (home) | the house tab drawn inside a light-blue rounded box in the bottom bar... | Missing View Identifier | classified from persona | Medium | persona | Gopal, Kwame | Scrolling: the unit banner and the tab bar stayed pinned; 'Greet people and say goodbye' / 'JUMP HERE?' scrolled past underneath | Gopal: "The only words at the top name a lesson, not a place, and the six pictures along the bottom have no words..." | Gopal: "Put a plain title such as 'Home' or 'Your lessons' at the top, and a word under each picture along the bottom" | confirmed |
| s8 | the Learn path (home) | the house tab drawn inside a light-blue rounded box in the bottom bar... | Missing View Identifier | classified from persona | Medium | persona | Gopal, Kwame | identifier read: the house tab drawn inside a light-blue rounded box in the bottom bar; above the path the unit banner 'SECTION 1, UNIT 1 / Order at a café' | Gopal: "The only words at the top name a lesson, not a place, and the six pictures along the bottom have no words..." | Gopal: "Put a plain title such as 'Home' or 'Your lessons' at the top, and a word under each picture along the bottom" | confirmed |
| s23 | the Learn path (home) | the house tab highlighted in the bottom bar; unit banner 'SECTION 1, UNIT 1 / Order at a café'... | Missing View Identifier | classified from persona | Medium | persona | Kwame | identifier read: the house tab highlighted in the bottom bar; unit banner 'SECTION 1, UNIT 1 / Order at a café'... | Kwame: "'Lesson 2 of 3' helps me, but the page itself has no name and the bottom row is pictures only" | Kwame: "A plain title such as 'Learn' or 'Home' at the top, and words under each picture in the bottom row" | confirmed |
| s25 | a lesson exercise | a lesson progress bar across the top with an X to quit, the energy count... | Missing View Identifier | classified from persona | Medium | persona | Kwame | lesson opened with the progress bar and X; choosing 'mom' highlighted the card and enabled CHECK, bar and instruction unchanged; X returned straight to the Learn path | Kwame: "'Select the correct image' tells me the task, and the bar suggests progress, but there is no step count and no name for the lesson..." | Kwame: "'Question 2 of 10' beside the bar, and the lesson name at the top" | confirmed |
| s26 | Leaderboards (empty) | trophy tab highlighted; body copy 'Finish 2 lessons to start competing on Leaderboards!' mid-screen | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame | no header at the top; the only text is 'Finish 2 lessons to start competing on Leaderboards!'; the trophy tab is boxed | Amy: "There is no title; I only find the word 'Leaderboards' inside an instruction sentence, and the highlighted bar item is a brown shape I cannot name" | Amy: "A title 'Leaderboards' at the top, and a text label under each bottom-bar item" | confirmed |
| s34 | Create Avatar | 'Create Avatar' in the top bar with X and DONE; category tabs with 'Skin tone' below | Missing View Identifier | classified from persona | Medium | persona | Gopal | not tested on the device: opening the editor risks saving an avatar (an account/profile change); the title is sufficient without the category heading | Gopal: "'Avatar' is a word I do not know, and the row of little pictures has no words, so I cannot tell which part I am on except by the 'Skin tone' heading" | Gopal: "Use 'Make your picture' as the title and put a word under each little picture" | provisional |
| s36 | the Learn path (home) | the house tab drawn inside a light-blue rounded box in the bottom bar... | Missing View Identifier | classified from persona | Medium | persona | Gopal, Kwame | identifier read: the house tab drawn inside a light-blue rounded box in the bottom bar; above the path the unit banner 'SECTION 1, UNIT 1 / Order at a café' | Gopal: "The only words at the top name a lesson, not a place, and the six pictures along the bottom have no words..." | Gopal: "Put a plain title such as 'Home' or 'Your lessons' at the top, and a word under each picture along the bottom" | confirmed |
| s46 | a lesson exercise | a lesson progress bar across the top with an X to quit, the energy count... | Missing View Identifier | classified from persona | Medium | persona | Kwame | identifier read: a lesson progress bar across the top with an X to quit, the energy count, and the instruction 'Select the correct image' | Kwame: "'Select the correct image' tells me the task, and the bar suggests progress, but there is no step count and no name for the lesson..." | Kwame: "'Question 2 of 10' beside the bar, and the lesson name at the top" | confirmed |
| s47 | the Learn path (home) | the house tab highlighted in the bottom bar; unit banner 'SECTION 1, UNIT 1 / Order at a café'... | Missing View Identifier | classified from persona | Medium | persona | Kwame | identifier read: the house tab highlighted in the bottom bar; unit banner 'SECTION 1, UNIT 1 / Order at a café'... | Kwame: "'Lesson 2 of 3' helps, but the page has no name and the bottom row is pictures" | Kwame: "A plain title such as 'Learn' or 'Home' at the top, and words under each picture in the bottom row" | confirmed |
| s50 | the share sheet over Find your friends | 'Find your friends' still readable at the top under the scrim... | Missing View Identifier | classified from persona | Medium | persona | Amy, Gopal, Kwame, Yuki | not tested on the device: opening the share flow is next to sharing, which the run forbids | Amy: "The boxed text at the bottom is a slogan, not a name for this panel, so I have to work out from the Messages and Save buttons that this is sharing" | Amy: "A plain title on the panel such as 'Share your profile'" | provisional |
| s68 | the Learn path (home) | the house tab drawn inside a light-blue rounded box in the bottom bar... | Missing View Identifier | classified from persona | Medium | persona | Gopal, Kwame | identifier read: the house tab drawn inside a light-blue rounded box in the bottom bar; above the path the unit banner 'SECTION 1, UNIT 1 / Order at a café' | Gopal: "The only words at the top name a lesson, not a place, and the six pictures along the bottom have no words..." | Gopal: "Put a plain title such as 'Home' or 'Your lessons' at the top, and a word under each picture along the bottom" | confirmed |
| s75 | the Learn path (home) | the house tab drawn inside a light-blue rounded box in the bottom bar... | Missing View Identifier | classified from persona | Medium | persona | Gopal, Kwame | identifier read: the house tab drawn inside a light-blue rounded box in the bottom bar; above the path the unit banner 'SECTION 1, UNIT 1 / Order at a café' | Gopal: "The only words at the top name a lesson, not a place, and the six pictures along the bottom have no words..." | Gopal: "Put a plain title such as 'Home' or 'Your lessons' at the top, and a word under each picture along the bottom" | confirmed |
| s78 | a lesson exercise | a lesson progress bar across the top with an X to quit, the energy count... | Missing View Identifier | classified from persona | Medium | persona | Kwame | identifier read: a lesson progress bar across the top with an X to quit, the energy count, and the instruction 'Select the correct image' | Kwame: "'Select the correct image' tells me the task, and the bar suggests progress, but there is no step count and no name for the lesson..." | Kwame: "'Question 2 of 10' beside the bar, and the lesson name at the top" | confirmed |
| s4 | the course menu open over the Learn path | the house tab still visibly boxed (dimmed under the scrim); the Spanish flag at the top boxed in blue... | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | menu dropped over the path: 'Spanish' (boxed) / 'Course', 'Your Spanish Score is 1', 'New Courses' over Math / Music / Chess... | Amy: "The only boxed name is 'New Courses', which is one section of the panel; the panel itself has no title, so I deduce what it is from the flags" | Amy: "A title at the top of the panel such as 'Your courses'" | confirmed |
| s7 | the course menu open over the Learn path | the house tab still visibly boxed (dimmed under the scrim); the Spanish flag at the top boxed in blue... | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | identifier read: the house tab still visibly boxed (dimmed under the scrim); the Spanish flag at the top boxed in blue... | Amy: "The panel has no title of its own; 'New Courses' names only its lower section" | Amy: "A title at the top of the panel such as 'Your courses'" | confirmed |
| s21 | Energy | 'Energy' in the top bar with an X and gem count | Missing View Identifier | classified from persona | Low | persona | Gopal | 'Energy' title with X; 25/25 bar; Unlimited / Recharge / Widget Boost / +5 energy rows | Gopal: "The title is there, but 'energy' here means something in the app that I have not learned, so the name does not tell me what this place is for" | Gopal: "Explain in a line under the title what energy is, e.g. 'Energy lets you do lessons'" | confirmed |
| s24 | the course menu open over the Learn path | the house tab still visibly boxed (dimmed under the scrim); the Spanish flag at the top boxed in blue... | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | identifier read: the house tab still visibly boxed (dimmed under the scrim); the Spanish flag at the top boxed in blue... | Amy: "The panel itself has no title; 'New Courses' names only its lower section" | Amy: "A title at the top of the panel such as 'Your courses'" | confirmed |
| s38 | the course menu open over the Learn path | the house tab still visibly boxed (dimmed under the scrim); the Spanish flag at the top boxed in blue... | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | identifier read: the house tab still visibly boxed (dimmed under the scrim); the Spanish flag at the top boxed in blue... | Amy: "The panel has no title; 'New Courses' names only one section of it" | Amy: "A title at the top of the panel such as 'Your courses'" | confirmed |
| s48 | the Feed | 'Feed' at the top-left; the heart-bubble tab highlighted | Missing View Identifier | classified from persona | Low | persona | Gopal | 'Feed' stayed pinned at the top and the heart tab stayed boxed while posts scrolled under | Gopal: "To me 'feed' means giving food; here it names something else, and I cannot learn what" | Gopal: "Call it something plain such as 'News from friends', and put words under the pictures at the bottom" | confirmed |
| s62 | the Feed | 'Feed' at the top-left; the heart-bubble tab highlighted | Missing View Identifier | classified from persona | Low | persona | Gopal | identifier read: 'Feed' at the top-left; the heart-bubble tab highlighted | Gopal: "To me 'feed' means giving food; here it names something else, and I cannot learn what" | Gopal: "Call it something plain such as 'News from friends', and put words under the pictures at the bottom" | confirmed |
| s63 | the Feed | 'Feed' at the top-left; the heart-bubble tab highlighted | Missing View Identifier | classified from persona | Low | persona | Gopal | identifier read: 'Feed' at the top-left; the heart-bubble tab highlighted | Gopal: "To me 'feed' means giving food; here it names something else, and I cannot learn what" | Gopal: "Call it something plain such as 'News from friends', and put words under the pictures at the bottom" | confirmed |
| s64 | the Feed | 'Feed' at the top-left; the heart-bubble tab highlighted | Missing View Identifier | classified from persona | Low | persona | Gopal | identifier read: 'Feed' at the top-left; the heart-bubble tab highlighted | Gopal: "To me 'feed' means giving food; here it names something else, and I cannot learn what" | Gopal: "Call it something plain such as 'News from friends', and put words under the pictures at the bottom" | confirmed |
| s65 | the Feed | 'Feed' at the top-left; the heart-bubble tab highlighted | Missing View Identifier | classified from persona | Low | persona | Gopal | identifier read: 'Feed' at the top-left; the heart-bubble tab highlighted | Gopal: "To me 'feed' means giving food; here it names something else, and I cannot learn what" | Gopal: "Call it something plain such as 'News from friends', and put words under the pictures at the bottom" | confirmed |
| s66 | the Feed | 'Feed' at the top-left; the heart-bubble tab highlighted | Missing View Identifier | classified from persona | Low | persona | Gopal | identifier read: 'Feed' at the top-left; the heart-bubble tab highlighted | Gopal: "To me 'feed' means giving food; here it names something else, and I cannot learn what" | Gopal: "Call it something plain such as 'News from friends', and put words under the pictures at the bottom" | confirmed |
| s69 | the course menu open over the Learn path | the house tab still visibly boxed (dimmed under the scrim); the Spanish flag at the top boxed in blue... | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | identifier read: the house tab still visibly boxed (dimmed under the scrim); the Spanish flag at the top boxed in blue... | Amy: "The only boxed name is 'New Courses', which names one section of the panel, not the panel itself..." | Amy: "A title at the top of the panel such as 'Your courses'" | confirmed |
| s76 | the course menu open over the Learn path | the house tab still visibly boxed (dimmed under the scrim); the Spanish flag at the top boxed in blue... | Missing View Identifier | classified from persona | Low | persona | Amy, Gopal, Kwame, Yuki | identifier read: the house tab still visibly boxed (dimmed under the scrim); the Spanish flag at the top boxed in blue... | Amy: "Same as before: only a section heading is named, the panel itself has no title" | Amy: "A title at the top of the panel such as 'Your courses'" | confirmed |

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
| s3 | Sufficient View Identifier | Amy | navigate with difficulty | "The house tells me this is home, but the unit name is the name of a song and a person, not a description of what I am learning..." | persona found an issue, tester did not |
| s3 | Sufficient View Identifier | Gopal | navigate with difficulty | "The band names a song, not a place, the rest of the page is blank, and the bottom pictures have no words" | persona found an issue, tester did not |
| s3 | Sufficient View Identifier | Kwame | navigate with difficulty | "The banner names a lesson, not the page, the rest of the screen is blank, and the bottom row has no words" | persona found an issue, tester did not |
| s4 | Sufficient View Identifier | Amy | navigate with difficulty | "The only boxed name is 'New Courses', which is one section of the panel; the panel itself has no title, so I deduce what it is from the flags" | persona found an issue, tester did not |
| s4 | Sufficient View Identifier | Gopal | navigate with difficulty | "There is no title saying what this panel is; 'New Courses' is halfway down and names only part of it..." | persona found an issue, tester did not |
| s4 | Sufficient View Identifier | Kwame | navigate with difficulty | "Half the screen is greyed out behind this panel and the only heading, 'New Courses', names one section, not what this panel is..." | persona found an issue, tester did not |
| s4 | Sufficient View Identifier | Yuki | navigate with difficulty | "The only name is 'New Courses', which is halfway down and only names one part..." | persona found an issue, tester did not |
| s5 | Sufficient View Identifier | Gopal | navigate with difficulty | "The only words at the top name a lesson, not a place, and the six pictures along the bottom have no words..." | persona found an issue, tester did not |
| s5 | Sufficient View Identifier | Kwame | navigate with difficulty | "The big green banner names a lesson topic, 'Order at a café', not a part of the app, and the bottom row is pictures without words..." | persona found an issue, tester did not |
| s7 | Sufficient View Identifier | Amy | navigate with difficulty | "The panel has no title of its own; 'New Courses' names only its lower section" | persona found an issue, tester did not |
| s7 | Sufficient View Identifier | Gopal | navigate with difficulty | "There is no title saying what this panel is; 'New Courses' is halfway down and names only part of it..." | persona found an issue, tester did not |
| s7 | Sufficient View Identifier | Kwame | navigate with difficulty | "Half the screen is greyed out behind this panel and the only heading, 'New Courses', names one section, not what this panel is..." | persona found an issue, tester did not |
| s7 | Sufficient View Identifier | Yuki | navigate with difficulty | "The only name is 'New Courses', which is halfway down and only names one part..." | persona found an issue, tester did not |
| s8 | Sufficient View Identifier | Gopal | navigate with difficulty | "The only words at the top name a lesson, not a place, and the six pictures along the bottom have no words..." | persona found an issue, tester did not |
| s8 | Sufficient View Identifier | Kwame | navigate with difficulty | "The big green banner names a lesson topic, 'Order at a café', not a part of the app, and the bottom row is pictures without words..." | persona found an issue, tester did not |
| s21 | Sufficient View Identifier | Gopal | navigate with difficulty | "The title is there, but 'energy' here means something in the app that I have not learned, so the name does not tell me what this place is for" | persona found an issue, tester did not |
| s23 | Sufficient View Identifier | Kwame | navigate with difficulty | "'Lesson 2 of 3' helps me, but the page itself has no name and the bottom row is pictures only" | persona found an issue, tester did not |
| s24 | Sufficient View Identifier | Amy | navigate with difficulty | "The panel itself has no title; 'New Courses' names only its lower section" | persona found an issue, tester did not |
| s24 | Sufficient View Identifier | Gopal | navigate with difficulty | "There is no title saying what this panel is; 'New Courses' is halfway down and names only part of it..." | persona found an issue, tester did not |
| s24 | Sufficient View Identifier | Kwame | navigate with difficulty | "Half the screen is greyed out behind this panel and the only heading, 'New Courses', names one section, not what this panel is..." | persona found an issue, tester did not |
| s24 | Sufficient View Identifier | Yuki | navigate with difficulty | "The only name is 'New Courses', which is halfway down and only names one part..." | persona found an issue, tester did not |
| s25 | Sufficient View Identifier | Kwame | navigate with difficulty | "'Select the correct image' tells me the task, and the bar suggests progress, but there is no step count and no name for the lesson..." | persona found an issue, tester did not |
| s26 | Sufficient View Identifier | Amy | navigate with difficulty | "There is no title; I only find the word 'Leaderboards' inside an instruction sentence, and the highlighted bar item is a brown shape I cannot name" | persona found an issue, tester did not |
| s26 | Sufficient View Identifier | Gopal | navigate with difficulty | "There is no title at the top; the only words are an instruction halfway down, and 'Leaderboards' is not my word" | persona found an issue, tester did not |
| s26 | Sufficient View Identifier | Kwame | navigate with difficulty | "I only work out the page name from the middle of a sentence; there is no title at the top" | persona found an issue, tester did not |
| s34 | Sufficient View Identifier | Gopal | navigate with difficulty | "'Avatar' is a word I do not know, and the row of little pictures has no words, so I cannot tell which part I am on except by the 'Skin tone' heading" | persona found an issue, tester did not |
| s36 | Sufficient View Identifier | Gopal | navigate with difficulty | "The only words at the top name a lesson, not a place, and the six pictures along the bottom have no words..." | persona found an issue, tester did not |
| s36 | Sufficient View Identifier | Kwame | navigate with difficulty | "The big green banner names a lesson topic, 'Order at a café', not a part of the app, and the bottom row is pictures without words..." | persona found an issue, tester did not |
| s38 | Sufficient View Identifier | Amy | navigate with difficulty | "The panel has no title; 'New Courses' names only one section of it" | persona found an issue, tester did not |
| s38 | Sufficient View Identifier | Gopal | navigate with difficulty | "There is no title saying what this panel is; 'New Courses' is halfway down and names only part of it..." | persona found an issue, tester did not |
| s38 | Sufficient View Identifier | Kwame | navigate with difficulty | "Half the screen is greyed out behind this panel and the only heading, 'New Courses', names one section, not what this panel is..." | persona found an issue, tester did not |
| s38 | Sufficient View Identifier | Yuki | navigate with difficulty | "The only name is 'New Courses', which is halfway down and only names one part..." | persona found an issue, tester did not |
| s46 | Sufficient View Identifier | Kwame | navigate with difficulty | "'Select the correct image' tells me the task, and the bar suggests progress, but there is no step count and no name for the lesson..." | persona found an issue, tester did not |
| s47 | Sufficient View Identifier | Kwame | navigate with difficulty | "'Lesson 2 of 3' helps, but the page has no name and the bottom row is pictures" | persona found an issue, tester did not |
| s48 | Sufficient View Identifier | Gopal | navigate with difficulty | "To me 'feed' means giving food; here it names something else, and I cannot learn what" | persona found an issue, tester did not |
| s50 | Sufficient View Identifier | Amy | navigate with difficulty | "The boxed text at the bottom is a slogan, not a name for this panel, so I have to work out from the Messages and Save buttons that this is sharing" | persona found an issue, tester did not |
| s50 | Sufficient View Identifier | Gopal | navigate with difficulty | "The only heading is a slogan; nothing says I am sharing, and the page behind is greyed out" | persona found an issue, tester did not |
| s50 | Sufficient View Identifier | Kwame | navigate with difficulty | "Several layers at once and no title on the part in front, so I have to work out that I am sharing something" | persona found an issue, tester did not |
| s50 | Sufficient View Identifier | Yuki | navigate with difficulty | "The panel covers the page, it's the phone's own share menu, and I have to piece together that I'm still inside the find-friends step" | persona found an issue, tester did not |
| s62 | Sufficient View Identifier | Gopal | navigate with difficulty | "To me 'feed' means giving food; here it names something else, and I cannot learn what" | persona found an issue, tester did not |
| s63 | Sufficient View Identifier | Gopal | navigate with difficulty | "To me 'feed' means giving food; here it names something else, and I cannot learn what" | persona found an issue, tester did not |
| s64 | Sufficient View Identifier | Gopal | navigate with difficulty | "To me 'feed' means giving food; here it names something else, and I cannot learn what" | persona found an issue, tester did not |
| s65 | Sufficient View Identifier | Gopal | navigate with difficulty | "To me 'feed' means giving food; here it names something else, and I cannot learn what" | persona found an issue, tester did not |
| s66 | Sufficient View Identifier | Gopal | navigate with difficulty | "To me 'feed' means giving food; here it names something else, and I cannot learn what" | persona found an issue, tester did not |
| s68 | Sufficient View Identifier | Gopal | navigate with difficulty | "The only words at the top name a lesson, not a place, and the six pictures along the bottom have no words..." | persona found an issue, tester did not |
| s68 | Sufficient View Identifier | Kwame | navigate with difficulty | "The big green banner names a lesson topic, 'Order at a café', not a part of the app, and the bottom row is pictures without words..." | persona found an issue, tester did not |
| s69 | Sufficient View Identifier | Amy | navigate with difficulty | "The only boxed name is 'New Courses', which names one section of the panel, not the panel itself..." | persona found an issue, tester did not |
| s69 | Sufficient View Identifier | Gopal | navigate with difficulty | "There is no title saying what this panel is; 'New Courses' is halfway down and names only part of it..." | persona found an issue, tester did not |
| s69 | Sufficient View Identifier | Kwame | navigate with difficulty | "Half the screen is greyed out behind this panel and the only heading, 'New Courses', names one section, not what this panel is..." | persona found an issue, tester did not |
| s69 | Sufficient View Identifier | Yuki | navigate with difficulty | "The only name is 'New Courses', which is halfway down and only names one part..." | persona found an issue, tester did not |
| s75 | Sufficient View Identifier | Gopal | navigate with difficulty | "The only words at the top name a lesson, not a place, and the six pictures along the bottom have no words..." | persona found an issue, tester did not |
| s75 | Sufficient View Identifier | Kwame | navigate with difficulty | "The big green banner names a lesson topic, 'Order at a café', not a part of the app, and the bottom row is pictures without words..." | persona found an issue, tester did not |
| s76 | Sufficient View Identifier | Amy | navigate with difficulty | "Same as before: only a section heading is named, the panel itself has no title" | persona found an issue, tester did not |
| s76 | Sufficient View Identifier | Gopal | navigate with difficulty | "There is no title saying what this panel is; 'New Courses' is halfway down and names only part of it..." | persona found an issue, tester did not |
| s76 | Sufficient View Identifier | Kwame | navigate with difficulty | "Half the screen is greyed out behind this panel and the only heading, 'New Courses', names one section, not what this panel is..." | persona found an issue, tester did not |
| s76 | Sufficient View Identifier | Yuki | navigate with difficulty | "The only name is 'New Courses', which is halfway down and only names one part..." | persona found an issue, tester did not |
| s78 | Sufficient View Identifier | Kwame | navigate with difficulty | "'Select the correct image' tells me the task, and the bar suggests progress, but there is no step count and no name for the lesson..." | persona found an issue, tester did not |

## 7. Withdrawn after testing

| Subject | Who withdrew | From | To | What the test showed |
|---|---|---|---|---|
| s27 | Amy | navigate with difficulty | no problem | Every time I reached the path on the phone the house was highlighted, including after I left and came back... |
| t18 | Amy | navigate with difficulty | no problem | On the phone, scrolling and swiping on Streak never left the page, and the 'Streak' title and tabs stayed fixed at the top... |
| t18 | Gopal | navigate with difficulty | no problem | On the phone, scrolling the Streak page up and down, and even pulling at the top, never took me anywhere else... |
| t18 | Kwame | cannot handle it at all | no problem | The 'Streak' title and tabs stayed at the top through every scroll and sideways swipe... |
| t18 | Yuki | navigate with difficulty | no problem | Scrolling up, down and sideways always kept 'Streak' and the tabs pinned at the top, and I only left the page when I tapped X, so on the phone the name never left me |

## 8. Detection false positives

| Screen | Region | What it said | Why it names no place | Persona said the same |
|---|---|---|---|---|
| s2 | header | "For English speakers" | labels the group of courses in the list, not a place — dismissed | — |
| s3 | header | "SECTION 1, UNIT 1 / Hot Cross Buns – Zari’s version" | names the course unit being studied, not a part of the app | — |
| s4 | header | "New Courses" | heading of a group of course shortcuts inside the course menu, not a place — dismissed | Amy, Gopal, Kwame, Yuki |
| s5 | header | "SECTION 1, UNIT 1 / Order at a café" | names the course unit being studied, not a part of the app | Kwame |
| s6 | header | "Streak Calendar" | sub-section heading inside the Streak page; names part of the page, not the screen — not counted | — |
| s6 | header | "Streak Society" | sub-section heading inside the Streak page; names part of the page, not the screen — not counted | — |
| s7 | header | "New Courses" | heading of a group of course shortcuts inside the course menu, not a place — dismissed | Amy, Gopal, Kwame, Yuki |
| s8 | header | "SECTION 1, UNIT 1 / Order at a café" | names the course unit being studied, not a part of the app | Kwame |
| s11 | header | "Special Offers" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s11 | header | "Streak" | sub-section heading of the Shop list (streak items for sale); names a group of items, not the screen, and shares its word with the Streak screen... | — |
| s12 | header | "SUPER" | product wordmark of the subscription — branding, not a part of the app | Kwame |
| s13 | header | "Special Offers" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s13 | header | "Streak" | sub-section heading of the Shop list (streak items for sale); names a group of items, not the screen, and shares its word with the Streak screen... | — |
| s14 | header | "SUPER" | product wordmark of the subscription — branding, not a part of the app | Kwame |
| s15 | header | "Add the Duolingo widget to your home screen to earn an XP Boost." | describes an offer (the widget reward), not a place in the app | — |
| s16 | header | "Special Offers" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s16 | header | "Streak" | sub-section heading of the Shop list (streak items for sale); names a group of items, not the screen, and shares its word with the Streak screen... | — |
| s17 | header | "SUPER" | product wordmark of the subscription — branding, not a part of the app | — |
| s18 | header | "Special Offers" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s18 | header | "Streak" | sub-section heading of the Shop list (streak items for sale); names a group of items, not the screen, and shares its word with the Streak screen... | — |
| s19 | header | "SUPER" | product wordmark of the subscription — branding, not a part of the app | Kwame |
| s20 | header | "Energy" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s20 | header | "Promo Code" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s23 | header | "SECTION 1, UNIT 1 / Order at a café" | names the course unit being studied, not a part of the app | — |
| s24 | header | "New Courses" | heading of a group of course shortcuts inside the course menu, not a place — dismissed | Amy, Gopal, Kwame, Yuki |
| s25 | header | "Select the correct image" | an exercise instruction — says what to do, not where you are | Kwame |
| s27 | header | "SECTION 1, UNIT 1 / Order at a café" | names the course unit being studied, not a part of the app | Kwame |
| s28 | header | "Ally Cooper" | the account holder's own name — names a person, not the section (no 'Profile' title anywhere) | — |
| s28 | header | "Create your avatar!" | the prompt of a bottom sheet offering avatar creation, not a place — dismissed | — |
| s29 | header | "Ally Cooper" | the account holder's own name — names a person, not the section (no 'Profile' title anywhere) | — |
| s32 | header | "Ally Cooper" | the account holder's own name — names a person, not the section (no 'Profile' title anywhere) | — |
| s35 | header | "Friend suggestions" | sub-section heading naming a list of people, not the screen — not counted | — |
| s36 | header | "SECTION 1, UNIT 1 / Order at a café" | names the course unit being studied, not a part of the app | Kwame |
| s37 | header | "Streak Calendar" | sub-section heading inside the Streak page; names part of the page, not the screen — not counted | — |
| s37 | header | "Streak Society" | sub-section heading inside the Streak page; names part of the page, not the screen — not counted | — |
| s38 | header | "New Courses" | heading of a group of course shortcuts inside the course menu, not a place — dismissed | Amy, Gopal, Kwame, Yuki |
| s42 | header | "You earned 6 gems!" | reports a reward outcome, not a place — dismissed | — |
| s43 | header | "Special Offers" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s43 | header | "Streak" | sub-section heading of the Shop list (streak items for sale); names a group of items, not the screen, and shares its word with the Streak screen... | — |
| s44 | header | "Special Offers" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s44 | header | "Streak" | sub-section heading of the Shop list (streak items for sale); names a group of items, not the screen, and shares its word with the Streak screen... | — |
| s45 | header | "SECTION 1, UNIT 1 / Order at a café" | names the course unit being studied, not a part of the app | — |
| s46 | header | "Select the correct image" | an exercise instruction — says what to do, not where you are | — |
| s47 | header | "SECTION 1, UNIT 1 / Order at a café" | names the course unit being studied, not a part of the app | — |
| s49 | header | "Friend suggestions" | sub-section heading naming a list of people, not the screen — not counted | — |
| s50 | header | "FOLLOW ME ON DUOLINGO!" | the caption of the card being shared, not a place — dismissed | — |
| s58 | header | "Personal Records" | sub-section heading of the achievements page — not counted | — |
| s58 | header | "Awards" | sub-section heading of the achievements page — not counted | — |
| s60 | header | "Baron Laqeas’s longest streak is 88!" | describes one award, not a place — dismissed | — |
| s61 | header | "Baron Laqeas’s best league finish was #6 in Pearl League!" | describes one award, not a place — dismissed | — |
| s68 | header | "SECTION 1, UNIT 1 / Order at a café" | names the course unit being studied, not a part of the app | Kwame |
| s69 | header | "New Courses" | heading of a group of course shortcuts inside the course menu, not a place — dismissed | Amy, Gopal, Kwame, Yuki |
| s70 | header | "Quest complete!" | reports an event, not a place — dismissed | — |
| s71 | header | "You earned a Double XP Boost for 15 minutes and 50 gems!" | reports a reward outcome, not a place — dismissed | — |
| s72 | header | "XP Boost activated! Earn double XP for the next 15 minutes." | reports an outcome on an overlay, not a place — dismissed | — |
| s74 | header | "Friend suggestions" | sub-section heading naming a list of people, not the screen — not counted | — |
| s75 | header | "SECTION 1, UNIT 1 / Order at a café" | names the course unit being studied, not a part of the app | Kwame |
| s76 | header | "New Courses" | heading of a group of course shortcuts inside the course menu, not a place — dismissed | Gopal, Kwame, Yuki |
| s77 | header | "Friend suggestions" | sub-section heading naming a list of people, not the screen — not counted | — |
| s78 | header | "Select the correct image" | an exercise instruction — says what to do, not where you are | — |
| s79 | header | "Special Offers" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s79 | header | "Streak" | sub-section heading of the Shop list (streak items for sale); names a group of items, not the screen, and shares its word with the Streak screen... | — |
| s80 | header | "SUPER" | product wordmark of the subscription — branding, not a part of the app | — |
| s81 | header | "Special Offers" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s81 | header | "Streak" | sub-section heading of the Shop list (streak items for sale); names a group of items, not the screen, and shares its word with the Streak screen... | — |
| s82 | header | "Add the Duolingo widget to your home screen to earn an XP Boost." | describes an offer (the widget reward), not a place in the app | — |
| s83 | header | "Special Offers" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s83 | header | "Streak" | sub-section heading of the Shop list (streak items for sale); names a group of items, not the screen, and shares its word with the Streak screen... | — |
| s84 | header | "Special Offers" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s84 | header | "Streak" | sub-section heading of the Shop list (streak items for sale); names a group of items, not the screen, and shares its word with the Streak screen... | — |
| s85 | header | "XP Boost activated! Earn double XP for the next 10 minutes." | reports an outcome on an overlay, not a place — dismissed | — |
| s86 | header | "XP Boost activated! Earn double XP for the next 25 minutes." | reports an outcome on an overlay, not a place — dismissed | — |
| s87 | header | "Special Offers" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s87 | header | "Streak" | sub-section heading of the Shop list (streak items for sale); names a group of items, not the screen, and shares its word with the Streak screen... | — |
| s89 | header | "You earned 9 gems!" | reports a reward outcome, not a place — dismissed | — |
| s90 | header | "Special Offers" | sub-section heading of the Shop list; names a group of items, not the screen — not counted | — |
| s90 | header | "Streak" | sub-section heading of the Shop list (streak items for sale); names a group of items, not the screen, and shares its word with the Streak screen... | — |

## 9. Summary

| Found by | Screens | Transitions |
|---|---|---|
| both | 24 | 0 |
| tester | 0 | 0 |
| persona | 27 | 0 |
| none | 38 | 1 |
| not evaluated / N/A | 1 | 150 |

| Issue | Count |
|---|---|
| Missing View Identifier | 51 |
| Disappearing View Identifier | 0 |
| Classification missing | 0 |

| Severity | Issues |
|---|---|
| Critical | 6 |
| High | 18 |
| Medium | 14 |
| Low | 13 |

| Persona | Issues held |
|---|---|
| Amy | 27 |
| Gopal | 45 |
| Kwame | 43 |
| Yuki | 14 |

| Count | Value |
|---|---|
| Exceptions upheld | 0 |
| Disagreements | 27 |
| Provisional | 15 |
| Unreachable | 0 |
| Withdrawn after testing | 5 |
| Detection false positives | 77 |
| Out-of-scope observations | 36 |
