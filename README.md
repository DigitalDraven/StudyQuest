# Study Quest v1.0

A no-API, client-side flashcard web app for turning school practice tests into study decks.

## Architecture
- GitHub Pages/static hosting compatible
- No backend
- No API keys
- ChatGPT handles image understanding using `templates/chatgpt-import-template.md`
- Study Quest imports the resulting `StudyCards 1.0` JSON
- Decks are stored locally in the browser with localStorage
- GSAP is used for UI entrance animation; the core app is dependency-light

## Use
1. Host this folder on GitHub Pages or any static web host.
2. Open `templates/chatgpt-import-template.md` and give it to ChatGPT with one or more practice-test images.
3. Ask ChatGPT to return only valid JSON using the template.
4. Save the response as `something.json`.
5. In Study Quest choose **New Deck → Import StudyCards**.
6. Validate/edit the extracted questions and answers.
7. Save & Study.

## Important privacy note
The app itself does not upload images or decks anywhere. ChatGPT receives the images when the parent chooses to attach them to the ChatGPT conversation.

## Roadmap
- IndexedDB instead of localStorage for larger decks
- PWA/offline install
- richer matching-card UI
- practice-test mode using the preserved multiple-choice options
- missed-card persistence across sessions
- sound/haptics and richer GSAP transitions
- optional Three.js scene as an ambient visual layer
