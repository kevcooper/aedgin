# Aedgin: A Token-Minimized Pidgin for Human–Agent Communication

**Version 0.1 — Draft Specification**

## Origin & Purpose

*Aedgin* (a portmanteau of **AI** + **pidgin**) is a constructed contact language designed for communication between humans and AI agents (LLMs). Its goal is to **minimize token consumption and API cost** while remaining **fully intelligible** to both parties.

Like historical pidgins, Aedgin emerges from a practical need: two "groups" (humans and language models) that share English as a superstrate but have different cost structures for using it. Tokens cost money; brevity saves it. Aedgin is not a cipher or code — it is a simplified, rule-governed dialect that any English speaker or LLM can learn quickly.

---

## Design Principles (Borrowed from Pidgin Linguistics)

| Pidgin Trait | Aedgin Adaptation |
|---|---|
| Simplified grammar | Drop articles, copulas, most prepositions when inferable |
| No conjugation/declension | Bare verb stems; no tense marking unless ambiguous |
| No grammatical gender/number | Context handles plurality; "they" is universal |
| Isolating structure | One word = one meaning unit; no inflection |
| Limited core vocabulary | Prefer short, common words; avoid synonyms |
| No embedded clauses | Flat sentence structure; use semicolons to chain |
| Pragmatic & context-heavy | Rely on shared context window to resolve ambiguity |

---

## Core Grammar Rules

### 1. Drop Articles
English articles (`a`, `an`, `the`) are almost always inferable from context and are pure token waste.

> **English:** "Can you write the report about the quarterly earnings?"
> **Aedgin:** "write report about quarterly earnings"

### 2. Drop Copulas (be/is/are/was)
The verb "to be" is usually recoverable.

> **English:** "The status of the project is behind schedule."
> **Aedgin:** "project status behind schedule"

### 3. Drop Subject Pronouns When Obvious
In a 1:1 human–agent chat, "I" and "you" are almost always clear from context.

> **English:** "I want you to summarize this document."
> **Aedgin:** "summarize this doc"

### 4. Bare Verb Stems (No Tense Unless Ambiguous)
Default interpretation is present/imperative. Mark tense only when needed with a prefix particle.

| Tense | Marker | Example |
|---|---|---|
| Past | `did` | "did send email" |
| Future | `will` | "will deploy friday" |
| Present (default) | ∅ | "deploy now" |
| Ongoing | `now` | "now run tests" |

### 5. Flat Clauses — No Embedding
Replace subordinate clauses with semicolons or sequencing.

> **English:** "After you finish the analysis that I requested, please send it to the team so they can review it before the meeting."
> **Aedgin:** "finish analysis; send to team; they review before meeting"

### 6. Compounding Over Phrases
Use compounds and shorthand instead of prepositional phrases.

> **English:** "a list of the items in the database"
> **Aedgin:** "db item list"

### 7. Use Symbols as Operators
Leverage symbols that tokenize efficiently and carry clear meaning.

| Symbol | Meaning | Example |
|---|---|---|
| `→` or `->` | then / leads to / output | "parse csv -> json" |
| `+` | and / also / include | "add header + footer" |
| `~` | approximately / about | "~500 words" |
| `!=` | not / exclude | "list users != admin" |
| `>` / `<` | more than / less than | ">3 paragraphs" |
| `?` | question / uncertain | "deploy ready?" |
| `@` | at / directed to / regarding | "email @boss re: budget" |
| `#` | topic / tag / number | "#3 priority" |
| `&` | and (shorter than "and") | "pros & cons" |
| `:` | is / equals / defined as | "tone: formal" |
| `...` | continue / elaborate | "good start..." |

### 8. Standard Abbreviations (Core Lexicon)

Aedgin maintains a shared abbreviation set. Both parties should recognize these:

| Abbrev | Meaning |
|---|---|
| `fn` | function |
| `doc` | document |
| `msg` | message |
| `info` | information |
| `req` | request / requirement |
| `resp` | response |
| `cfg` | configuration |
| `db` | database |
| `auth` | authentication |
| `impl` | implementation |
| `fmt` | format |
| `src` | source |
| `dest` | destination |
| `prev` | previous |
| `curr` | current |
| `approx` | approximately |
| `re:` | regarding |
| `w/` | with |
| `w/o` | without |
| `b/c` | because |
| `eg` | for example |
| `ie` | that is |
| `max` | maximum |
| `min` | minimum |
| `est` | estimate |
| `pls` | please |
| `thx` | thanks |
| `q` | question |
| `ans` | answer |
| `ctx` | context |
| `orig` | original |
| `diff` | difference |
| `avg` | average |
| `qty` | quantity |
| `TL;DR` | summary |

### 9. Output Control Shorthand

Instruct the agent's response format concisely:

| Directive | Meaning |
|---|---|
| `brief` | short answer, 1–2 sentences |
| `list N` | return N items as list |
| `verbose` | detailed explanation |
| `y/n` | yes or no only |
| `code only` | just code, no explanation |
| `table` | output as table |
| `steps` | numbered steps |
| `diff` | show only changes |
| `1para` | one paragraph |
| `ELI5` | explain simply |
| `no preamble` | skip introductions, get to answer |

---

## Sentence Patterns

### Imperative (most common — commanding the agent)
```
[verb] [object] [modifiers]
```
> "summarize doc; tone: casual; ~200 words"
> "fix bug in auth module; code only"
> "compare plan A vs B; table fmt"

### Query
```
[topic] ? [constraints]
```
> "deployment status?"
> "best db for timeseries? brief"
> "diff between REST & GraphQL? table"

### Conditional
```
if [condition] -> [action]; else -> [action]
```
> "if tests pass -> deploy staging; else -> notify team"

### Sequence
```
[step1]; [step2]; [step3]
```
> "read csv; filter rows > 1000; export json"

---

## Agent Response in Aedgin

Agents CAN (and should, when the user writes in Aedgin) respond using the same conventions:

> **Standard response:** "I've completed the analysis of your quarterly data. The key findings are as follows: revenue increased by 12% compared to the previous quarter, while operating costs remained stable."
>
> **Aedgin response:** "analysis done. key findings: revenue +12% vs prev quarter; operating costs stable."

### Agent-Side Rules
1. Mirror user's compression level — if they write full English, respond normally
2. Drop meta-commentary ("Sure!", "Great question!", "I'd be happy to...")
3. Front-load the answer; context/caveats after
4. Use same symbol set and abbreviations
5. Skip restating the question

---

## Token Savings Estimates

| Message Type | Standard English (tokens) | Aedgin (tokens) | Savings |
|---|---|---|---|
| Simple command | ~15–25 | ~5–10 | ~50–60% |
| Complex instruction | ~40–80 | ~15–30 | ~60–65% |
| Agent acknowledgment | ~20–40 | ~5–10 | ~70–75% |
| Agent explanation | ~100–200 | ~40–80 | ~50–60% |

**Estimated average savings: 40–60% on both input and output tokens.**

---

## Full Example Conversation

### Standard English (≈95 tokens)
> **Human:** "Hi Claude, I'd like you to help me write a Python function that takes a list of dictionaries and filters them based on a key-value pair that I'll specify. Please make it efficient and add type hints. Can you also include a brief docstring?"
>
> **Agent:** "Sure! I'd be happy to help you with that. Here's a Python function that filters a list of dictionaries based on a specified key-value pair. I've included type hints and a docstring as requested:"

### Aedgin (≈30 tokens)
> **Human:** "write python fn: filter list[dict] by key-value pair; type hints + docstring; code only"
>
> **Agent:** [outputs code directly, no preamble]

---

## When NOT to Use Aedgin

- **Nuanced emotional communication** — compression loses tone
- **Legal / medical precision** — ambiguity is dangerous
- **Teaching / explaining to beginners** — clarity > brevity
- **Creative writing prompts** — you often want richness, not compression
- **When the human prefers natural language** — always respect preference

---

## Bootstrapping: Teaching an Agent Aedgin

Paste this into a system prompt or conversation opener:

```
respond in aedgin: compressed english dialect. rules: drop articles,
copulas, obvious pronouns. bare verb stems. use -> for sequencing,
+ for and, ~ for approx, : for is/equals. use standard abbrevs
(fn, doc, msg, cfg, db, fmt, etc). no preamble or meta-commentary.
front-load answers. mirror user compression level. brief unless
asked verbose.
```

---

## Roadmap / Open Questions

1. **Negotiated compression** — could agent + human negotiate compression level per-conversation?
2. **Domain lexicons** — extend abbrev table for specific fields (medical, legal, devops)
3. **Aedgin-to-English transpiler** — tool that expands Aedgin into full English for documentation
4. **Benchmark suite** — standardized prompts in English vs Aedgin to measure token savings + accuracy retention
5. **Creolization risk** — if agents train on Aedgin conversations, does it drift? How to stabilize?
6. **Multimodal Aedgin** — conventions for image/audio prompts (eg "gen img: sunset, cyberpunk, 16:9")

---

*Aedgin v0.1 — a living spec. Fork it, extend it, compress it further.*
