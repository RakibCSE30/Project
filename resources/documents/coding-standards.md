# Coding & Docstring Standards

To maintain code quality, readability, and consistency across the **Smart Question Bank** project, all developers must adhere to the following coding standards.

---

## 1. Naming Conventions

We follow standard JavaScript/TypeScript naming conventions:

* **Variables & Functions:** `camelCase` (e.g., `generateQuestion()`, `isValidUser`)
* **Classes & React Components:** `PascalCase` (e.g., `QuestionPaper`, `SidebarComponent`)
* **Database Tables & Columns:** `snake_case` (e.g., `question_banks`, `user_id`)
* **Constants:** `UPPER_CASE` (e.g., `MAX_RETRY_ATTEMPTS`, `JWT_SECRET`)

---

## 2. Code Comments & Docstrings Guide

Do not just write *what* the code does; explain *why* it does it if the logic is complex. We use standard **JSDoc** formatting for all functions.

### Example for Backend API Controller:
```javascript
/**
 * Generates a randomized question paper based on difficulty rules.
 * @param {string} courseId - The unique identifier of the course.
 * @param {Object} dynamicRules - The difficulty distribution (e.g., { easy: 0.4, hard: 0.6 }).
 * @returns {Promise<Object>} The generated question paper structure.
 * @throws {ValidationError} If inputs are invalid or out of bounds.
 */
async function generateAutoQuestionPaper(courseId, dynamicRules) {
    // Core logic goes here...
}