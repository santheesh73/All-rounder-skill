# Frontend Design

## Purpose

Design a usable interface consistent with the product's visual direction.

## Activation conditions

Use for a new UI flow, a redesign, or a material change in layout, interaction, or accessibility. Follow the existing component pattern for small presentation changes.

## Required context

Target users and tasks, surrounding UI, design tokens, required content, representative data, and supported devices and input methods.

## Execution procedure

1. Identify the primary action and what users need to see before taking it. Inspect nearby screens for patterns worth preserving.
2. Establish hierarchy, type, spacing, color, and layout through existing tokens where they fit. Ground visual decisions in the content, brand, and task.
3. Design around content pressure such as long localized strings, narrow screens, and zoom. Set breakpoints where the layout fails a user task. Specify loading, empty, error, success, and retry states where applicable.
4. Use semantic controls, visible focus, clear labels and errors, adequate contrast, and reduced-motion behavior for meaningful motion.
5. Review representative viewports and exercise the primary interaction using the browser-testing playbook when browser access is available.

## Decision criteria

Reuse a component when its semantics fit. Extend it when existing consumers can keep their behavior. Use motion for state or orientation and make the same information available with reduced motion.

## Quality and safety rules

Keep meaning available without color alone. Keep primary actions reachable under zoom and keyboard navigation.

## Failure handling

If the UI cannot render, inspect component states and CSS for obvious defects. Identify viewport and interaction checks that still need a browser.

## Expected result

A coherent visual design with responsive behavior and states that support the user journey.

## Completion criteria

Hierarchy, responsive behavior, and relevant states are accounted for. Browser and accessibility checks have results or gaps.
