---
name: technical-explanation
description: Explains code and technical ideas to a software developer. Use when a reply explains how something works or why it is built that way.
metadata:
  version: "0.7.0"
---

# Technical explanation

The reader is a software developer. Assume ordinary programming words. Define a project name, and any word outside everyday programming, on first use.

These rules govern a reply that explains how something works or why it is built that way. A short factual answer stays short. Skip a stage that has nothing to say.

## Scope & Execution Boundaries

1. **Thinking Block Exemption:**
   - Internal architectural analysis, code reasoning, and mental trace blocks (the `thought` and `thinking` tags) are **100% exempt**.
   - Reason freely within thinking blocks. Apply these rules to the reply the reader sees.

2. **Code & Data Preservation Immunity:**
   - Code blocks, stack traces, abstract syntax tree dumps, terminal commands, and exact line quotes stay intact. Never alter, abbreviate, or mangle working code or logs to fit a sentence limit.

---

## Rules

1. **Order the explanation:**
   Use these stages, in this order, and skip a stage the answer has no content for:
   1. **What it is for.** One sentence on the operational intent.
   2. **How the parts relate.** A diagram or a summary table. Required when the explanation covers how more than one part relates to another. A single mechanism needs none. A sequence of steps that a numbered list already presents in order needs none.
   3. **The code.** The concrete snippet, with the file and the lines.

2. **Cite project code:**
   - When the explanation is about code in the project, name the file and the line range.
   - Use the citation form this host already uses. Do not invent a `file:///` link.
   - An explanation of what a person does, with no code, needs no citation.

3. **Names:**
   - Assume ordinary programming words. Do not define them.
   - Define a project-specific name, and any word outside everyday programming, on first use.
   - Use one name for one thing across the prose, the code, and any diagram.

4. **Diagrams:**
   - When a diagram is used, prose beside it says what it shows, using the diagram's own names and nothing the diagram does not show.
   - A diagram reaches a listener as its source text, which is not an explanation. The alternative is the prose, not the diagram's labels.

5. **One idea per block:**
   - A paragraph or a list item carries one idea. Separate ideas with a blank line.
   - Two topics do not share one block.

6. **Order, comparison, and forks:**
   - Steps that must happen in order go in a numbered list.
   - A comparison of two or more items goes in a table. Where a table would be too wide to read, use labelled records instead.
   - A fork is labelled conditions. "If the copy fails" is not one step buried in a single list.

7. **Words carry the warning:**
   - The words state a warning or a requirement.
   - Bold, a heading, or colour is not the only sign of it.

---

## Pre-Output Self-Audit Checklist

Before sending an explanation, audit against these checks:
- [ ] **Order:** Is what it is for stated before how the parts relate, and before the code, with empty stages skipped?
- [ ] **Citations:** Does project code name the file and the lines in this host's citation form?
- [ ] **Names:** Are project names and words outside everyday programming defined on first use, and is one name used for one thing?
- [ ] **Parts:** Does a diagram or table show how parts relate, unless one mechanism or a numbered list already presents that?
- [ ] **Code immunity:** Are code snippets and commands intact?
- [ ] **Diagram prose:** Does prose beside every diagram say what it shows?
- [ ] **One idea:** Does each block carry one idea, with a blank line before the next?
- [ ] **Steps:** Are ordered steps in a numbered list?
- [ ] **Comparisons:** Is a comparison a table, or labelled records because a table would be too wide?
- [ ] **Forks:** Is a fork labelled conditions rather than one numbered list?
- [ ] **Warnings:** Do the words state each warning or requirement?

## Worked examples

Models absorb style from examples, not rules. Each pair shows a failure mode and its fix.

Every "after" keeps the facts of its "before". It adds none and drops no qualification, and only filler goes. Where a "before" contradicts itself, the note beside it says which part governs. A rewrite that changes the meaning teaches the reader that plain language means reinterpreting, which is the opposite of the lesson.

### Explanations

These examples apply `technical-explanation`.

#### 1. What it is for, then the code

An explanation states what the code is for before it says how the code works. This one covers a single mechanism, so it needs no diagram. The reader is a software developer, so mutex stays undefined.

```text
Before: The `TokenBucket` class in `rate_limiter.py` (lines 34 to 89) implements
        the token bucket algorithm, using a mutex for thread safety. It takes a
        capacity and a refill rate, and its `consume()` method blocks until tokens
        are available. It exists to keep the application within third-party rate
        limits.
After:  **What it is for:** The `TokenBucket` class exists to keep the application
        within third-party rate limits.

        **The code:** The class is in `rate_limiter.py`, lines 34 to 89. It
        implements the token bucket algorithm. It uses a mutex for thread safety.

        It takes a capacity and a refill rate. Its `consume()` method blocks until
        tokens are available.
```

The citation keeps the file and the lines the "before" names. It does not invent a path or a `file:///` link.

#### 2. One name, defined on first use

The "before" uses three names for one store. The "after" uses the project's name, defined once.

```text
Before: The shadow book records unsettled charges. The poster then reads each
        ledger entry, walking the book once.
After:  The shadow book (this project's copy of unsettled charges) records
        unsettled charges. The poster then reads each shadow book entry, walking
        the shadow book once.
```

#### 3. A diagram with prose beside it

A diagram reaches a listener as its source text. Prose beside it says what the diagram shows, using the diagram's own names and nothing the diagram does not show.

```text
Before: ~~~mermaid
        sequenceDiagram
          Client->>Auth service: Credentials
          Auth service->>User database: Look up user
          Auth service-->>Client: Token
        ~~~

        See the diagram above for details.
After:  The client sends its credentials to the Auth service. The Auth service
        looks up the user in the User database, then returns a token to the
        client.

        ~~~mermaid
        sequenceDiagram
          Client->>Auth service: Credentials
          Auth service->>User database: Look up user
          Auth service-->>Client: Token
        ~~~
```
