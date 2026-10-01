# Study Quest v1.3.0
https://digitaldraven.github.io/StudyQuest/

A no-API, client-side flashcard web app for turning school practice-test photos into study decks using ChatGPT as the image-understanding/import assistant.

## Architecture

- GitHub Pages / static hosting compatible
- No backend
- No API keys
- ChatGPT handles image understanding using `templates/chatgpt-import-template.md`
- Study Quest imports the resulting StudyCards 1.0 JSON
- Decks and progress are stored locally in the browser
- Decks can be exported as portable `.studyquest.json` files and imported on another computer or iPad
- GSAP is used for UI animation; the core app remains dependency-light

## V1.2 workflow

1. Photograph every page of a practice test.
2. Open **New Deck** and copy the ChatGPT import template.
3. Start a ChatGPT conversation, attach one or more test images, and paste the template.
4. Ask ChatGPT to return the JSON exactly as instructed.
5. Paste the JSON into Study Quest.
6. Use **Validation Review** to scan the compact card list and expand any card that needs editing.
7. Save & Study, or export the deck for backup/transfer.

## Study modes

- **Study Mode:** question first, then reveal the answer. Multiple-choice options are intentionally hidden during normal flashcard practice.
- **Quiz Mode:** multiple-choice questions can be answered directly; written questions accept typed answers; matching questions can be self-checked.
- **Review Missed:** after a session, Study Quest can immediately run the cards marked for review.

## Portable decks

Use **Export Deck** during Validation Review to save a `.studyquest.json` file. On another device, use **New Deck → Advanced → import a saved StudyCards JSON file**.

## Privacy

Practice-test images remain in the user's ChatGPT conversation. Study Quest only receives the structured JSON the user chooses to paste/import. Decks remain in the browser's local storage unless the user exports them.


## v1.3.0

- Interactive matching Quiz Mode with randomized dropdown choices.
- Immediate quiz feedback before advancing.
- Dedicated Review Missed flow and persistent missed-card progress.
- Delete Deck with explicit confirmation.
- Study/Quiz question state is reset cleanly between cards.
- StudyCards format remains v1.2; app version is v1.3.0.
