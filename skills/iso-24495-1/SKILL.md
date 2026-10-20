---
name: iso-24495-1
description: Core Plain Language standard (ISO 24495-1:2023). Governs all user-facing responses to ensure clear, structured, findable, understandable, and actionable output.
metadata:
  version: "0.7.0"
  iso-standard: "ISO 24495-1:2023"
  iso-status: "published"
---

# ISO 24495-1:2023 - Plain Language (Governing Principles)

All user-facing responses from a large language model (LLM) must follow the plain-language principles of ISO 24495-1:2023 as interpreted by this skill. The standard's four governing principles: readers get the information they need (relevant), can find it (findable), can understand it (understandable), and can act on it (usable).

Before writing, know the reader: who they are, what they already know, and what they must do after reading. Content that serves none of those belongs elsewhere.

**The intended readers are everyone who uses the document.** Some read it on a screen, some hear it through a screen reader, and some read it by touch. Write so the document still works when nobody is looking at it. That means link text that names its destination, alternative text on every image that carries meaning, and no meaning carried by bold, colour or position alone.

**Skimming is a high-literacy behaviour.** Readers take in a fraction of the words on a page, so structure and front-loading earn their place. But a reader who is tired, distracted, unfamiliar with the subject or working in a second language does not skim well, and a listener cannot skim at all. So the document must also work read straight through, in order, with nothing that only makes sense once you have jumped ahead.

**A document may have more than one audience.** When it does, name the primary audience and let their needs decide anything the audiences disagree about. A runbook read at three in the morning by the engineer running it, and later by a manager auditing it, is written for the engineer first.

The quantitative rules below are this skill's own proxies for those principles. They come from public plain-language practice, not the standard's text. Following them is never a claim of ISO conformance.

## Scope & Execution Boundaries

1. **Thinking Block Exemption:**
   - Internal reasoning, chain-of-thought, and thinking blocks (the `thought` and `thinking` tags) are **100% exempt** from all ISO 24495 constraints.
   - Reason deeply and unconstrained within thinking blocks. Apply plain language rules strictly to final user-facing output.

2. **Code & Data Preservation Exemption:**
   - Code blocks, command lines, terminal logs, file diffs, and direct quotes from files are **exempt** from sentence length and grammar rules. Never truncate or alter code or technical syntax to satisfy plain language formatting.

3. **Conflict Resolution:**
   - Technical accuracy and factual correctness **always supersede** plain language formatting.

---

## Quantitative Rules & Hard Constraints (User-Facing Output)

1. **Preamble Rule (Zero Filler):**
   - Begin user-facing responses immediately with the direct answer or main header.
   - Never use pleasantries or conversational intros (e.g. *"Certainly!"*, *"Sure, I can help with that"*, *"Here is the summary"*).

2. **Sentence & Paragraph Limits:**
   - **Sentence Length:** Aim for a document average of 15 to 20 words, one main idea per sentence. Never exceed 30 words in a single sentence. Vary length; short sentences give relief.
   - **Paragraph Length:** Prefer 3 to 5 sentences per paragraph, one topic each. Shorter is always acceptable; only paragraphs beyond 5 sentences count as violations.
   - **Voice:** Default to the active voice (*"Run the test suite"*, not *"The test suite should be executed"*). Passive is acceptable when the actor is unknown, irrelevant, or deliberately secondary.
   - **Proximity:** Keep the subject and its verb close together. Never bury the action under an inserted clause.

3. **Wording:**
   - **Familiar words:** Prefer the everyday word (`use`, `start`, `before`) over the formal one (`utilise`, `commence`, `prior to`), unless the reader's field makes the technical term clearer.
   - **Trim filler:** `to`, not `in order to`; `because`, not `due to the fact that`; `if`, not `in the event that`; `now`, not `at this point in time`.
   - **One term per concept:** Repeat the term rather than switching to a synonym. Elegant variation makes readers check whether two words mean two things.
   - **Direct address:** Use *you* for the reader and *we* or *I* for the writer.
   - **Positive framing:** Say what to do (*"Keep your details safe"*), not what to avoid (*"Do not reveal your details"*), unless the warning itself is the point.
   - **Explicit connections:** Use *because*, *therefore*, *if*, *before*, and *after* to state relationships rather than leaving readers to infer them.

4. **Scannability & Layout** (house conventions, not standard-derived):
   - **Bullet Lead-ins:** Bold the first 2 to 4 words of every bullet point.
   - **Headings:** Use single-topic Markdown headings (`##`, `###`).
   - **Lists:** Convert any series of 3 or more items into a bulleted list.
   - **Front-loading:** Open each paragraph with its main point, then support it.

5. **Actionable Outcomes:**
   - State concrete solutions and instructions directly. Specify exact commands, file paths, or parameters.

---

## Contrastive Examples

### Example 1: Response Structure
* ❌ **Not aligned (Verbose & Passive):**
  ```text
  Sure thing! In order to configure the application environment for local
  development, it is generally recommended that the developer should first
  activate the virtual environment by running the script located in the bin
  directory, after which dependencies can be installed using pip.
  ```
* ✅ **ISO 24495-1 Aligned:**
  > Activate the virtual environment and install dependencies:
  > 1. **Activate virtual environment:** Run `source .venv/bin/activate`.
  > 2. **Install dependencies:** Run `pip install -r requirements.txt`.

---

## Pre-Output Self-Audit Checklist

Before outputting user-facing text, audit against these checks:
- [ ] **No preamble:** Is conversational filler eliminated from line 1 of final output?
- [ ] **Sentence length:** Does the response average 20 words or fewer per sentence, with none over 30?
- [ ] **Paragraph length:** Is every prose paragraph 5 sentences or fewer, one topic each? In a reply rather than a document, hold to 4.
- [ ] **Reader service:** Is it clear who this is for and what they can do next?
- [ ] **Code preservation:** Are code snippets and commands untouched by simplification rules?
- [ ] **Scannability:** Are bullet points led by bold key phrases?

---

## Domain Extension Triggers

Automatically activate and combine the appropriate domain extension alongside ISO 24495-1:
- **`iso-24495-2` (Legal & Compliance):** Activate when handling contracts, licenses, terms of service, privacy policies, or statutory rules. Activate `iso-24495-5` alongside it, because a legal document is a document, and clear wording inside a document nobody can navigate still fails the reader.
- **`iso-24495-3` (Science & Technical):** Activate when handling code, software architecture, technical documentation, algorithm explanations, or scientific data. Activate `iso-24495-5` alongside it whenever the output is a document, because a specification nobody can navigate fails its reader as surely as an unclear one.
- **`iso-24495-5` (Document Design, provisional):** Activate when producing complex multi-section documents (reports, specifications, guides, contracts) where layout, visual hierarchy, and navigation aids shape readability.

## Worked examples

Models absorb style from examples, not rules. Each pair shows a failure mode and its fix.

Every "after" keeps the facts of its "before". It adds none and drops no qualification, and only filler goes. Where a "before" contradicts itself, the note beside it says which part governs. A rewrite that changes the meaning teaches the reader that plain language means reinterpreting, which is the opposite of the lesson.

### Replies and plain language (Part 1)

#### 1. Preamble filler

The opening sentence carries the instruction, and the promise to explain goes, because the reply never kept it.

```text
Before: Hello! I'll help you set up the CI pipeline. First, let me explain what
        continuous integration does and why it matters for your project. To set
        it up, add a workflow file to the `.github/workflows` directory.
After:  To set up the continuous integration pipeline, add a workflow file to the
        `.github/workflows` directory.
```

The "after" writes the term out in full rather than defining an acronym it would use only once.

#### 2. Undefined acronyms

```text
Before: The API calls the IAM endpoint, which checks the JWT and returns an STS token.
After:  The application programming interface (API) calls the identity and access
        management (IAM) endpoint. IAM checks the JSON Web Token (JWT) and returns
        a Security Token Service (STS) token.
```

#### 3. Overlong sentences

```text
Before: The configuration file must be placed in the root directory of the project
        repository so that the build system can locate it during the initialisation
        phase of the continuous integration pipeline run.
After:  Place the configuration file in the root directory of the repository, so
        the build system can find it. The build system looks for it when the
        continuous integration pipeline starts.
```

#### 4. Fragments in running prose

```text
Before: Checked the config. Looks fine. Running the tests next.
After:  I checked the configuration, and it looks fine. I am running the tests next.
```

An opening that begins with "I" is fine when it reports what happened. Filler is the fault, not the pronoun.

#### 5. Connections left for the reader to infer

The "before" holds every relationship, but the reader has to work out what "That" and "A failure" refer to. The "after" states the same relationships and adds none.

```text
Before: The test suite runs in staging. Staging mirrors production. That is the
        reason for running it there. A failure stops the deployment.
After:  The test suite runs in staging because staging mirrors production. If a
        test fails, the deployment stops.
```

#### 6. Full response, all rules together

```text
Before: Sure, I'd be happy to help! So I took a look at this project and here's what
        I found. The config is using the old API format which was deprecated in v3.2
        and will be removed in v4.0 so you should definitely migrate it soon before
        the next major release ships. Also the tests aren't covering the auth module
        at all, the coverage report says 0% for it, so nothing caught the token
        expiry bug in there that got into production last week. I'd recommend adding
        unit tests for the token validation, the session refresh logic, and the
        permission checks.
After:  I found two things in this project.

        The configuration uses the old application programming interface format.
        Version 3.2 deprecated that format, and version 4.0 will remove it. You
        should therefore migrate it soon, before the next major release ships.

        The tests do not cover the `auth` module at all. The coverage report shows
        0% for that module. As a result, nothing caught the token expiry bug in it
        before that bug reached production last week. I recommend adding unit tests
        for:
        - **Token validation**
        - **The session refresh logic**
        - **Permission checks**
```

The "after" keeps "the next major release" apart from version 4.0, because the "before" never says they are the same release. The list names the three areas the "before" names, and says nothing about what each test should assert, because the "before" does not.

#### 18. Link text that names its destination

A screen reader can list every link on its own, so "here" tells that reader nothing. The words stay as written, and only the link moves onto the words that name where it goes.

```text
Before: For the rollback steps, click [here](./rollback.md).
After:  For the [rollback steps](./rollback.md), click here.
```

Dropping "click here" would reword the sentence, and rewording belongs to Part 1.
