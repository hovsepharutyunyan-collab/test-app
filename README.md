# Quiz CLI

An interactive command-line quiz game for learning JavaScript and programming fundamentals.

---

## Project Overview

Quiz CLI is a small, dependency-free Node.js command-line application that presents multiple-choice quizzes organized by category. It's designed both as a simple educational tool and as an example project demonstrating modern JavaScript features such as ES modules, async/await, classes, and file-system operations.

Key features:
- Multiple categories (JavaScript, Node.js, General Programming)
- Select how many questions to answer (All / 3 / 5 when available)
- Visual progress bar and colored terminal output
- Immediate feedback with explanations and a final score summary
- No external dependencies — uses built-in Node.js modules

## Technologies & Requirements

- Node.js (v18.0.0 or newer)
- Uses ES Modules ("type": "module" in package.json)
- No external NPM dependencies

## Installation

1. Clone the repository:

   git clone <repo-url>
   cd quiz-cli

2. Install (no dependencies required, but run to set up if you add packages):

   npm install

3. Ensure you have Node.js >= 18 installed:

   node -v

## Running the App

Start the quiz with:

   npm start

Or directly with Node:

   node index.js

How it works:
- Choose a category from the list
- Pick how many questions you want to answer
- Enter the number corresponding to your selected answer for each question
- Press Enter to continue between questions
- At the end you'll see your score, performance message, and a review of incorrect answers

## Usage Examples

- Run the app:
  npm start

- Walkthrough:
  1. Choose "JavaScript Basics"
  2. Select "3 questions"
  3. For each question, enter the number for the answer (e.g., `2`)
  4. Review the results and decide whether to play again

## Project Structure

- index.js - Entry point. Loads questions, handles main app loop and user interactions.
- package.json - Project metadata and scripts (start, test). Requires Node >= 18.
- data/questions.json - Quiz content (categories, questions, options, answers, explanations).
- src/
  - input.js - Console input helpers (prompt, select, confirm, pressEnter) using Node's readline.
  - quiz.js - Quiz game logic (Quiz class, shuffling, rendering progress, results).
  - colors.js - Small utility for ANSI terminal colors.
- .DS_Store - macOS metadata file (can be ignored or removed)

## Data Format (data/questions.json)

The questions file is a JSON object with a "categories" map. Each category looks like:

{
  "name": "Category Name",
  "questions": [
    {
      "question": "Question text",
      "options": ["opt A", "opt B", "opt C"],
      "answer": 0,               // zero-based index of correct option
      "explanation": "Optional explanation text"
    },
    ...
  ]
}

Add or edit categories and questions directly in this file to extend the quiz.

## Customization

- Add new categories or questions in `data/questions.json`.
- Change text styles or add new utility functions in `src/colors.js`.
- Modify the quiz flow or scoring rules in `src/quiz.js`.

## Development & Testing

- Start the app locally with `npm start`.
- `npm test` runs Node's built-in test runner (no tests included by default).

## License

MIT

## Contributing

Contributions are welcome — open an issue or submit a pull request. Keep changes small and focused (e.g., add new questions, improve UX, or add tests).

---

Enjoy learning and feel free to extend this project with more categories, questions, or features!