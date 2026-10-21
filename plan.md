# OOPify implementation plan

## Product approach

OOPify is a single-page React learning workspace for Java OOP. It is intentionally public and static: the experience lives in frontend state so a beginner can explore topics, run simulated examples, switch themes, and browse projects without an account or backend dependency.

### Design directions considered

- Editorial developer notebook — probability 0.08: warm paper surfaces, ink-like typography, annotated study cards, and a confident amber accent.
- Midnight terminal lab — probability 0.06: dark-first panels, electric cyan syntax accents, and dense tool-like navigation.
- Soft classroom dashboard — probability 0.05: lighter pastel cards, rounded utility sections, and a calm study rhythm.

**Chosen direction: Editorial developer notebook.**

- **Design movement:** a modern printed study guide mixed with a friendly code editor.
- **Core principles:** make the next action obvious; separate explanation from execution; use generous rhythm instead of visual clutter; keep every surface legible at small sizes.
- **Color philosophy:** a warm paper-like base makes the product feel approachable, while ink navy, amber, and coral provide clear learning hierarchy. Theme variants preserve the same semantic roles so changing mood never changes usability.
- **Layout paradigm:** a persistent left study rail anchors navigation; the main canvas reads like a notebook with stacked sections, a split topic workspace, and bounded code/output panes.
- **Signature elements:** amber marker strokes behind key phrases, compact step labels such as `01 / START HERE`, and dark code cards with gray comment ink.
- **Interaction philosophy:** clicking a navigation item changes the study context without losing position; running code always reveals output in place; theme controls stay close to the top bar instead of hiding in settings.
- **Animation:** short ease-out transitions for rail collapse, cards, buttons, and output reveal; no looping decoration that competes with reading.
- **Typography system:** use system UI for reliable rendering, with a slightly tighter display scale for headlines and monospace for code/labels. Strong weight contrast carries hierarchy.
- **Brand essence:** a plain-English Java OOP study room for absolute beginners; personality: direct, encouraging, practical.
- **Brand voice:** “Start with the thing you can see.” and “Run it, read it, change one line.”
- **Wordmark & logo:** the OOPify mark is a rounded square with a connected `O`/brace glyph, paired with a compact wordmark.
- **Signature brand color:** `#ffb84c`, a highlighter amber used for the primary action and study markers.

## Implementation structure

- `client/src/lib/learningData.ts` owns the 16-topic syllabus and exactly 10 project records, keeping all educational content data-driven.
- `client/src/pages/Home.tsx` owns the shell, navigation, theme state, dashboard sections, topic runner, project explorer, overview, and about views.
- `client/src/index.css` owns semantic theme variables, responsive layout primitives, code styling, and motion.
- `client/public/manus-routes.json` declares the single `/` route for Preview and publication.
- `app.config.ts` provides the project logo metadata required for checkpoint sync.

## Scope decisions

The code runner is a deterministic simulator rather than a Java compiler. Each example ships with an expected output string so “Run” is instant, predictable, and safe in a static public app. Progress is stored locally in the browser and does not require a database. The project stays serverless because no user accounts, private data, or durable application records are requested.

## Build workflow

Use the starter Vite/React stack and its installed dependencies. Register TypeScript diagnostics through the managed host, run the static dev server on port 3000, check the route manifest, run `pnpm check` and `pnpm build:static`, then commit the intended project files to the managed repository.
