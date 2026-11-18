# UI and UX Standards

## Framework and layout

Use Bootstrap 5 by default. A typical admin interface may include a top header, persistent desktop sidebar, mobile offcanvas navigation, and a clear content area. Reuse common layout components.

## Visual style

The interface should be minimal, clean, professional, and aesthetically pleasing.

Avoid gradients, flashy AI-style buttons, excessive shadows, unnecessary animations, decorative clutter, and inconsistent colour palettes. Use simple buttons, subtle borders, consistent spacing, and clear hierarchy.

## Branding

Use centrally configured application name, logo, favicon, colours, and typography. Define CSS variables centrally. Individual modules must not invent unrelated palettes.

## Typography

Use system fonts or locally hosted fonts by default. Avoid unnecessary remote font loading. Choose font sizes based on content and available width. Keep table text compact but readable. Do not shrink text excessively to fit wide tables; use responsive wrapping or horizontal scrolling.

## Forms

Use clear labels, appropriate input types, visible validation messages, sensible grouping, and server-side validation. Preserve safe values after validation failures. Make keyboard navigation and focus states usable.

## Tables

Render data from server-side results. Always use server-side pagination, search, filtering, and sorting. Do not use jQuery DataTables or client-side table processing as a replacement. Provide empty states and clear action labels. For wide tables, use horizontal scrolling.

## Accessibility and responsiveness

Use semantic HTML, labels associated with controls, sufficient contrast, keyboard-accessible controls, descriptive link text, and meaningful alternative text. Test common mobile widths and avoid layouts that depend on hover alone.
