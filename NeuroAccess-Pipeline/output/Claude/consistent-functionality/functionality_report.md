# Functionality Report — Claude

**Date:** 2026-09-30 · **Screens:** 35 · **Elements evaluated:** 161 · **Groups judged:** 52 of 52 (28 glyph · 22 function · 2 candidate)
**Issues:** 7 groups · **By severity:** Critical 0 · High 2 · Medium 5 · Low 0
**Personas:** All four ran — Amy, Gopal, Kwame, Yuki.

## 1. Attribution at a glance

| Group | Conflict kind | Appearance / function | Members | Screens | Severity | Found by | Personas | Observed | Recommendation | Via candidate | Confidence |
|---|---|---|---|---|---|---|---|---|---|---|---|
| gg1 | same appearance, different functionality | X | screen3-f2, screen4-f1, screen6-f2, screen7-f1, screen8-f1, screen20-f1, screen21-f2, screen22-f2, screen23-f1, screen24-f1, screen27-f1, screen28-f1, screen31-f1, screen32-f1, screen34-f2, screen35-f1 | screen3, screen4, screen6, screen7, screen8, screen20, screen21, screen22, screen23, screen24, screen27, screen28, screen31, screen32, screen34, screen35 | High | persona | Amy, Kwame, Yuki | screen3-f2: turns incognito off on the same screen: the X becomes the ghost again, the incognito wording disappears and the regular greeting returns; the composer and any draft stay; screen4-f1: closes the surface and returns to the home composer underneath; screen6-f2: closes the surface and returns to the home composer underneath; screen7-f1: closes the surface and returns to the home composer underneath; screen8-f1: closes the surface and returns to the home composer underneath; screen20-f1: closes the surface and returns to the home composer underneath; screen21-f2: turns incognito off on the same screen: the X becomes the ghost again, the incognito wording disappears and the regular greeting returns; the composer and any draft stay; screen22-f2: closes the surface and returns to the incognito composer underneath; screen23-f1: closes the surface and returns to the incognito composer underneath; screen24-f1: closes the surface and returns to the incognito composer underneath; screen27-f1: closes the surface and returns to the home composer underneath; screen28-f1: closes the surface and returns to the home composer underneath; screen31-f1: closes the surface and returns to the home composer underneath; screen32-f1: closes the surface and returns to the home composer underneath; screen34-f2: turns incognito off on the same screen: the X becomes the ghost again, the incognito wording disappears and the regular greeting returns; the composer and any draft stay; screen35-f1: closes the surface and returns to the home composer underneath | Amy: "Keep the close X in one position (top-left) everywhere. On the incognito screen replace the X with a text button that says 'Leave incognito' or 'Exit incognito chat'."; Kwame: "Give the top-right one words, such as 'Leave incognito', or keep the ghost there and show it switched on, so the plain X only ever means 'close this panel'."; Yuki: "Put a word next to the chat-corner X, like 'Exit incognito', or keep the ghost there and show it as switched on, so the plain X only ever means close this panel." | no | confirmed |
| fg4 | same functionality, different appearance | new chat | screen2-f2, screen2-f8, screen12-f3, screen18-f2, screen18-f8, screen33-f2, screen33-f8 | screen2, screen12, screen18, screen33 | High | both | Amy, Kwame | screen2-f2: opened a fresh empty chat composer with the keyboard up (drawer closed); screen2-f8: opened a fresh empty chat composer with the keyboard up (drawer closed); screen12-f3: opened a new empty chat composer (with a back arrow to Chats); screen18-f2: opened a fresh empty chat composer with the keyboard up (drawer closed); screen18-f8: opened a fresh empty chat composer with the keyboard up (drawer closed); screen33-f2: opened a fresh empty chat composer with the keyboard up (drawer closed); screen33-f8: opened a fresh empty chat composer with the keyboard up (drawer closed) | make the drawer wordmark a plain, non-interactive title and leave "+ New chat" as the single rendering of the job; if the title must stay pressable, give it the same "+ New chat" treatment so it reads as that action | no | confirmed |
| gg6 | same appearance, different functionality | microphone in a grey circle | screen1-f6, screen3-f7, screen5-f6, screen10-f6, screen11-f6, screen17-f6, screen19-f6, screen21-f7, screen26-f6, screen34-f7 | screen1, screen3, screen5, screen10, screen11, screen17, screen19, screen21, screen26, screen34 | Medium | persona | Gopal | screen1-f6: opens the page "Send messages to Claude using your voice." (speech-input introduction); screen3-f7: opens the page "Send messages to Claude using your voice." (speech-input introduction); screen5-f6: opens the page "Send messages to Claude using your voice." (speech-input introduction); screen10-f6: opens the page "Send messages to Claude using your voice." (speech-input introduction); screen11-f6: opens the page "Send messages to Claude using your voice." (speech-input introduction); screen17-f6: opens the page "Send messages to Claude using your voice." (speech-input introduction); screen19-f6: opens the page "Send messages to Claude using your voice." (speech-input introduction); screen21-f7: opens the page "Send messages to Claude using your voice." (speech-input introduction); screen26-f6: opens the page "Send messages to Claude using your voice." (speech-input introduction); screen34-f7: opens the page "Send messages to Claude using your voice." (speech-input introduction) | Gopal: "Show only one microphone at a time, and put the word 'Speak' beside it." | no | confirmed |
| gg7 | same appearance, different functionality | vertical sound-wave bars in a black circle | screen1-f7, screen3-f8, screen5-f7, screen10-f7, screen11-f7, screen17-f7, screen19-f7, screen21-f8, screen26-f7, screen34-f8 | screen1, screen3, screen5, screen10, screen11, screen17, screen19, screen21, screen26, screen34 | Medium | persona | Kwame | screen1-f7: not executed — starting voice mode is not allowed on the test devices; screen3-f8: not executed — starting voice mode is not allowed on the test devices; screen5-f7: not executed — starting voice mode is not allowed on the test devices; screen10-f7: not executed — starting voice mode is not allowed on the test devices; screen11-f7: not executed — starting voice mode is not allowed on the test devices; screen17-f7: not executed — starting voice mode is not allowed on the test devices; screen19-f7: not executed — starting voice mode is not allowed on the test devices; screen21-f8: not executed — starting voice mode is not allowed on the test devices; screen26-f7: not executed — starting voice mode is not allowed on the test devices; screen34-f8: not executed — starting voice mode is not allowed on the test devices | Kwame: "Label the black one with a word such as 'Talk' or 'Voice chat', and keep it visibly different from the microphone and from a send arrow." | no | provisional |
| gg8 | same functionality, different appearance | ghost outline | screen1-f2, screen5-f2, screen10-f2, screen11-f2, screen17-f2, screen19-f2, screen26-f2 | screen1, screen5, screen10, screen11, screen17, screen19, screen26 | Medium | persona | Kwame | screen1-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen5-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen10-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen11-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen17-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen19-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen26-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear | Kwame: "Add the word 'Incognito' under or beside the ghost, and keep the ghost in the corner shown as switched on, rather than replacing it with an X." | no | confirmed |
| gg20 | same appearance, different functionality | three vertical sliders | screen12-f2, screen13-f2, screen15-f2 | screen12, screen13, screen15 | Medium | persona | Kwame | screen12-f2: opened a dropdown "All ✓ / Pinned" under the icon; screen13-f2: opened a dropdown "Yours ✓ / Archived" under the icon; screen15-f2: opened a dropdown "All ✓ / Pinned / Yours / Shared with you" under the icon | Kwame: "Put the word 'Filter' or 'Sort' beside it, so it is not confused with the Capabilities setting." | no | confirmed |
| fg1 | same functionality, different appearance | incognito chat | screen1-f2, screen3-f2, screen5-f2, screen10-f2, screen11-f2, screen17-f2, screen19-f2, screen21-f2, screen26-f2, screen34-f2 | screen1, screen3, screen5, screen10, screen11, screen17, screen19, screen21, screen26, screen34 | Medium | persona | Gopal, Kwame, Yuki | screen1-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen3-f2: turns incognito off on the same screen: the X becomes the ghost again, the incognito wording disappears and the regular greeting returns; the composer and any draft stay; screen5-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen10-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen11-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen17-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen19-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen21-f2: turns incognito off on the same screen: the X becomes the ghost again, the incognito wording disappears and the regular greeting returns; the composer and any draft stay; screen26-f2: switches the chat to incognito: the ghost becomes an X, "Incognito chat" and the incognito explanation appear; screen34-f2: turns incognito off on the same screen: the X becomes the ghost again, the incognito wording disappears and the regular greeting returns; the composer and any draft stay | Gopal: "Use words in that corner for both: 'Private chat' to go in and 'Leave private chat' to come out, so it is plain that they are two halves of the same thing."; Kwame: "Keep one picture in that corner and show it switched on or off, with the word 'Incognito' beside it, rather than swapping it for an X."; Yuki: "Keep the ghost there and make it look switched on (filled, highlighted, or with a word like 'Incognito on') instead of swapping it for an X." | no | confirmed |

## 2. Expectation mismatches

| Group | Persona | Expected the same? | Expected | Actual | Conflict kind (persona-only) |
|---|---|---|---|---|---|
| gg1 | Gopal | yes | A cross is the one symbol here I have known all my life; it means close, and I expect it to close whatever is in front of me each time. | screen3-f2, screen21-f2 and screen34-f2 turn incognito off on the same screen; the other 13 close their sheet or page and return to the screen underneath | — |
| fg4 | Amy | no | 'New chat' says it starts a chat; 'Claude' is a heading and does not say it does anything at all. | all 7 start a new empty chat: the "Claude" wordmark (screen2-f2, screen18-f2, screen33-f2) opens a fresh empty chat composer exactly as "+ New chat" does | — |
| fg4 | Gopal | no | One is the heading at the top of the panel and the other is a button that plainly says 'New chat'; I would not expect a heading to start a new conversation. | all 7 start a new empty chat: the "Claude" wordmark (screen2-f2, screen18-f2, screen33-f2) opens a fresh empty chat composer exactly as "+ New chat" does | — |
| fg4 | Kwame | no | 'New chat' says it starts a conversation; 'Claude' looks like a title, and I would not expect a title to do anything, least of all start a new chat. | all 7 start a new empty chat: the "Claude" wordmark (screen2-f2, screen18-f2, screen33-f2) opens a fresh empty chat composer exactly as "+ New chat" does | — |
| fg4 | Yuki | no | The New chat buttons obviously start a chat, but the 'Claude' title looks like a heading - I wouldn't expect it to do anything, let alone the same as New chat. | all 7 start a new empty chat: the "Claude" wordmark (screen2-f2, screen18-f2, screen33-f2) opens a fresh empty chat composer exactly as "+ New chat" does | — |

## 3. Contested exceptions

| Group | Context the tester relied on | Persona | Persona said | Tester verdict | Persona verdict | Severity |
|---|---|---|---|---|---|---|
| gg1 | "Incognito chat" centred directly under the top bar, the large ghost and "Incognito chats stay out of your history and search, and aren't used to train Claude." — visible in the same top band as the X before the tap | Amy | The same X is used for two jobs (close a panel, leave incognito) and it is not even in the same corner, so I cannot rely on either its position or its picture; nothing written tells me which job the top-right one does. | Consistent Functionality | navigate with difficulty | High |
| gg1 | "Incognito chat" centred directly under the top bar, the large ghost and "Incognito chats stay out of your history and search, and aren't used to train Claude." — visible in the same top band as the X before the tap | Kwame | Thirteen of these are the same close button in the same top-left place on a panel and I would handle them easily. The three in the top right of the chat screen are the same picture in a different place doing, I think, a different job: leaving incognito. I would read that one over and over, asking whether it closes, leaves or deletes. | Consistent Functionality | navigate with difficulty | High |
| gg1 | "Incognito chat" centred directly under the top bar, the large ghost and "Incognito chats stay out of your history and search, and aren't used to train Claude." — visible in the same top band as the X before the tap | Yuki | The X on the slide-up panels is fine, but the same X in the corner of a chat means something else and I can't tell from the picture whether it ends incognito or closes and loses my chat. | Consistent Functionality | navigate with difficulty | High |

## 4. Disagreements

| Group | Tester verdict | Persona | Persona verdict | Persona said | Direction |
|---|---|---|---|---|---|
| gg1 | Consistent Functionality | Amy | navigate with difficulty | The same X is used for two jobs (close a panel, leave incognito) and it is not even in the same corner, so I cannot rely on either its position or its picture; nothing written tells me which job the top-right one does. | persona found an issue, tester did not |
| gg1 | Consistent Functionality | Kwame | navigate with difficulty | Thirteen of these are the same close button in the same top-left place on a panel and I would handle them easily. The three in the top right of the chat screen are the same picture in a different place doing, I think, a different job: leaving incognito. I would read that one over and over, asking whether it closes, leaves or deletes. | persona found an issue, tester did not |
| gg1 | Consistent Functionality | Yuki | navigate with difficulty | The X on the slide-up panels is fine, but the same X in the corner of a chat means something else and I can't tell from the picture whether it ends incognito or closes and loses my chat. | persona found an issue, tester did not |
| gg6 | Consistent Functionality | Gopal | navigate with difficulty | The microphone itself I recognise. But on several of these screens there are two microphones, one above the other, and a black round button with lines right beside them. I would not know which one to press. | persona found an issue, tester did not |
| gg7 | Consistent Functionality | Kwame | navigate with difficulty | Two voice-looking buttons sit next to each other, and the one I would mistake for 'send' is the black one. I cannot tell which one types my speech and which one starts a spoken conversation. The same sound-bar picture also appears beside 'Voice' in Settings, which suggests it is a voice setting as well. | persona found an issue, tester did not |
| gg8 | Consistent Functionality | Kwame | navigate with difficulty | I do not recognize the ghost as meaning anything, so I cannot connect it to incognito until after I have pressed it. Once pressed, the ghost is gone and an X is in its place, so the same corner shows two pictures and I cannot tell which state I am in. | persona found an issue, tester did not |
| gg20 | Consistent Functionality | Kwame | navigate with difficulty | The three here are consistent with each other, but I have seen the same slider picture on the Settings screen beside 'Capabilities', so I would not be confident whether this one sorts my list or takes me somewhere to change what Claude can do. | persona found an issue, tester did not |
| fg1 | Consistent Functionality | Gopal | navigate with difficulty | The cross I could use to leave, because I know what a cross means. But nothing tells me that the ghost and the cross belong together, one to go in and one to come out. I would not know how I got into the incognito screen or how to get back into it. | persona found an issue, tester did not |
| fg1 | Consistent Functionality | Kwame | navigate with difficulty | I do not recognize the ghost, and when it becomes an X it looks exactly like the close button on panels. I would not connect the X to the ghost, and I would be unsure whether pressing the X closes, deletes or leaves my chat. | persona found an issue, tester did not |
| fg1 | Consistent Functionality | Yuki | navigate with difficulty | The ghost turning into a plain X doesn't read as the same switch. An X means close to me, and on the slide-up panels in this app it does mean close. | persona found an issue, tester did not |

## 5. Withdrawn after testing

| Group | Who withdrew | From | To | What the test showed |
|---|---|---|---|---|
| gg4 | Kwame | navigate with difficulty | reversed | My word 'test' was still in the box and I was still in the incognito chat. Nothing was thrown away. |
| gg12 | Kwame | navigate with difficulty | reversed | It closed the menu both times, whatever picture was showing through underneath. |
| gg12 | Yuki | navigate with difficulty | reversed | The whole grey strip does one simple thing: close the menu. |

## 6. Detection false positives

| Element | Screen | Group | Tester observed | Found by | Personas told |
|---|---|---|---|---|---|
| none | — | — | — | — | — |

## 7. Summary

| Found by | Groups |
|---|---|
| both | 1 |
| tester | 0 |
| persona | 6 |
| none | 44 |
| not evaluated | 0 |

| Conflict kind | Groups |
|---|---|
| same appearance, different functionality | 4 |
| same functionality, different appearance | 3 |
| classification missing | 0 |

| Severity | Groups |
|---|---|
| Critical | 0 |
| High | 2 |
| Medium | 5 |
| Low | 0 |

| Persona | Issues held |
|---|---|
| Amy | 2 |
| Gopal | 2 |
| Kwame | 6 |
| Yuki | 2 |

| Count | Value |
|---|---|
| Expectation mismatches | 5 |
| Contested exceptions | 1 |
| Disagreements | 6 |
| Provisional | 6 |
| Withdrawn after testing | 3 |
| Candidates confirmed | 1 |
| Candidates dissolved | 1 |
| Function groups superseded | 0 |
| Detection false positives | 0 |
| Out-of-scope observations (incl. purpose complaints; not issues) | 37 |
