# ADR 001: Adoption of Vanilla JavaScript for Frontend Development

*   **Status**: Accepted
*   **Date**: 2025-11-18
*   **Deciders**: Development Team

## Context
The "Bin Day Assistant" is a Progressive Web App (PWA) designed to provide users with timely information about their waste collection schedules. The application's primary user base will access the service via mobile devices, often under varying network conditions. The functional requirements for the user interface are relatively straightforward, involving a multi-step wizard for address selection, a dashboard for viewing collection dates, and settings for subscription management.

We needed to select a frontend technology stack that aligns with our goals of high performance, maintainability, and rapid delivery, while minimizing unnecessary complexity. We evaluated using popular Single Page Application (SPA) frameworks such as React, Vue.js, and Angular against using standard, "Vanilla" JavaScript (ES6+).

## Decision
We have decided to build the frontend of the Bin Day Assistant using **Vanilla JavaScript (ES6 Modules)**, without the inclusion of a heavy component-based framework like React or Vue.

## Consequences

### Positive Consequences
*   **Performance**: By avoiding the runtime overhead and large bundle sizes associated with frameworks, we achieve near-instant load times and optimal Time to Interactive (TTI). This is critical for a PWA intended for quick, transient interactions on mobile networks.
*   **Simplicity**: The application's state management needs are modest. Direct DOM manipulation and standard Event Listeners are sufficient to handle the UI logic without the cognitive load or boilerplate code required by state management libraries (e.g., Redux, Context API).
*   **Longevity & Stability**: Standard ES6 modules are natively supported by all modern browsers. This approach minimizes "dependency rot" and ensures the code remains runnable for years without requiring frequent updates to build tools or framework versions.
*   **Reduced Build Complexity**: While we use Vite for bundling, the build process is significantly simpler and faster without the need for transpiling JSX or managing complex framework-specific plugins.

### Negative Consequences
*   **Scalability Limits**: As the application grows in complexity, manual DOM manipulation can become cumbersome and harder to maintain compared to the declarative component models of frameworks. If the UI requirements expand significantly, we may need to refactor or introduce a lightweight library.
*   **Developer Experience**: We forgo the ecosystem of pre-built components and developer tools (like React DevTools) that speed up development for complex interfaces. We must implement our own patterns for reusable UI elements.
*   **State Synchronization**: We must be disciplined in keeping the DOM in sync with the application state, as we do not have a virtual DOM or reactive binding system to handle this automatically.
