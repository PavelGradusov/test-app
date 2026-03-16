# Quiz CLI

## Project description

Quiz CLI is a small interactive command-line quiz game built with Node.js. It is designed as a learning/demo project and showcases modern JavaScript features such as ES modules, async/await, Promises, classes, and file system operations. The app reads question data from a JSON file and runs an interactive terminal quiz with colored output and progress tracking.

This repository is intended for learning and for running a simple, dependency-free CLI quiz.

## Setup instructions

1. Prerequisites
   - Node.js v18.0.0 or newer (the package.json specifies "engines": { "node": ">=18.0.0" }).

2. Clone the repository (or copy the `test-app` folder into your environment).

   Example:
   ```bash
   git clone <repo-url>
   cd <repo-folder>/test-app
   ```

3. Install dependencies
   - This project uses only Node built-ins and has no external dependencies. Running npm install is optional but harmless if you plan to add dev tools.
   ```bash
   # optional
   npm install
   ```

## How to run the project

From the `test-app` directory:

- Using npm script:
  ```bash
  npm start
  ```
  This runs `node index.js` as defined in package.json.

- Or directly with Node:
  ```bash
  node index.js
  ```

- On UNIX-like systems you can make the launcher executable and run it:
  ```bash
  chmod +x index.js
  ./index.js
  ```

When the CLI starts it displays a banner, prompts you to choose a category (if available), then walks you through questions. Use the numeric choices to select options. At the end, your score and explanations for answers are shown.

## Key features

- Interactive, terminal-based quiz experience
- Category-based questions (data stored in JSON under `data/questions.json`)
- Colored and formatted terminal output (ANSI codes, provided in `src/colors.js`)
- Progress display and scoring
- Explanations for answers
- Implemented with modern JavaScript language features:
  - ES modules (import/export)
  - Async/await and Promises
  - File system operations (reading JSON data)
  - Readline-based user input handling (prompts, selection)
  - Classes and OOP (Quiz class)
  - Utility functions (shuffling, progress rendering)
- No external dependencies required

## Project structure (overview)

- index.js — entry point that loads question data, displays banner, and coordinates the quiz flow
- package.json — project metadata and npm scripts
- data/questions.json — question data organized by categories (category name, questions array)
- src/
  - colors.js — small helper to colorize terminal output
  - input.js — readline-based input helpers (prompt, select, etc.)
  - quiz.js — Quiz class and game logic

## Adding or editing questions

The questions are stored in `data/questions.json`. Each category follows a structure similar to:

```json
{
  "categories": {
    "javascript": {
      "name": "JavaScript Basics",
      "questions": [
        {
          "question": "What keyword is used to declare a constant in JavaScript?",
          "options": ["var", "let", "const", "define"],
          "answer": 2,
          "explanation": "The 'const' keyword declares a block-scoped constant that cannot be reassigned."
        }
      ]
    }
  }
}
```

- `question`: string
- `options`: array of strings
- `answer`: index of correct option (0-based)
- `explanation`: optional string shown after answering

Add new categories as keys under `categories` and provide `name` and `questions` arrays.

## Contributing

- Feel free to submit improvements, additional question categories, or fixes.
- Keep the project dependency-free where possible.

## License

This project uses the MIT license (see package.json).

## Troubleshooting

- If the CLI does not start, ensure you are running Node v18+:
  ```bash
  node -v
  ```
- Run the app from the `test-app` directory (so the relative path to `data/questions.json` is correct), or use an absolute path in `index.js` if moving files.

If you want the full contents of any source file (for review or modification), request the path (for example `test-app/src/quiz.js`) and the file can be provided in chunks.
