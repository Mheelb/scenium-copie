# Slider Responsiveness and Contact Form Tests PRP

## Goal
Implement a responsive slider for screens smaller than 1536px and add automated tests for the contact form.

## Why
1.  **UX/UI:** The current slider is optimized for large screens (2XL). Smaller screens need a simpler, more adaptive layout.
2.  **Stability:** Ensure the contact form functions correctly across its two modes (Reservation/Information) and prevents invalid submissions.

## What
-   **Task 1:** Create `SliderBoxPhone.tsx` from `SliderBox.tsx`.
    -   Simple slider with 2 images side-by-side or 1 image if space is limited.
    -   Auto-sliding every 2000ms.
-   **Task 2:** Update `src/app/page.tsx` for conditional rendering.
    -   `SliderBox` for width > 1536px.
    -   `SliderBoxPhone` for width <= 1536px.
-   **Task 3:** Setup Vitest and React Testing Library.
-   **Task 4:** Implement `src/__tests__/components/ContactForm.test.tsx`.
    -   Mock `/api/contact` API calls.
    -   Verify "Reservation" form validation and successful submission.
    -   Verify "Information" form validation and successful submission.

## Technical Context

### Files to Reference (read-only)
- `src/containers/SliderBox.tsx` - Source for the slider logic.
- `src/components/ContactForm.tsx` - Target for testing.
- `src/app/page.tsx` - Main page to modify.

### Files to Implement/Modify
- `src/containers/SliderBoxPhone.tsx` - [New] Simplified responsive slider.
- `src/app/page.tsx` - [Modify] Add responsive logic.
- `package.json` - [Modify] Add testing dependencies and scripts.
- `vitest.config.ts` - [New] Test configuration.
- `src/__tests__/setup.ts` - [New] RTL setup.
- `src/__tests__/components/ContactForm.test.tsx` - [New] Tests for ContactForm.

### Existing Patterns to Follow
- GSAP for slider animations.
- Tailwind for responsive styling.
- `fetch` for API interactions.

## Implementation Details

### Components
- `SliderBoxPhone`: Use a container with `overflow-hidden` and `flex`. Animate the `translateX` using GSAP or simple CSS transitions. Since the original uses GSAP, I'll stick with GSAP.
- `page.tsx`: Use `useEffect` with `window.innerWidth` and a state variable to handle rendering. Avoid layout shifts if possible by initializing state with `null` or a default value and only rendering after mount.

### Testing
- Mock `fetch` using `vi.fn()` or `vitest-fetch-mock`.
- Use `screen.getByPlaceholderText` and `screen.getByRole` for robust selector matching.
- Verify error messages for missing fields.

## Validation Criteria

### Functional Requirements
- [ ] `SliderBoxPhone` displays 2 images when width is between certain breakpoints and 1 image below.
- [ ] `SliderBoxPhone` auto-slides every 2000ms.
- [ ] `page.tsx` correctly switches between `SliderBox` and `SliderBoxPhone` at 1536px.
- [ ] Contact form tests cover both modes (Reservation/Information).
- [ ] Contact form tests verify validation errors for all required fields.
- [ ] Contact form tests verify successful API calls with correct payloads.

### Technical Requirements
- [ ] Vitest runs without errors (`npm test`).
- [ ] TypeScript compiles without errors.
- [ ] No regression on existing UI.

### Testing Steps
1. Run `npm test`.
2. Manual verification of responsiveness using browser dev tools at 1536px.
