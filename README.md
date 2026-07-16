# Accessibility is a product feature

Jesus commands us to love our neighbors. I believe that should reach into the practical details of what I build: who can perceive it, operate it, understand it, and participate.

This repository is my working accessibility standard and a record of a cross-product accessibility pass. It is meant to be useful, copied, challenged, and improved.

It is not a certification or a claim that every barrier has been removed.

## Why I made this public

Over one month, I went back through four products I had been building and asked a more serious question than “does it work?”

> Who might be excluded by the way this works today?

The products were different—a public portfolio, a community and veterans resource, a job-search tool, and a visual codebase-understanding product—but the gaps repeated:

- visual structure without an equivalent semantic structure;
- controls that were easier with a pointer than a keyboard;
- motion without a meaningful reduced-motion path;
- fields and changing states without useful names or announcements;
- diagrams and canvases without a text-based way to receive the same information;
- automated checks that could report success even when the underlying scan failed.

Accessibility needed to move from a finishing pass into the product definition.

## What changed

| Product | Product-level changes | Verification added |
| --- | --- | --- |
| Portfolio | Synchronous first-render translations, keyboard-sized church-history navigation, clearer link affordances | Axe and Lighthouse across six representative routes, enforced in CI |
| ATXBro | A global skip target; persisted Standard, Lexend, and OpenDyslexic options; high-contrast and reduced-motion controls; better field names, contrast, and target sizes | 69 product tests, a 103-page production build, and Axe across seven routes |
| JobPilot | Semantic job cards and dashboard structure, labeled fields, live status messages, contextual action names, reduced-motion behavior | Accessibility contract tests within a full suite of 668 passing tests |
| EYE | Dialog focus management, complete tab semantics, keyboard-operable nodes, and textual alternatives for visual service graphs | Production build plus static and rendered accessibility contracts |

The product repositories are not all public. This repository shares the method, evidence model, and reusable standard without publishing private source code.

## The standard

The short version:

1. Start with native HTML and a meaningful document structure.
2. Make every essential path work without a pointer.
3. Name controls and announce important state changes.
4. Preserve visible focus, contrast, zoom, reflow, reduced motion, and forced colors.
5. Give visual-only experiences an equivalent semantic or textual path.
6. Make accessibility checks fail closed in CI.
7. Manually test the experience. Automation cannot represent a person.

The complete, reusable release gate is in [ACCESSIBILITY_CHECKLIST.md](ACCESSIBILITY_CHECKLIST.md).

## What “fail closed” means

An accessibility command should return a failing exit code when:

- the production server does not start;
- a representative route returns an error response;
- Axe reports an A or AA violation;
- the expected heading, main landmark, skip link, or control name is missing;
- a report cannot be produced or parsed.

This matters because a caught-and-ignored scanner error is not a passing accessibility test.

An example CI sequence looks like this:

```yaml
- run: npm ci
- run: npm run lint
- run: npm run typecheck
- run: npm run test
- run: npm run build
- run: npx playwright install --with-deps chromium
- run: npm run test:a11y
```

The exact tools can change. The contract should not: a broken or incomplete scan cannot produce a green check.

## What automation cannot tell me

Automated rules catch only part of the problem. They cannot tell me whether:

- the reading order makes sense to a person;
- an accessible name is technically present but confusing;
- a screen-reader announcement arrives at the right moment;
- a workflow is exhausting or cognitively unclear;
- a text alternative communicates the useful meaning of a visual;
- the product works well with a person's actual tools, strategies, and environment.

That is why the checklist includes keyboard, screen-reader, zoom, reflow, high-contrast, reduced-motion, and mobile checks. It is also why feedback from disabled people should be treated with respect, not as free labor owed to a product team.

## A note on fonts and preferences

There is no single “accessible font” that works for everyone. Dyslexia-oriented fonts help some readers and hinder others. The goal is a readable default with meaningful choices—not deciding on another person's behalf.

## Use this in your own project

- Copy [ACCESSIBILITY_CHECKLIST.md](ACCESSIBILITY_CHECKLIST.md) into your repository.
- Copy the [pull-request template](.github/pull_request_template.md) or adapt it to your release process.
- Add a rendered accessibility command to CI.
- Record manual evidence for new interaction patterns.
- Document known gaps with an owner, mitigation, and target date.

## Known limits and next steps

- The case study used representative routes and states, not every possible state.
- Automated WCAG A and AA checks do not establish complete WCAG conformance.
- Manual VoiceOver, zoom/reflow, forced-colors, and mobile sign-off remains part of each production release.
- This standard should change as I learn from users, practitioners, and better evidence.

## Feedback

If you see something unclear, incomplete, or harmful, please open an issue. Correction is welcome. The contribution guidelines explain how to share feedback without needing to write code.

## License

MIT. Use it, adapt it, and make it better.
