# Test App — CLI Quiz

## Project description

Test App is a small command-line quiz application built with Node.js. It loads quiz questions from data/questions.json and runs an interactive quiz in the terminal. The project is organized with simple modules for coloring output, handling user input, and quiz logic, making it easy to extend or reuse.

## File structure

- data/
  - questions.json — quiz questions and answers
- src/
  - colors.js — utilities for colored terminal output
  - input.js — input handling for the CLI
  - quiz.js — quiz logic and flow
- index.js — application entry point
- package.json — project metadata and dependencies

## Prerequisites

- Node.js (recommend v14+)
- npm (or yarn)

## Setup instructions

1. Clone the repository (or download the project files):

   git clone <repository-url>
   cd test-app

2. Install dependencies:

   npm install

   or with yarn:

   yarn install

## How to run the project

You can run the app directly with Node or via an npm script.

- Directly with Node:

  node index.js

- With npm (if a start script is present in package.json):

  npm start

The application will read questions from `data/questions.json` and launch an interactive quiz in your terminal.

## Questions format

Questions are stored in `data/questions.json`. The expected structure is a JSON array of question objects. A typical object may look like:

```
{
  "question": "What is the capital of France?",
  "options": ["Paris", "Berlin", "Madrid", "Rome"],
  "answer": 0
}
```

- `question`: the question text
- `options`: array of possible answers
- `answer`: index (0-based) of the correct option

You can add, remove, or modify entries in this file to change the quiz content.

## Key features

- Simple CLI quiz experience
- Questions loaded from a JSON file for easy customization
- Colored terminal output (via src/colors.js) for better readability
- Modular code: separate files for input handling and quiz logic to simplify maintenance and extension

## Extending the project

- Add new question types (true/false, open-ended)
- Add scoring persistence or high-score leaderboard
- Add configuration options (number of questions, categories)

## Troubleshooting

- If the app doesn't start, ensure you have a compatible Node.js version installed and that dependencies were installed successfully (`npm install`).
- If questions don't appear, verify the JSON in `data/questions.json` is valid and properly formatted.

## License & Contribution

This is a small demo project. Feel free to fork, modify, and open pull requests or issues if you have suggestions.

---

If you need the README adjusted to match exact package.json scripts or to include example output, provide the contents of `package.json` and `index.js`, and I will update the README accordingly.