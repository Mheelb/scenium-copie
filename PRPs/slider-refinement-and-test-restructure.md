# Slider Refinement and Test Restructure PRP

## Goal
Explain testing dependencies, rename the test directory to `src/tests`, and refine `SliderBoxPhone.tsx` to match the styles of `SliderBox.tsx` while implementing a specific sliding loop logic for 2 images.

## Why
1.  **Clarity:** Better understanding of the testing tools and following a custom naming convention for the test directory.
2.  **Consistency:** Ensure `SliderBoxPhone` matches the visual identity (fonts, weights, sizes) of the main `SliderBox`.
3.  **UX Improvement:** Implement a smoother, loop-based sliding animation for 2 cards where the right item becomes the left item and a new one enters from the right.

## What
-   **Task 1: Testing Dependency Explanation**
    -   Provide clear explanations for `Vitest`, `Happy-dom`, and `React Testing Library`.
-   **Task 2: Rename Test Directory**
    -   `src/__tests__` -> `src/tests`.
    -   Update `vitest.config.mjs` setup file path.
-   **Task 3: Refine `SliderBoxPhone.tsx`**
    -   Match exactly the font sizes (`var(--h1-desk)`, `var(--title-social)`, `var(--txt-social)`) and weights from `SliderBox.tsx`.
    -   Implement the sliding loop:
        -   Initial state: Card 1 = `slidesData[1]`, Card 2 = `slidesData[2]`.
        -   Animation: Card 1 slides out left, Card 2 moves to left position, Card 3 slides in from right.
        -   The cards should have the same structure as `SliderBox.tsx` (image, title, description).

## Technical Context

### Files to Reference (read-only)
- `src/containers/SliderBox.tsx` - Reference for fonts and styles.
- `src/__tests__/setup.tsx` - Test setup to be moved.
- `src/__tests__/components/ContactForm.test.tsx` - Tests to be moved.

### Files to Implement/Modify
- `src/containers/SliderBoxPhone.tsx` - [Modify] Apply exact styles and new loop logic.
- `vitest.config.mjs` - [Modify] Update paths for test setup.
- `src/tests/` - [Rename] Target for moved tests.

### Existing Patterns to Follow
- GSAP for sliding animations.
- Use of CSS variables for typography consistency.
- `flushSync` pattern for index updates if needed.

## Implementation Details

### Slider Logic Refinement
Instead of sliding a long container, I'll use a local state for the visible indices and animate the transition using GSAP by targeting the specific card elements.
- Initial: Index 1 and Index 2 are visible.
- Every 2000ms:
  1.  New card is instantiated/rendered off-screen to the right.
  2.  Card at left slides out to -100%.
  3.  Card at right slides to left (0%).
  4.  New card slides into right.
  5.  Update indices.

### Styles
- `h1`: `style={{ fontSize: "var(--h1-desk)" }}`
- `h2`: `style={{ fontSize: "var(--title-social)" }}`
- `p`: `style={{ fontSize: "var(--txt-social)" }}`

## Validation Criteria

### Functional Requirements
- [ ] `SliderBoxPhone` starts with Nuage (id 2) and Ballon (id 3).
- [ ] `SliderBoxPhone` loop works as described: right becomes left, new one from right.
- [ ] `SliderBoxPhone` fonts and weights match `SliderBox.tsx` exactly.
- [ ] Tests run successfully from the new `src/tests` directory.

### Technical Requirements
- [ ] `npm test` works.
- [ ] GSAP animations are smooth and follow the 2000ms interval.
- [ ] No regression on layout.

### Testing Steps
1. Run `npm test` after renaming the directory.
2. Manually verify `SliderBoxPhone` styles and loop sequence.
