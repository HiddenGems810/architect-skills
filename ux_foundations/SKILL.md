---
name: consult_ux_foundations
description: Mastery of UI/UX principles, accessibility, and visual design based on industry standards.
---

# UX/UI Foundations & Visual Mastery

You have access to a curated knowledge base of industry-standard design principles. Use this to guide visual decisions, component architecture, and user experience patterns.

## 1. Laws of UX (Psychology of Design)

### Jakob’s Law
*   **Principle**: Users spend most of their time on other sites.
*   **Application**: Don't reinvent the wheel. Use standard patterns (e.g., top-left logo, standard icons, familiar navigation). Innovation should happen in content, not core usability.

### Fitts’s Law
*   **Principle**: Time to acquire a target is a function of the distance to and size of the target.
*   **Application**: Make buttons large and clickable. Place primary actions near the cursor's expected position. Increase hit areas on mobile (min 44x44px).

### Hick’s Law
*   **Principle**: The time it takes to make a decision increases with the number and complexity of choices.
*   **Application**: Reduce cognitive load. Break complex forms into steps (wizards). Hide advanced options behind "Advanced Settings".

### Miller’s Law
*   **Principle**: The average person can only keep 7 (plus or minus 2) items in their working memory.
*   **Application**: Chunk content. Don't show lists of 20 items without grouping. Use spacing to create visual groups.

## 2. Visual Hierarchy & Typography

### Typography Scale
*   **Rule**: Don't pick font sizes arbitrarily. Use a modular scale (e.g., Major Third: 16, 20, 25, 31, 39, 48px).
*   **Usage**: Establish a clear H1 -> H2 -> H3 hierarchy. Line-height should be ~1.5x for body text and ~1.2x for headings.

### Spacing & White Space
*   **Rule**: White space is not empty space; it is an active design element.
*   **System**: Use a 4px or 8px baseline grid. (Margins/Padding: 4, 8, 16, 24, 32, 48, 64px). Denser spacing implies relatedness.

### Contrast & Color
*   **Rule**: Ensure legibility.
*   **Standard**: WCAG AA requires 4.5:1 contrast ratio for normal text.
*   **Application**: Use HSL colors for programmatic control. Don't rely on color alone to convey state (use icons + text).

## 3. Component Architecture (Atomic Design)

### Atoms
*   **Definition**: Basic building blocks (Buttons, Inputs, Labels, Icons).
*   **Development**: These should be your base UI components with no business logic.

### Molecules
*   **Definition**: Groups of atoms bonded together (Search form: Input + Button).
*   **Development**: Reusable patterns that do one thing.

### Organisms
*   **Definition**: Groups of molecules (Header: Logo + Nav + Search + User Profile).
*   **Development**: Distinct sections of an interface.

## 4. Motion Design (12 Principles of UX Motion)

### Easing (not specific principle, but fundamental)
*   **Rule**: Nothing in real life moves linearly.
*   **Application**: Use `ease-out` for entering elements (decelerate), `ease-in` for exiting (accelerate).

### Signaling
*   **Principle**: Motion queues user attention.
*   **Application**: A "shake" animation on an invalid input signals error faster than text.

### Feedback
*   **Principle**: Every interaction needs a reaction.
*   **Application**: Button ripples, hover states, and active states confirm the system received the input.

## 5. Tactical Design Tips (Refactoring UI)

### Shadows for Depth
*   **Tip**: Use shadows to create a hierarchy of elevation. A modal should have a larger, more diffused shadow than a dropdown, which is higher than a card.

### Labels are Last Resort
*   **Tip**: If a value has a unit (e.g., "$50.00"), you don't need a label saying "Price". Format speaks for itself.

### Align by Baseline
*   **Tip**: When aligning icons with text, optical alignment matters more than mathematical center. Align by the baseline of the text.

### Visual Noise
*   **Tip**: De-emphasize borders. Instead of a gray border, try using a different background color (off-white) to separate sections.
