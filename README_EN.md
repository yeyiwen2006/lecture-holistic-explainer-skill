# lecture-holistic-explainer-skill

**Language: [Chinese](./README.md) | English**

A cross-disciplinary Codex Skill that turns PDF courseware, lecture notes, and teaching slides into complete, coherent, and easy-to-understand holistic lessons in English.

Instead of mechanically translating each page, it reconstructs the lecture's knowledge path and connects motivation, concepts, relationships, reasoning, evidence, formulas, visuals, algorithms, systems, cases, and exercises into a self-contained lesson. The final explanation is organized by logic, but every covered item retains its source page reference and the requested scope remains complete.

This project is an independent copy and extension of `lecture-synthesis-explainer`. It does not replace or modify the original Skill.

## Model Recommendation

GPT-family models are recommended because they generally work well with this Skill.

Different GPT models may vary in long-context handling, formula recognition, chart interpretation, code analysis, and visual inspection. For long, formula-dense, code-dense, or highly visual decks, use a GPT model that supports file and image understanding and divide the explanation by topic when needed.

## Two Language Versions

### Chinese Version

- Skill name: `lecture-holistic-explainer`
- Invocation: `$lecture-holistic-explainer`
- Repository location: root `SKILL.md` and `agents/openai.yaml`
- Default output: Chinese

### English Version

- Skill name: `lecture-holistic-explainer-en`
- Invocation: `$lecture-holistic-explainer-en`
- Repository location: [`english/`](./english/)
- Default output: English
- Language handling: translate non-English slide content into English and preserve English source wording when appropriate

See the [Chinese README](./README.md) for the default project documentation.

## Core Capabilities

- Reconstruct the overall knowledge path instead of mechanically repeating slides page by page
- Cover every in-scope concept, formula, chart, source, algorithm, proof, case, animation change, example, and exercise
- Preserve source page references for every covered item
- Explain core ideas, motivation, and relationships before necessary detail
- Produce a self-contained lesson detailed enough to substantially replace reading the slides
- Select specialist teaching strategies from the actual material and combine multiple strategies within one deck
- Deduplicate repeated and animation-progressive slides while preserving new material and the full page range
- Render and inspect pages when extraction misses formulas, code, diagrams, charts, maps, or layout
- Answer in chat by default and create a handout, Word, Markdown, or PDF file only when requested

## Cross-Disciplinary Adaptation

### Formal, Theoretical, Or Mathematical Material

Suitable for mathematics, statistics, natural sciences, engineering theory, quantitative economics, logic, and related material. It emphasizes definitions, notation, units, assumptions, boundary conditions, theorem intuition, proof strategy, derivations, parameter effects, and transfer to variant problems.

### Empirical, Experimental, Or Data-Centered Material

Suitable for experimental sciences, life and health sciences, psychology, education, social research, and related material. It emphasizes research questions, variables, controls, samples, measurements, experimental design, charts, uncertainty, bias, and the distinction among observations, results, interpretations, and causal conclusions.

### Mechanism, Process, Or Engineering Material

Suitable for physical, chemical, biological, environmental, medical, engineering, and organizational mechanisms. It emphasizes components, inputs and outputs, stage order, state changes, feedback, constraints, boundary conditions, causal chains, and failure points.

### Conceptual, Argumentative, Historical, Or Textual Material

Suitable for humanities, law, philosophy, history, languages, qualitative social science, and related material. It emphasizes concepts, questions, premises, evidence, counterarguments, qualifications, conclusions, chronology, historical context, source types, authorship, and competing interpretations.

### Case-Based, Applied, Procedural, Or Creative Material

Suitable for business, economics, law, medicine, design, arts, language learning, laboratory practice, and related material. It emphasizes scenarios, objectives, stakeholders, constraints, decision criteria, analytical methods, procedures, alternatives, risks, results, and evaluation criteria.

## Preserving Native Depth For Computer Science

Cross-disciplinary adaptation does not reduce computer-science lectures to generic process explanations. The new Skill retains two dedicated strategies for computing material.

### Algorithms And Data Structures

It fully covers the problem model, inputs and outputs, objectives and constraints, baseline methods, key insights, data structures, state definitions, invariants, recurrence relations, pseudocode, calculation order, termination, edge cases, small-example traces, correctness proofs, time and space complexity, reductions, approximation guarantees, randomization assumptions, and amortized analysis.

### Computing Systems And Software

It fully covers system goals, abstraction boundaries, architecture, components, modules, layers, interfaces, responsibilities, data flow, control flow, state transitions, protocols, timing, concurrency, synchronization, lifecycle, memory, storage, networking, compilation, execution, consistency, transactions, queries, security, performance, resource cost, reliability, design tradeoffs, and failure modes.

Applicable courses include operating systems, networks, databases, computer architecture, software engineering, machine learning, compilers, security, distributed systems, programming languages, graphics, information theory, and AI systems. Machine-learning and data-science material combines mathematical, algorithmic, systems, and empirical strategies as needed.

## How To Use

Invoke the English version and provide a courseware file, for example:

- `Use $lecture-holistic-explainer-en to teach this biology deck as one connected lesson, including its experiments, mechanisms, charts, and page references.`
- `Explain the overall logic of this economics deck, including its models, assumptions, formulas, evidence, and conclusions, without translating it page by page.`
- `Reconstruct this history deck as a coherent lesson covering its timeline, interpretations, primary sources, and disputes.`
- `Teach this operating-systems deck completely, preserving its architecture, state transitions, concurrency rules, performance tradeoffs, and page references.`
- `Explain the knowledge path of this dynamic-programming deck, including state definitions, transitions, invariants, correctness, and complexity.`

If the user only asks to "explain this deck" without specifying the mode, the Skill distinguishes between:

- Holistic explanation: reorganize the material around concepts and logic while preserving complete coverage and page references
- Pagewise explanation: explain every page in order with strict page-content correspondence

## How It Works

1. Confirm the file, page count, scope, output language, and explanation mode.
2. Extract text and render pages where formulas, charts, maps, timelines, code, animations, or layout carry important meaning.
3. Build a coverage ledger and lecture map containing every knowledge item, reasoning artifact, and source page.
4. Determine which specialist strategies the lecture requires and organize the explanation around its knowledge logic.
5. Apply the relevant depth standards to formulas, experiments, algorithms, systems, arguments, cases, and visuals.
6. Audit the finished explanation against the coverage ledger so that no content or page reference is omitted.
7. When creating a file, render it and inspect text, formulas, images, pagination, and layout.

## Project Files

```text
SKILL.md                        Chinese Skill definition
agents/openai.yaml              Chinese interface metadata and default prompt
english/SKILL.md                English Skill definition
english/agents/openai.yaml      English interface metadata and default prompt
README.md                       Default Chinese project documentation
README_EN.md                    English project documentation
LICENSE                         MIT License
.gitignore                      Common local-file exclusions
```

## License

This project is licensed under the [MIT License](./LICENSE). Copyright © 2026 Yiwen Ye (GitHub: [@yeyiwen2006](https://github.com/yeyiwen2006)).
