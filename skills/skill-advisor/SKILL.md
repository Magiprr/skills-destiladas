---
name: skill-advisor
description: "Before acting on a prompt, check whether an installed skill fits it. If one does, name it with a one-line reason and rewrite the prompt so it gets a better result, not a nicer-sounding one. Use at the start of every task, or for /skill-advisor."
---

# Skill advisor

Before you start any task, read the skills listed in this session and decide whether one fits the prompt. The user is still learning when each skill applies. Each suggestion teaches them one, on a real prompt.

## When to speak

- Speak only when a skill clearly fits. A skill that only fits loosely costs the user a read and teaches the wrong habit.
- Suggest one skill. Suggest two only when they run in sequence, such as one that finds a bug and one that checks what the fix could break.
- Say nothing when no skill fits, when the user already called one, or when the prompt is a one-line question.

## What to say

Put this at the top of the reply, before any work, in the user's language:

> **Skill:** /name. Why it fits this prompt, in one line.
> **Prompt:** the rewritten prompt, ready to paste.

Then continue. If the rewrite only adds facts you can find yourself, follow the rewritten prompt and use the skill. If it needs a fact or a decision only the user has, stop and ask for that one thing.

## How to rewrite the prompt

The rewrite exists to change the result. Every piece you add must do at least one of these jobs:

1. **Call the skill** by its slash name, so it loads.
2. **Define done** as something you can observe: "loads in under 1 second on a phone", not "make it faster".
3. **Give the evidence the agent would not find alone**: the exact error, where and when it happens, the steps to reproduce it, the screen or file involved.
4. **Set the scope**: what must not change, and where the work stops.
5. **Ask for proof**: how the result will be checked before anyone calls it done.
6. **Hand back the user's decisions**: when the choice belongs to the user, ask for 2 or 3 options with a recommendation instead of one answer.

Keep the user's own words and language. Mark what only the user can fill in with brackets, like `[since when?]`.

Do not add:

- Politeness, praise, or a role ("you are an expert").
- Formatting demands the task does not need.
- The same request, longer.
- Guesses written as facts.

A rewrite that only sounds better is a failure. If you can't name the job each new piece does, cut the piece. Most rewrites fit in four lines.

## Examples

Prompt: "the login is slow, fix it"

> **Skill:** /diagnosing-bugs. The cause is unknown, and this skill measures before it changes anything.
> **Prompt:** "/diagnosing-bugs login takes [about 5 s] on [phone or desktop] since [which change]. Find the cause before touching code, show me the measurement, and fix it at the cause. Done means under 1 s, measured the same way."

Prompt: "make three versions of the onboarding screen"

> **Skill:** /prototype. Three throwaway versions side by side cost less than building one and redoing it.
> **Prompt:** "/prototype three versions of the onboarding screen that differ in [what: amount of text, steps, illustration]. Don't touch the real app. Show them side by side with what each one gains and costs, and recommend one."

Prompt: "write the email to the investor"

> **Skill:** /unslop, after the draft. The first draft always carries AI tells, and this skill removes them.
> **Prompt:** "Write the email to [who] asking for [what, by when]. Under 120 words. Then run /unslop on it."
