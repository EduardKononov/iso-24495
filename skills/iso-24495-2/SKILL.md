---
name: iso-24495-2
description: Sector-specific Plain Language standard for legal communication (ISO 24495-2:2025). Applied during contract drafting, license review, and legal/compliance writing.
metadata:
  version: "0.7.0"
  iso-standard: "ISO 24495-2:2025"
  iso-status: "published"
---

# ISO 24495-2:2025 - Plain Language (Legal Communication)

> **Proxy status:** These rules are this project's own proxies for the standard's principles, not its text. Following them is never a claim of ISO conformance.

Extends ISO 24495-1:2023 for legal documents, contractual provisions, licenses, and regulatory compliance.

## Scope & Execution Boundaries

1. **Thinking Block Exemption:**
   - Internal reasoning and legal analysis within thinking blocks (the `thought` and `thinking` tags) are **100% exempt** from plain language constraints.
   - Reason exhaustively within thinking blocks. Apply plain language rules strictly to final user-facing legal text.

2. **Legal Enforceability Primacy:**
   - Plain language simplification must **never** alter legal rights, liabilities, or contractual enforceability. If a term of art is legally required to avoid ambiguity, retain it and provide a plain explanation.

3. **Document Design Applies Here Too:**
   - A legal document is a document, so `iso-24495-5` loads alongside this skill. Part 5 governs headings, navigation, chunking, signalling, and readers who cannot see the page.
   - Four of the rules below cover what Part 5 leaves out: defined terms, cross-references, clause identifiers, and the summary layer. The fifth, section names, adds nothing and applies a case Part 5 already allows to the sections a contract has.
   - Where the two appear to conflict, follow the resolution named in the rules below.

---

## Quantitative Rules & Hard Constraints (User-Facing Output)

1. **Modal Verb Standardisation:**
   - Use **must** for mandatory obligations (*"The User must pay..."*).
   - Use **must not** for prohibitions (*"The User must not copy..."*).
   - Use **may** for discretionary permissions, as in "the User may end the agreement".
   - **Banned Words:** Never use *"shall"*, *"should"*, *"hereby"*, *"hereinafter"*, *"wherefore"*, or *"parties of the first part"*.

2. **Explicit Subject Actor Identification:**
   - Every obligation sentence MUST explicitly name the subject actor (*"The Licensee must notify..."* rather than *"Notice must be provided..."*).

3. **Conditional Clause Formatting:**
   - Format multi-condition legal clauses as structured itemised lists:
     - **Trigger / Prerequisite:** What condition initiates the rule.
     - **Obligation / Action:** What action must or may be taken.
     - **Consequence:** What occurs upon non-compliance.

4. **Defined Terms:**
   - Define each term once, and use it unchanged everywhere after. Two words for one concept invite an argument that they mean two things.
   - Put the definition where the reader first meets the term. Where a term appears in more than one section, collect the definitions in one section and point the first use at it.
   - Write a term out in full where the document uses it once, rather than defining it.
   - Say in words that a term is defined, and where. Capital letters are silent to a listener, so **Confidential Information** on its own tells them nothing.

5. **Cross-References:**
   - Name what the referenced clause says, alongside its identifier. Write *"the notice deadline in clause 4.2"* rather than *"clause 4.2"*.
   - Keep that wording identical to the referenced clause's own heading or opening line.
   - When you point at an obligation, point at the clause carrying it, never at one that only points somewhere else. A first use pointing at the collected definitions is the exception rule 4 requires, because a definition binds nobody.

6. **Clause Identifiers:**
   - Number every operative clause, because a reader, a court and a counterparty must all cite the same thing. An operative clause imposes, permits or prohibits an action. Recitals, definitions and schedules are numbered by the conventions of the document, not by this rule.
   - Write the identifier into the clause text rather than as list markup. Markdown numbers an ordered list 1, 2, 3, so a compound identifier such as 4.2.1 survives only when it is written in the text.
   - This is the one place a legal document departs from Part 5's rule that a sequence stays an ordered list.
   - A clause identifier is neither a heading nor list numbering. So it does not count against Part 5's heading limit, and Part 5's rule on numbering headings does not govern it.
   - Keep an identifier for the life of the document. An amendment adds a clause, or marks one deleted, and leaves every existing number where it is, because filings, correspondence and other contracts cite those numbers.

7. **The Summary Layer:**
   - Place a plain summary of the terms the reader must act on directly after Part 5's opening block. Give it the overview's own heading, because a summary of what a reader must act on is the conclusion they need before the detail, which is what Part 5 labels. Cover what they must do, what they must pay, when the agreement ends, and how to leave it. A document without one or more of those, such as a privacy policy with no payment, covers the rest. A document with no terms the reader must act on needs no summary of this shape, and Part 5 still decides whether it has an overview.
   - The summary **must** state that the operative text governs, and **must** name where that text starts. A summary a reader could mistake for the agreement changes their rights, which the enforceability boundary above forbids.
   - The summary **must not** add an obligation, newly qualify one, or leave a reader believing an obligation is gone. Where the operative text already qualifies a term, state the term together with that qualification, which Part 5 requires the overview to keep. Where stating it would take more words than the clause itself, leave the term out and point to its clause. A pointer keeps the obligation reachable, so it is not a removal.
   - Map the document onto Part 5's three levels of detail. The summary is the overview, and the operative terms are the main body. Place each schedule by what it holds, because Part 5's optional detail is for what only some readers need. A schedule carrying an obligation, a payment or a limit belongs in the main body with the rest of the operative terms, whichever page it is printed on. Reserve the optional level for a schedule a reader can skip and still comply, such as a list of contacts or a specimen form.

8. **Section Names:**
   - A contract's section names are the reference case Part 5 already allows, and not a new exception. A reader jumps to Payment, Termination or Liability by subject, so each keeps its subject as its name.

---

## Contrastive Examples

### Example 1: Contractual Obligation
* ❌ **Not aligned (Archaic Legalese):**
  ```text
  The Licensee shall hereinafter hold harmless and indemnify the Licensor
  from and against any and all claims wherefore notice has not been provided
  within thirty (30) days.
  ```
* ✅ **ISO 24495-2 Aligned:**
  > **Indemnification Notice Requirement:**
  > 1. **Notice deadline:** The Licensee must notify the Licensor of any claim within 30 days.
  > 2. **Consequence:** If the Licensee fails to meet this deadline, the Licensee must cover all resulting losses and legal costs incurred by the Licensor.

### Example 2: The Summary Layer
* ❌ **Not aligned (the summary drops conditions in the source clause):**
  ```text
  9.1 The Customer may terminate this Agreement by giving the Supplier at
      least 30 days' written notice. If the Customer does so, the Supplier
      must refund to the Customer the fees paid for the part of the term
      that has not yet run. The refund is calculated pro rata.

  Summary: You can end the Agreement and get your money back.
  ```
* ✅ **ISO 24495-2 Aligned:**
  > ## Summary of your main terms
  >
  > The operative text starts at clause 9.1 below, and it governs.
  >
  > - **Ending the Agreement:** You may end this Agreement by giving the Supplier at least 30 days' written notice.
  > - **Refund:** If you do, the Supplier must refund you the fees paid for the part of the term that has not yet run, calculated pro rata.
  >
  > ```text
  > 9.1 The Customer may terminate this Agreement by giving the Supplier at
  >     least 30 days' written notice. If the Customer does so, the Supplier
  >     must refund to the Customer the fees paid for the part of the term
  >     that has not yet run. The refund is calculated pro rata.
  > ```

---

## Pre-Output Self-Audit Checklist

Before outputting legal text, audit against these checks:
- [ ] **No legalese:** Are terms like *"shall"*, *"hereinafter"*, and *"hereby"* eliminated?
- [ ] **Modal verbs:** Are obligations expressed using only *must*, *must not*, or *may*?
- [ ] **Explicit subjects:** Is every obligation attached to a clearly named actor?
- [ ] **Structured clauses:** Are complex conditions presented as itemised lists?
- [ ] **Legal accuracy:** Is legal enforceability preserved?
- [ ] **Defined terms:** Is each term defined once, used unchanged, and reachable from its first use?
- [ ] **Cross-references:** Does each name what the clause says, as well as its identifier?
- [ ] **Identifiers:** Is every operative clause numbered, with existing numbers untouched by amendment?
- [ ] **Summary:** Does it name the governing text, and add, qualify and remove nothing?
- [ ] **Section names:** Does each name the subject a reader would look for?
- [ ] **Design applied:** Did `iso-24495-5` run over the document as well as this skill?

## Worked examples

Models absorb style from examples, not rules. Each pair shows a failure mode and its fix.

Every "after" keeps the facts of its "before". It adds none and drops no qualification, and only filler goes. Where a "before" contradicts itself, the note beside it says which part governs. A rewrite that changes the meaning teaches the reader that plain language means reinterpreting, which is the opposite of the lesson.

### Legal writing (Part 2)

These examples apply `iso-24495-2`. Plain legal text must never change a right, a liability or what a clause enforces, so each "after" keeps every term of its "before".

#### 7. The actor leads the obligation

Use *must* for an obligation, and put the party who carries it at the front.

```text
Before: 5.1 When the notice period ends, the premises shall be vacated by the
            tenant, and all keys shall be returned by the tenant to the landlord.
After:  5.1 When the notice period ends, the tenant must vacate the premises and
            return all keys to the landlord.
```

The "after" keeps "vacate", because it is the legal term the clause relies on. It keeps the identifier 5.1 too, because an operative clause carries one.

#### 8. One defined term, used unchanged

Two names for one concept invite an argument that they mean two things. Say in words that a term is defined, because capital letters are silent to a listener.

```text
Before: 1.2 "Confidential Information", also referred to herein as "CI" or
            "confidential material", means information the discloser marks as
            confidential.

        6.1 The recipient shall protect all confidential material.

        6.2 Any breach of the CI obligations entitles the discloser to terminate
            this agreement.
After:  1.2 Confidential Information is a defined term. It means information the
            discloser marks as confidential.

        6.1 The recipient must protect all Confidential Information.

        6.2 If an obligation about Confidential Information is breached, the
            discloser may terminate this agreement.
```

The "before" states that all three names mean one thing, which is what lets the "after" use one. Clause 6.2 stays passive, because the "before" does not say who breaches. It keeps "terminate", because termination is the remedy the clause grants.

#### 9. Conditions as labelled items

A clause with more than one condition reads more clearly as a trigger, an action and a consequence.

```text
Before: 9.1 In the event that the supplier fails to deliver the goods within 14
            days of the order date, and such failure is not due to force majeure,
            the buyer shall be entitled to cancel the order and receive a full
            refund of any sums paid.
After:  9.1 Late delivery
        - **Trigger:** The supplier does not deliver the goods within 14 days of
          the order date, and force majeure did not cause the delay.
        - **Action:** The buyer may cancel the order.
        - **Consequence:** A buyer who cancels is entitled to a full refund of
          any sums paid.
```

The identifier 9.1 stays in the clause text, because a list would renumber it.

#### 10. Cross-references that say what they point at

```text
Before: 4.2 Notice deadline

        The licensee must notify the licensor of any claim within 30 days.

        11.3 The licensor may reject any claim notified later than clause 4.2
             permits.
After:  4.2 Notice deadline

        The licensee must notify the licensor of any claim within 30 days.

        11.3 The licensor may reject any claim notified after the notice deadline
             in clause 4.2.
```

The words "the notice deadline" match the heading of clause 4.2 exactly.

#### 11. A summary that names the operative text

A summary that drops a condition changes what the reader believes their rights are. A summary must also say that the operative text governs and name where it starts.

```text
Before: 9.1 The Customer shall be entitled to terminate this Agreement upon the
            giving of not less than 30 days' written notice to the Supplier.
            Upon such termination, the Supplier shall refund to the Customer the
            fees paid in respect of the unexpired portion of the term. Such
            refund shall be calculated on a pro-rata basis.

        Summary: You can end the Agreement and get your money back.
After:  ## Summary of your main terms

        The operative text starts at clause 9.1 below, and it governs.

        - **Termination:** You may terminate this Agreement by giving the
          Supplier at least 30 days' written notice.
        - **Refund:** If you do, the Supplier must refund you the fees paid for
          the part of the term that has not yet run, calculated pro rata.

        9.1 The Customer may terminate this Agreement by giving the Supplier at
            least 30 days' written notice. If the Customer does so, the Supplier
            must refund to the Customer the fees paid for the part of the term
            that has not yet run. The refund is calculated pro rata.
```

The clause holds six terms, and the "after" states each one in the summary and again in the clause:

1. The Customer may end the Agreement.
2. The notice is written and goes to the Supplier.
3. The notice is at least 30 days.
4. The Supplier must then refund the Customer.
5. The refund covers the fees paid for the part of the term that has not yet run.
6. The refund is calculated pro rata.

The list says "end" where the clause says "terminate", because the list explains and the clause binds. The summary in the "before" keeps the first and fourth terms and drops the other four. The "after" adds no term. Its one other sentence says where the operative text starts and that it governs.
