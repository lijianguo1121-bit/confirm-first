# Web Development Matching Playbook

For checklist items involving web pages / webapps / UI. Goal: beautiful UI and complete interaction, built on proven GitHub tools.

## Matching strategy

1. Search live and re-verify stars/activity — the names below are starting points, not facts; numbers change.
2. Prefer composing a small stack (framework + component library + animation + icons) over one giant dependency.
3. Prefer copy-in component models (e.g. shadcn/ui style) or well-maintained libraries with recent commits.

## Candidate toolbox by category (verify via live search before use)

| Category | Strong candidates to search first |
| --- | --- |
| UI components | shadcn/ui, Radix UI, Ant Design, MUI, daisyUI, Aceternity UI, Magic UI |
| CSS framework | tailwindcss |
| Animation / interaction | motion (framer-motion), GSAP, react-spring, auto-animate, lenis (smooth scroll) |
| Icons | lucide, heroicons, phosphor-icons |
| Charts / data viz | echarts, recharts, d3, tremor |
| 3D / special effects | three.js, react-three-fiber |
| Design reference | awwwards/landing-page collections, uiverse |

If the local environment already provides an approved stack (e.g. a webapp skill with React + Tailwind + shadcn/ui), use it and only fill gaps from GitHub.

## UI quality bar (must all pass)

- Visual hierarchy: one clear primary action per view; consistent spacing scale and typography pairing.
- No default-looking pages: custom palette, non-browser-default controls, intentional whitespace.
- Responsive: usable at mobile and desktop widths; no horizontal scroll or clipped content.
- Theme: dark/light handled deliberately, not half-styled.

## Interaction checklist (verify in Phase 4)

- States: hover / focus / active / disabled on every interactive element.
- Async states: loading skeleton or spinner, empty state, error state with retry.
- Feedback: actions confirm via toast, inline result, or transition — never silent.
- Motion: transitions 150–300ms, ease-out; no janky layout jumps.
- Keyboard: Tab order works; Enter/Escape behave on dialogs and forms.
- Accessibility basics: contrast ≥ 4.5:1 for body text, alt text, labels on inputs.

## How to present the match (Phase 3 format for web items)

```
<事项> → <栈/工具组合> ★（各组件一句话职责）＋ UI/交互按 web-dev 清单验收
```
