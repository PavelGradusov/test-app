# Programming Quiz Questions (JSON)

A small, structured collection of programming quiz questions stored as JSON. The dataset covers JavaScript basics, Node.js fundamentals, and general programming concepts — each question includes options, the index of the correct answer, and a short explanation. The data is intended to be consumed by quiz apps, tutorials, or CLI/GUI tools.

## Key Features
- Categorized question banks: `javascript`, `nodejs`, `general`
- Each question contains:
  - `question` (string)
  - `options` (array of strings)
  - `answer` (zero-based index into `options`)
  - `explanation` (string)
- Plain JSON format — framework- and language-agnostic
- Ready to import in Node.js or any language that reads JSON

## Installation
This repository contains only data. To use it locally:
1. Clone the repository:
   git clone <repo-url>
2. No build step or dependencies required to read the JSON.

Optional: Node.js (recommended for the usage examples below).

## Usage / How to run
You can load and use the dataset in any environment that can parse JSON. Examples below use Node.js.

- Quick inspect with Node:
  node -e "console.log(JSON.stringify(require('./data/questions.json'), null, 2))"

- Simple Node script (example):
  1. Create `show.js`:
     const data = require('./data/questions.json');
     const cat = data.categories.javascript;
     console.log(`# Category: ${cat.name}`);
     cat.questions.forEach((q, i) => {
       console.log(`\n${i + 1}. ${q.question}`);
       q.options.forEach((opt, j) => console.log(`  ${String.fromCharCode(65 + j)}. ${opt}`));
       console.log(`  Answer: ${String.fromCharCode(65 + q.answer)}`);
       console.log(`  Explanation: ${q.explanation}`);
     });
  2. Run:
     node show.js

- Reading the file in other languages:
  Use your language's JSON parser to read `data/questions.json` and iterate categories/questions.

## Examples (textual)
Sample entry (rendered):

Category: JavaScript Basics

1. What keyword is used to declare a constant in JavaScript?
  A. var
  B. let
  C. const
  D. define
  Answer: C
  Explanation: The 'const' keyword declares a block-scoped constant that cannot be reassigned.

Another sample (JSON excerpt):
{
  "question": "What does API stand for?",
  "options": ["Application Programming Interface", "Advanced Program Integration", "Automated Protocol Interface", "Application Process Integration"],
  "answer": 0,
  "explanation": "API stands for Application Programming Interface - a set of protocols for building software."
}

## File structure
- data/
  - questions.json      — main dataset (categories → questions)
- README.md             — this file

Top-level keys in `data/questions.json`:
- `categories`: object keyed by category slug (`javascript`, `nodejs`, `general`)
  - each category has:
    - `name`: display name
    - `questions`: array of question objects

Question object fields:
- `question` (string)
- `options` (array[string])
- `answer` (integer; zero-based index into `options`)
- `explanation` (string)

## Contribution
Contributions are welcome. Suggested workflow:
- Fork the repo
- Add or edit questions in `data/questions.json`
- Maintain the structure shown above
- Keep `answer` as a zero-based index
- Provide clear, concise `explanation` for each question
- Submit a pull request with a brief description of changes

When adding questions:
- Ensure options are in the intended order and the `answer` index matches the correct option
- Avoid duplicate questions
- Group new questions under an existing category or add a new category object with a unique slug and `name`

## Noteworthy implementation details / Notes
- The dataset is intentionally minimal and dependency-free (plain JSON).
- The `answer` field is zero-based (0 = first option).
- The JSON structure is stable and easy to transform for use in web apps, CLI quizzes, or mobile apps.
- No runtime code or package manifest (package.json) is included; examples assume a Node.js runtime only for demonstration.

## Dependencies
- None required to use the data.
- Node.js (optional) for the usage examples shown above.

## License
No LICENSE file is included in the repository. You may use the data under the terms you prefer. If you want a permissive license, consider adding an MIT license file (COPYING/ LICENSE) to the repository.

If you want, I can generate a sample MIT LICENSE file and a simple Node.js CLI loader for these questions.
