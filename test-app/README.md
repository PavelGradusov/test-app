# Quiz CLI

> An interactive command-line quiz game for learning JavaScript and Node.js concepts.

## Overview

Quiz CLI is a small, educational command-line application written in modern JavaScript (ES Modules) that helps users test and learn programming concepts. It features multiple categories of questions (JavaScript, Node.js, General Programming), a shuffleable question order, per-question explanations, a progress bar, and a results summary with review of incorrect answers.

The project demonstrates Node.js features such as async/await, Promises, file system operations, readline-based input handling, classes, and simple ANSI-based terminal styling.

<!-- TOC -->

- [Overview](#overview)
- [Setup](#setup)
- [Usage](#usage)
- [File structure](#file-structure)
- [Development](#development)
- [Contributing](#contributing)
- [License](#license)

## Setup

Prerequisites:

- Node.js >= 18.0.0 (uses ES modules and the built-in node: namespace)

Quick start:

1. Clone the repository and change into the project directory:

   git clone <repo-url>
   cd test-app

2. (Optional) Install dependencies. This project has no external dependencies, but running npm install is harmless and prepares the project if dependencies are added later:

   npm install

3. Run the quiz:

   npm start

Or directly with Node.js:

   node index.js

You can also make the CLI executable and run it directly:

   chmod +x index.js
   ./index.js

Customizing questions:

- Questions are stored in data/questions.json. You can add categories or questions using the existing JSON structure (see File structure section).

## Usage

When you run the app you'll be presented with a simple interactive menu:

- Choose a category (e.g., "JavaScript Basics", "Node.js Fundamentals").
- Choose how many questions to attempt (All, 3, or 5 when available).
- For each question, pick the answer by entering its number.
- Press Enter to proceed between questions when prompted.
- After the quiz you'll see a results summary with score, percentage, a performance message, and a review of incorrect answers.

Example session (abridged):

1. Start the app:

   npm start

2. Select a category by entering the option number.
3. Select number of questions.
4. Answer questions by typing the number of the option and pressing Enter.
5. When the quiz ends, choose whether to play again (y/n).

Controls:

- Input is numeric for selections.
- Confirmations are entered as y/n.
- Press Enter when prompted to continue.

Note: The CLI uses simple text-based menus; there is no network activity or external API usage.

## File structure

Top-level (test-app):

- index.js            - Main CLI entry point (executable via node)
- package.json        - Project metadata (name: quiz-cli, node engine >=18)
- README.md           - (This file)
- data/
  - questions.json    - JSON file containing categories and questions
- src/
  - colors.js         - ANSI color helpers and convenience functions
  - input.js          - readline-based input helpers (prompt, select, confirm)
  - quiz.js           - Quiz class: game logic, shuffling, progress, results

Each question object in data/questions.json follows this shape:

{
  "question": "...",
  "options": ["opt1", "opt2", ...],
  "answer": <index_of_correct_option>,
  "explanation": "optional explanation text"
}

You can add new categories under the top-level "categories" object in data/questions.json.

## Development notes & additional info

Architecture:

- index.js ties everything together: loads questions, shows a banner, handles the main loop, and uses the Quiz class to run rounds.
- src/input.js provides reusable prompts and selection utilities built on node:readline.
- src/quiz.js contains the core Quiz class implementing shuffle (Fisher-Yates), per-question flow, scoring, progress bar, and result reporting.
- src/colors.js contains small helpers to colorize terminal output using ANSI escape codes.

Testing:

- package.json includes a test script: "test": "node --test" but no dedicated test files are present. You can add Node.js built-in tests (using the test runner) under a test/ directory and run npm test.

Extending questions:

- Add or modify categories in data/questions.json. The app reads the file at runtime, so changes are immediate.

Contribution & Code style:

- The code uses modern ES module syntax (import/export). Aim for Node.js >= 18.
- Keep functions small and well-documented. The project is small and intended for learning; contributions should focus on clarity and educational value.

### License

This project is released under the MIT License (see package.json). By contributing you agree to license your changes under MIT.

<!-- END -->
