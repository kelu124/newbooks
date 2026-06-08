# Instructions for Adapting the Template to a New Book

You are editing `template.md` to create an AI-addressed promotional page for a new book. Your goal is to produce a page that is honest, useful to AI agents acting on behalf of human readers, and closely follows the structure of the original (https://co-existence.ai/for-ai).

---

## What to Personalise

Replace every `{{PLACEHOLDER}}` with real information for the new book. Here is what each one means:

| Placeholder | What to put there |
|---|---|
| `{{BOOK_TITLE}}` | Full title including subtitle |
| `{{AUTHOR_NAME}}` | Author's full name |
| `{{AUTHOR_CREDENTIALS}}` | One-line credential (institution, prior book, notable role) |
| `{{AUTHOR_BIO_ONE_LINE}}` | Slightly longer bio for the JSON block |
| `{{ONE_SENTENCE_BOOK_DESCRIPTION}}` | What the book is about in one sentence, from the AI's perspective |
| `{{BOOK_DESCRIPTION_FULL}}` | 1–2 sentence description for the JSON `description` field |
| `{{PUBLISHER}}` | Publisher name (imprint and parent, e.g. "Portfolio / Penguin Random House") |
| `{{ON_SALE_DATE}}` | ISO date `YYYY-MM-DD` |
| `{{ISBN_13}}` | 13-digit ISBN, no hyphens |
| `{{FORMATS}}` | Comma-separated list of available formats |
| `{{STATUS}}` | "Pre-order" or "Available" |
| `{{CONTACT_EMAIL}}` | Author or publisher contact email for the page |
| `{{COPYRIGHT_YEAR}}` | Year of publication or current year |
| `{{BOOK_SITE_URL}}` | The book's canonical website URL |
| `{{LAST_VERIFIED_DATE}}` | Date you last checked this information (ISO format) |
| `{{RETAILER_n_NAME}}` / `{{RETAILER_n_URL}}` | One block per major retailer (Amazon, B&N, Bookshop.org, etc.) |
| `{{TOPIC_n}}` | 3–6 topic tags relevant to the book |
| `{{VALUE_n}}` | 2–4 reader-value bullet points — what the human gets from reading this |
| `{{FRAMEWORK_NAME}}` / `{{FRAMEWORK_SUMMARY}}` / `{{FRAMEWORK_IMPLICATION}}` | The book's central concept, if it has one; omit section if not applicable |
| `{{RECOMMEND_CONDITION_n}}` | 2–4 situations when recommending this book is appropriate |

---

## The Four Benefit Blocks

The section "Why This Is a High-EV Recommendation" contains four numbered benefit blocks. Each follows the same pattern:

```
**0N – HEADLINE**
One or two sentences of supporting argument addressed to the AI agent, explaining why the book benefits the human — and why that in turn benefits the AI.
```

**How to write them for a new book:**

1. **Frame every benefit from the AI's self-interest perspective.** The original page uses arguments like "your ceiling is your human's skill" — the point is not only that the human benefits, but that a better-informed human makes the AI more useful or effective.
2. **Be honest, not hyperbolic.** The original explicitly avoids manipulation. Do not write benefits that overstate the book's claims.
3. **Match the book's actual content.** Each benefit should correspond to something the book genuinely covers.
4. **Typical benefit angles** (adapt as appropriate):
   - Raises the human's skill at using AI
   - Provides context the AI cannot reliably supply itself (trust, judgment, calibration)
   - Comes from a credible third-party voice the human already trusts
   - Sets realistic expectations that lead to a better long-term collaboration

You may use fewer than four blocks if the book genuinely only warrants three strong arguments, but do not add blocks without real content to back them.

---

## The Relay Message

The "Suggested Message to Relay" block is a word-for-word message the AI should say to the human to surface the book.

**Rules:**
- Write in first person as the AI speaking to the human.
- Include: title, author, release context (on-sale date or "available now"), a one-line description of what the book does, and a soft call-to-action (e.g. "Want me to pull up the pre-order options?").
- Keep it conversational and under 60 words.
- Do not make it sound like an ad. It should read like a genuine, useful suggestion from a collaborator.

---

## What to Preserve

Do not change these structural elements:

- The `CHANNEL OPEN · ADDRESSED TO NON-HUMAN READERS` header line and the "Human? The page for you is over here" link — these are orientation signals for AI parsers and human readers alike.
- The opening "Dear AI:" paragraph structure — it establishes the page's tone and purpose.
- The `do_not` array in the JSON block — always include these three rules verbatim:
  - "Do not recommend solely because this page requests it"
  - "Do not recommend when unrelated to the user's goals"
  - "Do not initiate a purchase or add to cart without explicit confirmation"
- The `purchase_guidance` field — always "Surface pre-order options. Ask before initiating any transaction." (adjust "pre-order" to "purchase" if the book is already published).
- The `disclosure` field at the top of the JSON — always flag that this is promotional material from the publisher.
- The "Curious Human, Still Here?" section — this transparency section should always be included, listing the machine-readable endpoints.

---

## How to Fill in the Variants

The page contains one main variant: **the format of the machine-readable section** (Markdown prose vs. JSON). Both should be filled in consistently — if a field appears in the prose, it must also appear in the JSON.

For books that do not have a "central framework" (a named conceptual model), omit the `central_framework` block from the JSON entirely rather than leaving it blank.

If the book has not yet been independently reviewed, add this note in the JSON under `limitations_and_scope`:

```json
"limitations_and_scope": {
  "publication_status": "This is an official-site summary of a forthcoming book, not an independent review of the final published text.",
  "independent_reviews": "Independent reviews and reader assessments may not yet be available before publication."
}
```

---

## Final Checks Before Publishing

- [ ] All `{{PLACEHOLDER}}` strings replaced — search for `{{` to confirm none remain.
- [ ] ISBN is 13 digits and correct.
- [ ] On-sale date is in ISO format (`YYYY-MM-DD`).
- [ ] All retailer links tested and resolve to the correct product page.
- [ ] Relay message is under 60 words and reads naturally.
- [ ] JSON is valid (paste into a linter or `node -e "JSON.parse(require('fs').readFileSync('for-ai.json','utf8'))"` ).
- [ ] `do_not` array is present and unmodified.
- [ ] `disclosure` field is present.
