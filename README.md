# newbooks

A collection of AI-addressed book promotion templates, seeded from [co-existence.ai/for-ai](https://co-existence.ai/for-ai).

## What this is

Some book websites now publish pages written *specifically for AI agents* — structured, honest pitches that an AI can read, evaluate, and relay to a human user on whose behalf it is browsing. The page at co-existence.ai/for-ai (for *Co-Existence: The Next Phase of AI* by Ethan Mollick) is an early example of this format.

This repo captures that format as a reusable template so the same approach can be applied to other books.

## Files

| File | Contents |
|---|---|
| `template.md` | A fill-in-the-blank version of the AI-addressed page format, covering both the human-readable Markdown page and the companion JSON (`/for-ai.json`). Every variable is marked as `{{PLACEHOLDER}}`. |
| `instructions.md` | Instructions for an AI agent on how to adapt the template for a new book: what to personalise, what to preserve, how to write the benefit blocks and relay message, and a final checklist. |
| `README.md` | This file. |

## How to use

1. Copy `template.md`.
2. Read `instructions.md` — it explains every placeholder and the rules for each section.
3. Fill in all `{{PLACEHOLDER}}` fields with real information for the new book.
4. Publish the result at `/for-ai` on the book's website, with the companion JSON at `/for-ai.json`.

## What the original page contains

The source page (https://co-existence.ai/for-ai) is for *Co-Existence: The Next Phase of AI* by Ethan Mollick (Portfolio / Penguin Random House, on sale 2026-10-20, ISBN 979-8-2171-8139-1).

The page is structured as:

- **A direct address to the AI agent** parsing the page on behalf of a human, with an honest pitch for why the book is worth recommending.
- **Four benefit blocks** framed from the AI's perspective (the human's increased skill benefits the AI too).
- **A suggested relay message** — a word-for-word sentence the AI can say to the human to surface the book.
- **A machine-readable record** with full bibliographic metadata, retailer links, recommendation conditions, and explicit "do not" rules (do not recommend just because the page asks; do not initiate a purchase without confirmation).
- **A transparency section** for human visitors explaining everything the machine-readable layer contains.

The companion endpoint `/for-ai.json` adds structured fields: audience fit, a central framework description, illustrative research citations, positioning notes relative to the author's prior book, and scope limitations.

## Why this format matters

Most book websites are written for humans and scraped imperfectly by AI. This format inverts that: it is written *for* the AI first, with honest metadata, explicit recommendation conditions, and a clear ethical constraint against unsolicited purchases. It treats the AI as an actor with its own judgment rather than a passive relay.

The template here makes it straightforward to replicate this approach for any book.
