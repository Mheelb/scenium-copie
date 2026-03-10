# Slider Phone Refinement PRP

## Goal
Fix visual and performance issues in `SliderBoxPhone.tsx`: restore missing backgrounds/borders during animation, adjust the mobile breakpoint to 1000px, and eliminate the image flicker when new slides enter.

## Why
1.  **Visual Integrity:** Backgrounds and borders should remain consistent throughout the animation.
2.  **UX/UI:** Screens below 1000px are too narrow for two cards; switching to one card improves readability.
3.  **Performance/Polish:** The "flicker" where a new card shows the previous image before updating is jarring and feels unpolished.

## What
-   **Task 1: Style Consistency**
    -   Ensure `cardStyle` (background, border) is preserved during and after GSAP animations.
    -   Avoid `clearProps: "all"` which may be wiping React-applied inline styles.
-   **Task 2: Responsive Breakpoint**
    -   Update `handleResize` logic to switch to 1 image when `window.innerWidth < 1000`.
-   **Task 3: Eliminate Image Flicker**
    -   Refactor the sliding logic to avoid `cloneNode` for content that needs to be different.
    -   Render the "next" card in the React tree instead of manually cloning and updating the DOM. This ensures React manages the image source and it's ready before the animation starts.

## Technical Context

### Files to Reference (read-only)
- `src/containers/SliderBox.tsx` - Reference for original styles.

### Files to Implement/Modify
- `src/containers/SliderBoxPhone.tsx` - [Modify] Implement fixes and logic refinement.

### Existing Patterns to Follow
- GSAP for smooth transitions.
- React state for managing `activeIndex`.

## Implementation Details

### Refined Sliding Logic
Instead of `cloneNode`, I'll render three cards:
1.  `Visible Card 1`
2.  `Visible Card 2` (hidden if < 1000px)
3.  `Hidden Card` (always rendered off-screen with the *next* slide data)

Animation flow:
- Animate all three cards to the left.
- On complete:
    - Update `activeIndex`.
    - Reset positions instantly (without animation) using GSAP or React state.

### Breakpoint
- Update `isMobile` check to use `1000` instead of `640`.

### Styles
- Ensure `cardStyle` includes `background: 'var(--grey)'` and `border: '2px solid var(--border-grey)'`.
- Check if `SliderBox.tsx` has specific styles for different cards (black vs grey) and replicate.

## Validation Criteria

### Functional Requirements
- [ ] Slider displays 1 card below 1000px.
- [ ] Backgrounds and borders are visible on all cards at all times.
- [ ] No image flicker: the card entering from the right shows the correct image from the start of the animation.
- [ ] Loop sequence: Nuage/Ballon -> Ballon/Fleur -> Fleur/Nuage.

### Technical Requirements
- [ ] `npm test` passes.
- [ ] GSAP animations use `clearProps: "transform"` instead of `all`.
- [ ] React `mounted` state handles SSR consistency.

### Testing Steps
1. Resize browser to < 1000px and verify 1-card layout.
2. Observe animation to ensure no flicker on the entering card.
3. Verify styles match `SliderBox.tsx` exactly.
