# Project Report: Unit Testing and Test-Driven Development in React

## 1. Title
**Write Unit Tests and Apply Test-Driven Development (TDD) to a React Application**

## 2. Abstract
This project demonstrates unit testing and test-driven development by building TaskFlow, a small React task manager. The application supports creating, completing, filtering, and deleting tasks. Vitest runs the tests, while React Testing Library verifies observable UI behavior. The project illustrates how automated tests help catch regressions and support safer refactoring.

## 3. Problem Statement
When a JavaScript interface is developed without tests, small changes can unintentionally break existing behavior. Manual testing is repetitive and may miss edge cases such as blank input, incorrect filtering, or task-count errors. The objective is to build a working React application and use automated tests as an ongoing specification of expected behavior.

## 4. Objectives
- Understand unit testing and the TDD cycle.
- Write tests for utility functions and React components.
- Verify expected and edge-case behavior automatically.
- Use tests to reduce regressions when implementation changes.
- Demonstrate an application with a simple, accessible interface.

## 5. Technology Stack
- **React:** UI components and state management.
- **JavaScript (ES modules):** application logic.
- **Vite:** development server and production bundler.
- **Vitest:** test runner and assertions.
- **React Testing Library:** tests UI behavior from a user's perspective.
- **user-event:** realistic keyboard and mouse interactions in tests.
- **jsdom:** browser-like DOM environment for tests.

## 6. System Modules
1. **Task form:** accepts a task title, trims whitespace, and reports invalid empty submissions.
2. **Task operations:** creates tasks, toggles completion, and deletes tasks.
3. **Task filters:** displays all tasks, only active tasks, or only completed tasks.
4. **Progress summary:** displays total/completed/remaining counts and a completion percentage.
5. **Automated test suite:** checks utility functions, form behavior, and end-to-end-like UI interactions at the component integration level.

## 7. Test-Driven Development Methodology
TDD uses a repeating three-stage cycle:

1. **Red:** write a test for a requirement and run it; it should fail because the behavior is not implemented yet.
2. **Green:** write the smallest implementation that makes the test pass.
3. **Refactor:** improve structure and readability without changing expected behavior; rerun tests.

For example, the blank-task requirement starts with a test that expects no task to be added and an accessible validation message. The form then implements the guard condition. The test is run again to confirm the behavior.

## 8. Test Cases
| ID | Test case | Expected result |
|---|---|---|
| UT-01 | Create a task with surrounding whitespace | Title is trimmed and task starts incomplete |
| UT-02 | Create a task with only whitespace | Validation error is thrown by the utility |
| UT-03 | Filter all tasks | All tasks are returned |
| UT-04 | Filter active tasks | Completed tasks are excluded |
| UT-05 | Filter completed tasks | Only completed tasks are returned |
| UT-06 | Calculate task statistics | Total, completed, and remaining counts are correct |
| CT-01 | Submit a valid form | Callback receives the trimmed title and input clears |
| CT-02 | Submit a blank form | Error is shown and callback is not called |
| IT-01 | Add a task through the UI | New task appears and total count increases |
| IT-02 | Complete a task | Checkbox state updates and completed filter includes it |
| IT-03 | Choose active filter | Completed items are hidden |
| IT-04 | Delete a task | Selected task disappears |
| IT-05 | Clear completed tasks | Completed tasks are removed |
| IT-06 | Select a filter with no results | Helpful empty state is displayed |

## 9. How to Execute the Tests
From the project root:
```bash
npm install
npm run test:run
npm run test:coverage
npm run build
```
The test command reports passed/failed cases in the terminal. The coverage command generates a coverage report, including an HTML report under `coverage/`.

## 10. Expected Outcome
The application should allow a user to manage a short task list, and the automated suite should verify the specified behavior. Tests are repeatable and can be run after each code change. Run the commands above on the target machine and record the actual output in the submission; this report intentionally does not claim a test count or coverage percentage before execution in that environment.

## 11. Limitations
- Tasks are stored in component state only and are not persisted after refresh.
- Tests run in jsdom and do not replace full browser/device acceptance testing.
- No backend, authentication, or multi-user synchronization is included because they are not needed for the core TDD demonstration.

## 12. Future Enhancements
- Persist tasks in local storage or a database.
- Add task due dates, priorities, and search.
- Add end-to-end browser tests with Playwright.
- Add CI so tests run automatically on every pull request.

## 13. Conclusion
TaskFlow provides a practical example of unit testing and TDD in a React application. Separating task utilities from UI components makes the logic easier to test, while interaction tests validate that the visible interface behaves as intended. The Red–Green–Refactor cycle provides a disciplined way to implement features and prevent regressions.
