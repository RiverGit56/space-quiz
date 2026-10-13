# Copilot Instructions for Space Quiz

## Architecture & Project Structure

- **Self-Contained Web Application**: All markup, CSS styling, state logic, questions data, and event handling reside in a single file (`index.html`). No build tooling, bundlers, external CDNs, or runtime dependencies are used.
- **State Management**:
  - `questions`: Array of objects containing `question`, `options` (4 strings), and `answerIndex` (0-3).
  - Runtime variables: `currentQuestionIndex`, `score`, `answered`, and `autoAdvanceTimer`.
  - Screens: `#quizScreen` (questions, options, and feedback banner) and `#resultsScreen` (score circle, accuracy percentage, stats grid, and restart trigger).
- **Theme System**:
  - CSS custom properties defined on `:root` and responsive to `@media (prefers-color-scheme: light)` by default.
  - Manual overrides toggled via `data-theme="dark"` or `data-theme="light"` on `<html>`.

## Build, Test, and Verification

- **Preview**: Open `index.html` directly in any web browser (`file:///.../index.html`) or via the integrated browser canvas.
- **Testing**:
  - Run browser-level smoke tests via the integrated browser canvas or standard browser console.
  - Test keyboard navigation (`A`-`D` or `1`-`4` for options, `Enter`/`Space` to advance/restart, and `R` to restart).
  - Verify accessibility and theme toggle persistence (`#themeToggleBtn`).

## Key Conventions

- **Zero External Dependencies**: Keep the application entirely self-contained within `index.html`. Do not introduce npm packages, remote script tags, or web fonts unless explicitly requested.
- **Telemetry / Mission-Control Aesthetic**: The header (`h1.title`) uses a monospace font stack (`ui-monospace, SFMono-Regular, ...`), an active blinking beacon (`.telemetry-beacon`), and a status indicator (`SYS:ONLINE`). Retain this styling when modifying header elements.
- **Animation Patterns**:
  - Correct answers apply `.correct` with `correctPulse` animation and display `✓`.
  - Wrong answers apply `.wrong` with `shake` animation, display `✕`, and simultaneously reveal the correct choice with `.correct`.
  - Keep button focus indicators visible via `:focus-visible`.
