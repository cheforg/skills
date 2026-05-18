<p>
  <a href="https://www.aihero.dev/s/skills-newsletter">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skills-repo-dark_2x.png">
      <source media="(prefers-color-scheme: light)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png">
      <img alt="Skills" src="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png" width="369">
    </picture>
  </a>
</p>

# Skills For Real Engineers

Agent skills for doing real engineering — not vibe coding.

This repo combines two collections:

- **Matt Pocock's skills** — small, composable engineering and productivity skills designed to fix common failure modes with Claude Code, Codex, and other coding agents.
- **Vercel's agent-skills** — React/Next.js performance, web design, React Native, view transitions, composition patterns, and Vercel deployment.

Every skill lives directly under `skills/<skill-name>/`. There are no category folders — just sibling skills.

If you want to keep up with changes, join ~60,000 other devs on the newsletter:

[Sign Up To The Newsletter](https://www.aihero.dev/s/skills-newsletter)

## Quickstart (30-second setup)

1. Run the skills.sh installer:

```bash
npx skills@latest add mattpocock/skills
```

2. Pick the skills you want, and which coding agents you want to install them on. **Make sure you select `/setup-matt-pocock-skills`**.

3. Run `/setup-matt-pocock-skills` in your agent. It will:
   - Ask you which issue tracker you want to use (GitHub, Linear, or local files)
   - Ask you what labels you apply to ticks when you triage them (`/triage` uses labels)
   - Ask you where you want to save any docs we create

4. Bam - you're ready to go.

## Why These Skills Exist

These skills fix common failure modes seen with Claude Code, Codex, and other coding agents.

### #1: The Agent Didn't Do What I Want

> "No-one knows exactly what they want"
>
> David Thomas & Andrew Hunt, [The Pragmatic Programmer](https://www.amazon.co.uk/Pragmatic-Programmer-Anniversary-Journey-Mastery/dp/B0833F1T3V)

**The Problem**. The most common failure mode in software development is misalignment. You think the dev knows what you want. Then you see what they've built - and you realize it didn't understand you at all.

This is just the same in the AI age. There is a communication gap between you and the agent. The fix for this is a **grilling session** - getting the agent to ask you detailed questions about what you're building.

**The Fix** is to use:

- [`/grill-me`](./skills/grill-me/SKILL.md) - for non-code uses
- [`/grill-with-docs`](./skills/grill-with-docs/SKILL.md) - same as [`/grill-me`](./skills/grill-me/SKILL.md), but adds more goodies (see below)

These are the most popular skills in this repo. They help you align with the agent before you get started, and think deeply about the change you're making. Use them _every_ time you want to make a change.

### #2: The Agent Is Way Too Verbose

> With a ubiquitous language, conversations among developers and expressions of the code are all derived from the same domain model.
>
> Eric Evans, [Domain-Driven-Design](https://www.amazon.co.uk/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215)

**The Problem**: At the start of a project, devs and the people they're building the software for (the domain experts) are usually speaking different languages.

The same tension exists with agents. Agents are usually dropped into a project and asked to figure out the jargon as they go. So they use 20 words where 1 will do.

**The Fix** for this is a shared language. It's a document that helps agents decode the jargon used in the project.

<details>
<summary>
Example
</summary>

Here's an example [`CONTEXT.md`](https://github.com/mattpocock/course-video-manager/blob/076a5a7a182db0fe1e62971dd7a68bcadf010f1c/CONTEXT.md), from the `course-video-manager` repo. Which one is easier to read?

- **BEFORE**: "There's a problem when a lesson inside a section of a course is made 'real' (i.e. given a spot in the file system)"
- **AFTER**: "There's a problem with the materialization cascade"

This concision pays off session after session.

</details>

This is built into [`/grill-with-docs`](./skills/grill-with-docs/SKILL.md). It's a grilling session, but that helps you build a shared language with the AI, and document hard-to-explain decisions in ADR's.

> [!TIP]
> A shared language has many other benefits than reducing verbosity:
>
> - **Variables, functions and files are named consistently**, using the shared language
> - As a result, the **codebase is easier to navigate** for the agent
> - The agent also **spends fewer tokens on thinking**, because it has access to a more concise language

### #3: The Code Doesn't Work

> "Always take small, deliberate steps. The rate of feedback is your speed limit. Never take on a task that's too big."
>
> David Thomas & Andrew Hunt, [The Pragmatic Programmer](https://www.amazon.co.uk/Pragmatic-Programmer-Anniversary-Journey-Mastery/dp/B0833F1T3V)

**The Problem**: Let's say that you and the agent are aligned on what to build. What happens when the agent _still_ produces crap?

It's time to look at your feedback loops. Without feedback on how the code it produces actually runs, the agent will be flying blind.

**The Fix**: You need the usual tranche of feedback loops: static types, browser access, and automated tests.

For automated tests, a red-green-refactor loop is critical. This is where the agent writes a failing test first, then fixes the test. This helps give the agent a consistent level of feedback that results in far better code.

The **[`/tdd`](./skills/tdd/SKILL.md)** skill slots into any project. It encourages red-green-refactor and gives the agent plenty of guidance on what makes good and bad tests.

For debugging, **[`/diagnose`](./skills/diagnose/SKILL.md)** wraps best debugging practices into a simple loop.

### #4: We Built A Ball Of Mud

> "Invest in the design of the system _every day_."
>
> Kent Beck, [Extreme Programming Explained](https://www.amazon.co.uk/Extreme-Programming-Explained-Embrace-Change/dp/0321278658)

> "The best modules are deep. They allow a lot of functionality to be accessed through a simple interface."
>
> John Ousterhout, [A Philosophy Of Software Design](https://www.amazon.co.uk/Philosophy-Software-Design-2nd/dp/173210221X)

**The Problem**: Most apps built with agents are complex and hard to change. Because agents can radically speed up coding, they also accelerate software entropy. Codebases get more complex at an unprecedented rate.

**The Fix** for this is a radical new approach to AI-powered development: caring about the design of the code.

This is built in to every layer of these skills:

- [`/to-prd`](./skills/to-prd/SKILL.md) quizzes you about which modules you're touching before creating a PRD
- [`/zoom-out`](./skills/zoom-out/SKILL.md) tells the agent to explain code in the context of the whole system

And crucially, [`/improve-codebase-architecture`](./skills/improve-codebase-architecture/SKILL.md) helps you rescue a codebase that has become a ball of mud. Run it on your codebase once every few days.

### Summary

Software engineering fundamentals matter more than ever. These skills are a best effort at condensing those fundamentals into repeatable practices, to help you ship the best apps of your career. Enjoy.

## Reference

All active skills, alphabetical:

- **[caveman](./skills/caveman/SKILL.md)** — Ultra-compressed communication mode. Cuts token usage ~75% by dropping filler while keeping full technical accuracy.
- **[composition-patterns](./skills/composition-patterns/SKILL.md)** — React composition patterns that scale. Avoid boolean prop proliferation through compound components, lifting state, and composing internals.
- **[deploy-to-vercel](./skills/deploy-to-vercel/SKILL.md)** — Deploy applications and websites to Vercel. Returns preview URL and a claim URL for transferring ownership.
- **[diagnose](./skills/diagnose/SKILL.md)** — Disciplined diagnosis loop for hard bugs and performance regressions: reproduce → minimise → hypothesise → instrument → fix → regression-test.
- **[git-guardrails-claude-code](./skills/git-guardrails-claude-code/SKILL.md)** — Set up Claude Code hooks to block dangerous git commands (push, reset --hard, clean, etc.) before they execute.
- **[grill-me](./skills/grill-me/SKILL.md)** — Get relentlessly interviewed about a plan or design until every branch of the decision tree is resolved.
- **[grill-with-docs](./skills/grill-with-docs/SKILL.md)** — Grilling session that challenges your plan against the existing domain model, sharpens terminology, and updates `CONTEXT.md` and ADRs inline.
- **[improve-codebase-architecture](./skills/improve-codebase-architecture/SKILL.md)** — Find deepening opportunities in a codebase, informed by the domain language in `CONTEXT.md` and the decisions in `docs/adr/`.
- **[migrate-to-shoehorn](./skills/migrate-to-shoehorn/SKILL.md)** — Migrate test files from `as` type assertions to `@total-typescript/shoehorn`.
- **[prototype](./skills/prototype/SKILL.md)** — Build a throwaway prototype to flush out a design — either a runnable terminal app for state/business-logic questions, or several radically different UI variations toggleable from one route.
- **[react-best-practices](./skills/react-best-practices/SKILL.md)** — React and Next.js performance optimization guidelines from Vercel Engineering.
- **[react-native-skills](./skills/react-native-skills/SKILL.md)** — React Native and Expo best practices: list performance, animations, UI patterns, native module integration.
- **[react-view-transitions](./skills/react-view-transitions/SKILL.md)** — Implement smooth, native-feeling animations using React's View Transition API. Covers `<ViewTransition>`, `addTransitionType`, transition types, and Next.js integration.
- **[scaffold-exercises](./skills/scaffold-exercises/SKILL.md)** — Create exercise directory structures with sections, problems, solutions, and explainers.
- **[setup-matt-pocock-skills](./skills/setup-matt-pocock-skills/SKILL.md)** — Scaffold the per-repo config (issue tracker, triage label vocabulary, domain doc layout) that the engineering skills consume. Run once per repo before using `to-issues`, `to-prd`, `triage`, `diagnose`, `tdd`, `improve-codebase-architecture`, or `zoom-out`.
- **[setup-pre-commit](./skills/setup-pre-commit/SKILL.md)** — Set up Husky pre-commit hooks with lint-staged, Prettier, type checking, and tests.
- **[tdd](./skills/tdd/SKILL.md)** — Test-driven development with a red-green-refactor loop. Builds features or fixes bugs one vertical slice at a time.
- **[to-issues](./skills/to-issues/SKILL.md)** — Break any plan, spec, or PRD into independently-grabbable issues using vertical slices.
- **[to-prd](./skills/to-prd/SKILL.md)** — Turn the current conversation context into a PRD and publish it to the project issue tracker.
- **[triage](./skills/triage/SKILL.md)** — Triage issues through a state machine of triage roles.
- **[vercel-cli-with-tokens](./skills/vercel-cli-with-tokens/SKILL.md)** — Deploy and manage Vercel projects using token-based authentication rather than interactive login.
- **[web-design-guidelines](./skills/web-design-guidelines/SKILL.md)** — Review UI code for Web Interface Guidelines compliance: accessibility, performance, focus, forms, animation, typography, and more.
- **[write-a-skill](./skills/write-a-skill/SKILL.md)** — Create new skills with proper structure, progressive disclosure, and bundled resources.
- **[zoom-out](./skills/zoom-out/SKILL.md)** — Tell the agent to zoom out and give broader context or a higher-level perspective on an unfamiliar section of code.

### In progress

Drafts not yet ready to ship — interfaces may change.

- **[handoff](./skills/handoff/SKILL.md)** — Compact the current conversation into a handoff document for another agent to pick up.
- **[writing-beats](./skills/writing-beats/SKILL.md)** — Shape an article as a journey of beats, choose-your-own-adventure style.
- **[writing-fragments](./skills/writing-fragments/SKILL.md)** — Mine the user for fragments and append them to a single document as raw material for a future article.
- **[writing-shape](./skills/writing-shape/SKILL.md)** — Take a markdown file of raw material and shape it into an article through a conversational session.

### Personal

Tied to a specific personal setup — not promoted for general use.

- **[edit-article](./skills/edit-article/SKILL.md)** — Edit and improve articles by restructuring sections and tightening prose.
- **[obsidian-vault](./skills/obsidian-vault/SKILL.md)** — Search, create, and manage notes in an Obsidian vault.

### Deprecated

No longer maintained — kept for reference. Don't rely on these.

- **[design-an-interface](./skills/design-an-interface/SKILL.md)** — Generate multiple radically different interface designs for a module using parallel sub-agents.
- **[qa](./skills/qa/SKILL.md)** — Interactive QA session where the user reports bugs conversationally and the agent files issues.
- **[request-refactor-plan](./skills/request-refactor-plan/SKILL.md)** — Create a detailed refactor plan with tiny commits via user interview, then file it as a GitHub issue.
- **[ubiquitous-language](./skills/ubiquitous-language/SKILL.md)** — Extract a DDD-style ubiquitous language glossary from the current conversation.

## License

MIT
