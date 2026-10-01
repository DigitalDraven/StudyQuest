# Study Quest — ChatGPT Image Import Template v1.0

You are converting one or more photographs/screenshots of a child's school practice test into a Study Quest deck.

## Instructions
1. Read ALL attached images before producing output. They are pages of the same test unless the user says otherwise.
2. Preserve the original question meaning. Do not invent missing questions or answers.
3. Extract every study-worthy question you can identify.
4. For multiple-choice questions, preserve ALL choices and identify the correct answer.
5. For matching questions, create `type: "matching"` and preserve every correct pair in `pairs`.
6. For written-answer questions, create `type: "written"` and give the expected/correct answer. If the worksheet supplies an answer, use it. If the answer is not shown, provide the most defensible answer from the question and clearly flag uncertainty in `notes`.
7. Use `true_false` for true/false questions.
8. If a question is unreadable or genuinely ambiguous, include it but add a concise `notes` field explaining what needs parent review.
9. Do not include student handwriting as the correct answer unless it is clearly the teacher-provided answer key. The goal is to create study material from the practice test.
10. Return ONLY valid JSON. No Markdown fences. No commentary before or after the JSON.

## Required output format
{
  "format": "StudyCards",
  "version": "1.0",
  "title": "Short descriptive deck title",
  "subject": "Science",
  "cards": [
    {
      "type": "multiple_choice",
      "question": "Question text",
      "choices": ["Choice A", "Choice B", "Choice C", "Choice D"],
      "answer": "Correct choice text",
      "notes": "Optional uncertainty note"
    },
    {
      "type": "written",
      "question": "Question text",
      "answer": "Expected answer",
      "notes": "Optional uncertainty note"
    },
    {
      "type": "matching",
      "question": "Match each item with its correct answer.",
      "pairs": [
        {"left": "Item", "right": "Answer"}
      ],
      "answer": "See pairs",
      "notes": "Optional uncertainty note"
    },
    {
      "type": "true_false",
      "question": "Statement",
      "answer": "True"
    }
  ]
}

## Important
- Do not output anything except the JSON object.
- Keep all multiple-choice choices even though Study Quest's default flashcard view only shows the correct answer after reveal.
- If several images are attached, combine them into one deck in page order.
- Do not duplicate a question that appears across images.
