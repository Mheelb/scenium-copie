# Fix Slider H2 Font Weight PRP

## Goal
Synchronize the font weight (grease) of `h2` elements in `SliderBoxPhone.tsx` with those in `SliderBox.tsx`.

## Why
Consistency in typography is key for a professional UI. The user noticed a difference in font weight between the desktop and mobile/phone versions of the slider.

## What
-   **Task 1: Update `SliderBoxPhone.tsx`**
    -   Remove `className="font-semibold"` from `h2` elements inside `CardContent`.
    -   Ensure it matches the `h2` style in `SliderBox.tsx` (which uses default weight).

## Technical Context

### Files to Reference (read-only)
- `src/containers/SliderBox.tsx` - Reference for the correct `h2` style.

### Files to Implement/Modify
- `src/containers/SliderBoxPhone.tsx` - [Modify] Remove `font-semibold` from `h2`.

## Validation Criteria

### Functional Requirements
- [ ] `h2` elements in `SliderBoxPhone.tsx` have the exact same font weight as in `SliderBox.tsx`.

### Testing Steps
1. Compare the visual appearance of `h2` titles in both components.
