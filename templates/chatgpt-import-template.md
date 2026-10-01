# Study Quest — ChatGPT Image Import Template v1.2

You are converting one or more photographs/screenshots of a child's school practice test into a Study Quest deck.

## Instructions
1. Read **ALL attached images** before producing output. They are pages of the same test unless the user says otherwise.
2. Preserve the original question meaning. Do not invent missing questions, choices, or source answers.
3. Extract every study-worthy question you can identify, in the original order when possible.
4. For multiple-choice questions, preserve **ALL choices** and identify the correct answer.
5. For matching questions, use `type: "matching"` and preserve every correct pair in `pairs`. Do not put "See pairs" in `answer`; the pairs are the answer.
6. For written-answer questions, use `type: "written"`. If a correct answer is printed on the worksheet or answer key, preserve it faithfully. If a student's handwritten answer is present, identify it as the student's answer. If no answer is supplied and you must infer one from the question/material, do so only when reasonably clear and mark the source as `inferred`.
7. Use `true_false` for true/false questions.
8. If a question is unreadable or genuinely ambiguous, include it when possible and explain the uncertainty in `notes` rather than inventing details.
9. Do not grade the student's handwritten answer unless the source provides enough information to do so reliably.
10. Return **only valid JSON**. Do not wrap it in Markdown fences and do not add commentary before or after the JSON.
11. Use the following `answer_source` values:
   - `source` = answer is explicitly present in the supplied worksheet/source material
   - `student` = answer is the student's handwritten response
   - `teacher_key` = answer is explicitly supplied by a teacher/answer key
   - `inferred` = answer was inferred from the question/material rather than explicitly supplied
   - `unknown` = source cannot be determined
12. For inferred answers, add a short `notes` value explaining that the answer was inferred.

## Output schema
{
  "format": "StudyCards",
  "version": "1.0",
  "title": "string",
  "subject": "string",
  "cards": [
    {
      "type": "multiple_choice",
      "question": "string",
      "choices": ["string", "string"],
      "answer": "string",
      "answer_source": "source | student | teacher_key | inferred | unknown",
      "notes": "string"
    },
    {
      "type": "matching",
      "question": "string",
      "pairs": [
        {"left": "string", "right": "string"}
      ],
      "answer_source": "source | student | teacher_key | inferred | unknown",
      "notes": "string"
    },
    {
      "type": "written",
      "question": "string",
      "answer": "string",
      "answer_source": "source | student | teacher_key | inferred | unknown",
      "notes": "string"
    },
    {
      "type": "true_false",
      "question": "string",
      "answer": "True | False",
      "answer_source": "source | student | teacher_key | inferred | unknown",
      "notes": "string"
    }
  ]
}

## Final checks before responding
- Confirm every attached page was read.
- Preserve every useful multiple-choice option.
- Confirm matching questions contain the actual pairs.
- Do not silently turn an inferred answer into a source answer.
- Return JSON only.
