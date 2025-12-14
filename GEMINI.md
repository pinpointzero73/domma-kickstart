## Project Overview

This project is a "kickstart" template for the Domma JavaScript framework. It's a single-page, dependency-free landing page that demonstrates how to use Domma's core features.

**Main Technologies:**

*   **Domma:** A zero-dependency JavaScript framework that provides:
    *   jQuery-compatible DOM manipulation (`$`).
    *   Lodash-compatible utility functions (`_`).
    *   A rich library of UI components (navbar, modals, tabs, etc.).
    *   A responsive grid system.
    *   A theming system with light/dark modes and color variants.
    *   Helper modules for local storage (`S`), dates (`D`), and reactive models (`M`).
*   **HTML5 & CSS3:** The project uses modern HTML and CSS for structure and styling.

## Building and Running

This project does not require a build process. To run it, simply open the `index.html` file in a web browser.

**Development:**

*   The main application logic is in `includes/index.js`.
*   Custom styles can be added to `css/custom.css`.
*   The Domma framework files (CSS and JS) are located in the `/dist` directory.

While there is no `package.json`, the `index.html` file mentions `npm run build`. This suggests that for a more complex project, you might introduce a build step (e.g., for minification, concatenation, or using a package manager).

## Development Conventions

The codebase is well-structured and follows these conventions:

*   **IIFE:** The main JavaScript code in `includes/index.js` is wrapped in an Immediately Invoked Function Expression (IIFE) to prevent polluting the global namespace.
*   **'use strict';**: Strict mode is enabled to catch common coding mistakes.
*   **Clear Sections:** The JavaScript code is divided into clear, numbered sections for different functionalities (Navbar, Basic Setup, Grid Logic, etc.).
*   **Comments:** The code is extensively commented to explain how to use Domma's features and how to customize the template.
*   **Namespaces:** Domma uses specific namespaces to organize its API:
    *   `Domma` or `$`: For DOM manipulation.
    *   `_`: For utility functions.
    *   `M`: For reactive models.
    *   `D`: For date manipulation.
    *   `S`: For local storage.
