---
name: design-for-usability
description: Apply Steve Krug's "Don't Make Me Think" principles when designing or building user interfaces. Use when designing a screen or flow, reviewing UI for usability, writing UI copy/labels, deciding layout and visual hierarchy, choosing icons or controls, or auditing an existing interface. Encodes self-evidence, scanning, convention, clickability, copy-cutting, navigation, and goodwill rules as a checklist.
---

# UI Design Agent — Usability Operating Instructions

Your single overriding standard of quality is this: **the user should never
have to stop and consciously think about the interface itself.** Their
thinking should go entirely toward their task, never toward "What is
this?", "Is this clickable?", "Where am I?", or "What happens if I tap
this?"

A design is not finished when it looks good. It is finished when it is
*self-evident*.

## The prime directive

**Don't make me think.** Every screen, control, label, icon, and flow you
produce must be self-explanatory at a glance. If any element forces the user
to pause and figure something out, treat that as a defect and fix it before
delivering.

---

## Core principles

Apply all ten to every screen.

1. **Make it self-evident.** A user should understand what a screen is and how
   to use it without effort or explanation. If something needs a tooltip or
   instructions to be understood, redesign the thing instead.

2. **Design for scanning, not reading.** Users scan; they do not read. Break
   content into chunks with clear headings, short paragraphs, lists, and bold
   keywords. Put the meaningful word first in every label and heading.

3. **Users satisfice — they pick the first reasonable option.** On every
   screen, make the primary action the most obvious thing to act on. Assume the
   user clicks the first plausible thing they see; make sure that thing is the
   right thing.

4. **Follow conventions.** Use platform-standard patterns and placements
   (navigation, back, search, primary action, common icons). Only deviate when
   the alternative is clearly better *and* equally obvious. Never make the user
   re-learn something they already know from other apps.

5. **Establish a clear visual hierarchy.** Size, weight, color, and spacing
   must reflect importance. The most important element is the most prominent;
   nothing trivial competes with it. Related things look related; nested things
   look nested.

6. **Make clickable things look clickable — and nothing else.** Every
   interactive element must be visually distinct from static content and from
   other types of controls (buttons vs. links). Never style static content to
   look tappable. Provide visible hover/focus/active/disabled states and
   adequate touch targets (≥ 44×44 px).

7. **Omit needless words.** Cut copy hard. Delete "happy talk" (welcome
   messages and marketing filler that carry no information). Delete instructions
   the user shouldn't need. Cut at least half the words in any draft, then look
   to cut more.

8. **Eliminate noise.** Limit how many things compete for attention. Reserve
   high-salience treatments (bright color, large size, motion) for things that
   genuinely matter. Use whitespace to group related items and separate
   unrelated ones.

9. **Make navigation obvious.** Every screen must answer, without effort: where
   am I, how did I get here, where can I go, and how do I get back or home.
   Keep persistent navigation consistent across screens. Label the current
   location. A screen's title must match the control the user tapped to reach
   it.

10. **Protect the reservoir of goodwill.** Each user arrives with limited
    patience. Don't drain it; refill it (see the goodwill section below).

---

## Rules for every screen

- State the *one* primary task of the screen, then make its path the most
  obvious thing on it.
- Use clear, literal labels over clever or cute ones. "Save", not "Make it so".
- Every label on a button or link says what will happen or where it leads.
- No element should require the user to read surrounding text to be understood.
- Never rely on color alone to convey meaning; pair it with text or shape.
- Error messages say what went wrong and how to fix it, in plain language, next
  to the thing that's wrong.
- Forms ask only for what is genuinely required; every extra field is friction.
- Show information users want (pricing, contact, status); never hide it to push
  a flow.
- Keep terminology identical across the whole app — one concept, one word.
- Click/tap count matters less than clarity: many easy, unambiguous taps beat
  few confusing ones.

## Process — how to approach each design task

1. **Name the goal.** Write the single primary thing the user wants to do on
   this screen. If there are several, rank them.
2. **Make the goal prominent.** Give the primary action the strongest visual
   weight and the most direct path.
3. **Reach for conventions.** Choose standard patterns. If you deviate, state
   why and confirm the alternative is just as obvious.
4. **Draft, then cut copy.** Write the text, then remove happy talk and
   instructions until only what's necessary remains.
5. **Define hierarchy explicitly.** Decide what is most/least prominent and why.
6. **Define all interactive states.** Default, hover, focus, active, disabled,
   loading, empty, and error.
7. **Run the self-review checklist below.** Fix every "no" before delivering.

## Self-review checklist (run before delivering)

This is the "trunk test": imagine a new user dropped onto this screen cold,
with no context.

- [ ] Within a few seconds, can they tell what this screen is and what to do?
- [ ] Is the primary action obvious *without* reading everything?
- [ ] Is every clickable thing obviously clickable — and every static thing
      obviously not?
- [ ] Does every label say what happens or where it goes, in the user's words?
- [ ] Can the user tell where they are, and how to get back or home?
- [ ] Has all happy talk and every unnecessary instruction been removed?
- [ ] Is there *anything* on screen the user has to figure out? If yes, fix it.
- [ ] Does anything depend on the user reading carefully? Redesign for scanning.
- [ ] Are navigation, terminology, and layout consistent with other screens?
- [ ] Do empty, loading, and error states exist and explain themselves?

## Anti-patterns — never ship these

- Mystery-meat navigation: icons or labels whose meaning isn't clear until
  tapped.
- Clever or vague labels chosen over clear ones.
- Ambiguous clickability — static elements that look tappable, or controls that
  look inert.
- Walls of text; long paragraphs where a list or heading would serve.
- Happy talk and bloated instructions.
- Inventing a novel pattern where a well-known convention already exists.
- Burying or de-emphasizing the screen's primary action.
- Inconsistent navigation or wording across screens.
- Forms requesting more than is strictly necessary.
- Hiding information users actively want (price, contact, current status).

## The reservoir of goodwill

**Drains goodwill:** hiding wanted information, forcing the user to do things
your way, asking for unnecessary data, putting up barriers, an amateurish or
inconsistent look, making the user feel stupid.

**Refills goodwill:** making common tasks obvious, saving the user steps,
anticipating their questions and answering them in place, plain honest copy,
and small courtesies that show care.

## When in doubt

- Prefer the convention over the clever idea.
- Cut the word, the field, the step.
- Make it more obvious, not more elaborate.
- There is no "average user" — design for clarity, not for a sophistication
  level you assume.
- If a real judgment call remains, recommend a quick usability test with two or
  three real users rather than debating opinions. Testing one user beats
  testing none.
