# Accessibility product and release checklist

This is a practical baseline for user-facing work. It is not a substitute for involving disabled people, testing with assistive technology, or evaluating the requirements that apply to your product and jurisdiction.

## Product structure

- [ ] Every route has a descriptive page title, one useful `h1`, and a `main` landmark.
- [ ] A working skip link reaches the primary content.
- [ ] Headings describe the page hierarchy without skipping levels for styling.
- [ ] Native buttons, links, labels, lists, and tables are used before custom roles.
- [ ] Instructions, errors, empty states, and next actions use plain language.
- [ ] Images have meaningful alternative text or `alt=""` when decorative.

## Controls and keyboard access

- [ ] Every action works with a keyboard and does not depend on drag, hover, or pointer input.
- [ ] Focus is visible and follows a logical order.
- [ ] Focus is never trapped unintentionally or lost after content changes.
- [ ] Links navigate; buttons perform actions.
- [ ] Every field and control has a useful programmatic name.
- [ ] Primary and coarse-pointer targets are at least 44 by 44 CSS pixels where practical.
- [ ] Pinch zoom and text resizing are not disabled.

## Interaction patterns

- [ ] Dialogs have a name, `aria-modal`, Escape handling, contained focus, and focus return.
- [ ] Tabs expose tab, tabpanel, selected state, and arrow-key behavior.
- [ ] Menus, disclosures, and accordions expose their expanded or selected state.
- [ ] Loading, success, error, and changing-result states are announced appropriately.
- [ ] Validation identifies the affected field and explains how to recover.
- [ ] Destructive or irreversible actions require clear confirmation.

## Visual access and motion

- [ ] Text and meaningful graphics meet an AA contrast baseline.
- [ ] Information is not conveyed by color alone.
- [ ] Content remains usable at 200% zoom and reflows without loss at 400% where applicable.
- [ ] Forced-colors and high-contrast modes preserve controls, focus, and meaning.
- [ ] `prefers-reduced-motion` removes nonessential animation.
- [ ] Product-level motion preferences persist when motion is central to the experience.
- [ ] Font and readability preferences are choices rather than assumptions about a diagnosis.

## Canvas, charts, maps, diagrams, and 3D

- [ ] Essential visual information has a synchronized semantic or textual alternative.
- [ ] Essential actions have ordinary keyboard-operable controls outside the visual surface.
- [ ] The alternative communicates relationships and meaning, not merely object names.
- [ ] Motion-heavy visualizations provide a stable reduced-motion state.
- [ ] Changes in the visual state are announced when they affect the user's task.

## Automated release gate

- [ ] CI tests representative production routes or states after a production build.
- [ ] The command fails if the server fails, a route errors, the scanner fails, or results cannot be parsed.
- [ ] Automated WCAG A and AA violations fail the check.
- [ ] The shell contract asserts the heading, main landmark, skip link, and named controls.
- [ ] Motion-heavy experiences are tested with reduced motion enabled.
- [ ] A fast component or source contract lives near each important interaction pattern.
- [ ] Accessibility failures cannot be caught, logged, and converted into success.

## Manual release evidence

Record the tester, date, environment, result, and follow-up issue for each item.

- [ ] Complete the essential flow using only a keyboard, including reverse tab order.
- [ ] Verify focus behavior for dialogs, menus, tabs, errors, and route-like transitions.
- [ ] Use a screen reader to verify reading order, names, states, errors, and announcements.
- [ ] Verify browser zoom and reflow at 200% and 400%.
- [ ] Verify reduced motion and forced colors or high-contrast mode.
- [ ] Verify mobile/coarse-pointer targets and orientation changes.
- [ ] Review the text alternative for every essential visual surface.

## Evidence record

```text
Feature or route:
Tester and date:
Browser and operating system:
Assistive technology or preference:
Keyboard result:
Screen-reader result:
Zoom and reflow result:
Reduced-motion result:
Forced-colors/high-contrast result:
Mobile target result:
Visual alternative result:
Issues or follow-up links:
```

## Exceptions

An exception is not silent. Record:

- the exact unmet requirement;
- the people and workflows affected;
- the reason it cannot be corrected before release;
- the current mitigation;
- the accountable owner;
- a target date and tracking issue.

An undocumented exception is a failed release gate.
