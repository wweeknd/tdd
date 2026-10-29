# TaskFlow — React Unit Testing and Test-Driven Development

A responsive task-management application built with React, Vite, Vitest, and React Testing Library. It demonstrates the **Red → Green → Refactor** TDD workflow with unit tests for pure functions, component tests, and application-level interaction tests.

## Features
- Add tasks with input validation and whitespace trimming
- Mark tasks complete/incomplete
- Filter all, active, and completed tasks
- Delete individual tasks or clear all completed tasks
- Live task count, completion percentage, progress bar, and empty states
- Responsive layout and accessible labels/feedback

> Demo note: tasks are held in React state and reset when the page is refreshed. Persistent storage is intentionally outside this assignment's core scope.

## Requirements
- Node.js 20+ recommended
- npm

## Run the project
```bash
npm install
npm run dev
```
Open the local URL printed by Vite (normally `http://localhost:5173`).

## Run tests
```bash
npm run test:run       # run the full test suite once
npm run test           # watch mode while developing
npm run test:coverage  # tests plus HTML/text coverage report
npm run build          # production build
```

## Test suite overview
| File | Type | What it verifies |
|---|---|---|
| `src/utils/tasks.test.js` | Unit | Task creation/validation, filtering, statistics, empty list |
| `src/components/TaskForm.test.jsx` | Component | Valid submit, trimming, clearing input, blank-input error |
| `src/App.test.jsx` | Integration | Initial UI, add, complete, filtering, delete, clear completed, empty state |

## Applying TDD
For each feature, write a failing test first (**Red**), implement the minimum code needed to pass (**Green**), then improve the implementation while keeping the suite green (**Refactor**).

Suggested example — task title validation:
1. **Red:** add a test expecting whitespace-only input not to call `onAddTask` and to display an error.
2. **Green:** add validation in `TaskForm` before invoking the callback.
3. **Refactor:** extract reusable task creation and filtering logic into `src/utils/tasks.js`; rerun the suite to guard against regressions.

The committed test files represent the test specifications and the current implementation is designed to satisfy them. To demonstrate the TDD cycle during a presentation, temporarily break one assertion or remove the relevant validation, run `npm run test:run` to show the failure, then restore the implementation and run it again.

## Project structure
```text
react-tdd-task-manager/
├── index.html
├── package.json
├── vite.config.js
├── README.md
├── PROJECT_REPORT.md
└── src/
    ├── App.jsx
    ├── App.test.jsx
    ├── main.jsx
    ├── styles.css
    ├── components/
    │   ├── TaskForm.jsx
    │   └── TaskForm.test.jsx
    ├── utils/
    │   ├── tasks.js
    │   └── tasks.test.js
    └── test/setup.js
```

## Troubleshooting
- If dependencies are missing, run `npm install` from the project folder.
- If a port is already in use, Vite will offer another local port.
- If the test environment reports dependency/version incompatibilities, use a current Node.js LTS release and reinstall dependencies (`rm -rf node_modules package-lock.json && npm install`).
