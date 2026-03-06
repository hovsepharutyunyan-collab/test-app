# quiz-cli

An interactive command-line quiz game for learning JavaScript. Pick a category, choose how many questions to answer, and get instant feedback with explanations and a final score.

---

## Table of Contents

- [Features](#features)  
- [Requirements](#requirements)  
- [Installation](#installation)  
- [Usage](#usage)  
  - [CLI flow](#cli-flow)  
  - [Example commands](#example-commands)  
- [Data format & how to add / edit questions](#data-format--how-to-add--edit-questions)  
- [Project structure](#project-structure)  
- [Scripts](#scripts)  
- [Contributing](#contributing)  
- [License](#license)  
- [Suggestions & future improvements](#suggestions--future-improvements)

---

## Features

- Interactive CLI quiz experience.
- Multiple categories (javascript, nodejs, general).
- Choose number of questions (All, 3, 5).
- Immediate feedback per question (correct/incorrect) with optional explanations.
- Score summary and review of incorrect answers.
- Colorized output and simple progress bar for better UX.

---

## Requirements

- Node.js v18.0.0 or newer (package.json specifies engines: node >=18.0.0)
- npm (for installing dependencies, if any)

---

## Installation

1. Clone the repository
   ```bash
   git clone https://github.com/<your-org>/test-app.git
   cd test-app
   ```
2. Install dependencies (if any are added in package.json)
   ```bash
   npm install
   ```
3. Ensure your Node.js version is >= 18.0.0:
   ```bash
   node -v
   ```

---

## Usage

Start the quiz from the repository root.

### CLI flow

1. Run the program.
2. Select a category from the list (e.g. javascript, nodejs, general).
3. Select how many questions to answer (All / 3 / 5).
4. For each question:
   - Read the question and options.
   - Select an answer.
   - See immediate feedback (correct/incorrect) and explanation if provided.
   - A progress bar updates as you advance.
5. After all selected questions, view your score and optionally review incorrect answers.
6. Choose whether to replay or exit.

### Example commands

Run with Node directly:
```bash
node index.js
```

Or via npm script:
```bash
npm start
```

Run tests (project includes a `test` script that runs Node's test runner):
```bash
npm test
```

---

## Data format & how to add / edit questions

Questions are stored in `data/questions.json`. The top-level structure is:

{
  "categories": {
    "<categoryId>": {
      "name": "<Human readable name>",
      "questions": [
        {
          "question": "<Question text>",
          "options": ["<option1>", "<option2>", "..."],
          "answer": <index_of_correct_option>,
          "explanation": "<optional explanation text>"
        },
        ...
      ]
    },
    ...
  }
}

Example snippet (add to `data/questions.json` following its existing structure):
```json
{
  "categories": {
    "javascript": {
      "name": "JavaScript",
      "questions": [
        {
          "question": "Which method creates a new array with the results of calling a provided function on every element in this array?",
          "options": ["forEach", "map", "filter", "reduce"],
          "answer": 1,
          "explanation": "Array.prototype.map returns a new array containing the results of applying the callback to each element."
        }
      ]
    }
  }
}
```

Guidelines for adding/editing:
- Keep `answer` as a zero-based index into the `options` array.
- `explanation` is optional but recommended for learning value.
- Use a unique category key (e.g., `nodejs`, `general`) and provide a `name` for display.
- Keep JSON valid (no trailing commas).

---

## Project structure

A brief overview of important files and folders:

- index.js — CLI entrypoint. Loads `data/questions.json`, prompts category and question count, and runs the quiz using the Quiz class and input helpers.
- package.json — Project metadata and npm scripts (start, test). Specifies Node engine >=18.0.0 and license MIT.
- data/questions.json — Quiz data. Contains categories and arrays of question objects.
- src/quiz.js — Quiz class: handles question shuffling, asking questions, progress bar, score calculation, and showing results/review.
- src/input.js — Readline helpers: createInterface, prompt, select, confirm, pressEnter.
- src/colors.js — ANSI color helpers for colored CLI output.

(If you add tests, docs, or other resources, list them here as well.)

---

## Scripts

Available npm scripts (from package.json):

- start: node index.js
  - Launches the quiz CLI.
- test: node --test
  - Runs Node's built-in test runner (useful if/when tests are added).

Run a script:
```bash
npm run start
npm run test
```
Or the shortcuts:
```bash
npm start
npm test
```

---

## Contributing

Thank you for considering contributing! A simple workflow:

1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feat/my-feature
   ```
3. Make your changes. If you modify quiz data, update `data/questions.json` following the format above.
4. Run the app locally to verify behavior:
   ```bash
   npm start
   ```
5. Commit and push your branch, then open a Pull Request describing your changes.

Notes:
- Keep changes focused and include tests when adding logic (you can use Node's test runner invoked via `npm test`).
- For data changes, prefer small, targeted additions with clear question phrasing and explanations.

---

## License

This project is licensed under the MIT License.

A short notice you can include in a LICENSE file:

MIT License

Copyright (c) [year] [copyright holders]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...

(Include a full LICENSE file when committing. The package.json already indicates "MIT".)

---

## Suggestions & future improvements

Ideas to make the project even better:
- Add automated CI (GitHub Actions) to run tests and linting on PRs.
- Introduce unit tests for Quiz logic (score calculation, shuffling, edge cases).
- Add input validation and more robust error handling.
- Add screenshots or an animated GIF in the README demonstrating the CLI flow.
- Support more formats (YAML, external JSON path) or allow loading custom question files via CLI flags.
- Add localization support for different languages.
- Improve UX with timers, difficulty levels, or persistent score tracking.

---

If you need help editing the questions file or want an example PR to add a new category, tell me the category and a couple of sample questions and I can prepare the JSON and a recommended commit/PR message.