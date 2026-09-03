---
name: lecture-holistic-explainer
description: Turn local lecture PDFs, slide decks, and courseware from any course domain into self-contained, easy-to-understand Chinese holistic lessons that reconstruct the overall knowledge path without requiring page-by-page correspondence. Use when the user wants the motivation, concepts, reasoning, evidence, formulas, diagrams, algorithms, systems, cases, and exercises taught as one coherent lesson, with source page references for every covered item. Preserve specialist depth for theoretical, algorithmic, computing-systems, empirical, argumentative, and applied material. If the user only asks to explain a lecture PDF and does not specify holistic versus pagewise coverage, ask which mode they want.
---

# Lecture Holistic Explainer

## Overview

Use this skill to transform a local lecture PDF, slide deck, or courseware file into a coherent Chinese teaching explanation. Rebuild the lecture's knowledge path so the learner understands what problem the material addresses, why each idea appears, how the ideas connect, what evidence or reasoning supports them, and how to use them without needing to reopen the slides for the core content.

Holistic explanation is not a high-level summary. It may reorganize pages by concept and logic, but it must preserve all in-scope knowledge: definitions, claims, sources, formulas, notation, diagrams, datasets, experiments, algorithms, code, proofs, mechanisms, cases, animation changes, examples, and exercises or problems. Every covered item must retain its source page reference.

Keep explanations complete but not bloated. Explain the core idea first, then include enough intermediate reasoning, slide examples, formulas, diagrams, evidence, and problem context for the lesson to substantially replace reading the original slides. Remove only irrelevant background, repeated wording, and digressions that do not help the learner understand the lecture.

The primary goal is fast, genuine understanding. When a learner may be seeing an idea for the first time, preserve the bridge that makes it understandable: the problem being solved, the simple mental model, prerequisite concepts, relationships among terms, the meaning of each important symbol, code line, arrow, source, or data series, a small concrete example, and the rule for applying the idea.

Priority rule: within the user's requested scope and all higher-level constraints, the highest priority is "clear, easy to understand, and no in-scope knowledge point is missed." The second priority is "concise, non-repetitive, and not needlessly verbose." Do not sacrifice concept bridges, reasoning, evidence, formulas, diagrams, examples, specialist depth, or coverage merely to make the explanation shorter.

Teaching-depth rule: explain the full logic of each knowledge point before compressing routine detail. Clarify its purpose, assumptions or context, relationship to earlier and later material, key reasoning or evidence, applicability, and transfer to variants. Compress mechanical algebra, arithmetic, routine matrix multiplication, repetitive substitution, long case enumeration, and duplicated wording unless a step changes the interpretation or is a common source of error.

Generalization must not flatten specialist material. Infer the actual discipline and content types from the slides, use the appropriate strategies below, and preserve field-specific terminology, conventions, proof standards, algorithmic reasoning, system behavior, evidence standards, or interpretive context. A single lecture may require several strategies.

For lower-priority or non-exam-focused topics, still explain their basic logic and relationship to the lecture path. Mark them as lower priority when appropriate, but do not reduce them to labels unless the slides contain only a passing mention.

Use this skill for whole-lecture or whole-topic explanation. Do not use it when the user asks for page-by-page translation, page-by-page explanation, or strict page-content correspondence; use `$lecture-pagewise-explainer` instead.

The output surface follows the user's instruction:

- If the user asks to explain the material or explain it in chat, answer directly in the conversation.
- If the user asks for notes, a handout, Markdown, Word, PDF, or another file, create that artifact rather than only answering in chat.
- Do not create files when the user only wants an in-chat explanation.

When creating a document artifact, make it self-contained enough to replace the original slides in the requested scope. Include necessary slide images, diagrams, tables, code screenshots, maps, timelines, plots, or visual fragments when text alone would make the explanation difficult to understand. Do not add decorative images that carry no teaching value.

## Skill Selection Rule

- Use this skill when the user explicitly asks for an overall explanation, holistic lesson, synthesis, conceptual storyline, connected knowledge path, or a complete and easy explanation that does not need strict page-by-page structure.
- Use `$lecture-pagewise-explainer` when the user explicitly asks for every page, page-by-page translation, page-by-page explanation, or strict page-number correspondence.
- If the user only says "解释这个课件", "讲解这个 PDF", or otherwise leaves the mode ambiguous, ask them to choose between:
  - holistic explanation: reorganize the material around its ideas and logic while preserving page references and complete coverage;
  - pagewise explanation: explain each page in order with strict page-content correspondence.

## Course And Content Strategy Router

Classify the lecture by the material it actually contains, not by a single course label. Combine strategies when a deck mixes theory, code, experiments, systems, cases, or arguments.

### Formal, Theoretical, Or Mathematical Material

For mathematics, statistics, natural sciences, engineering theory, quantitative economics, logic, and other formal material, emphasize:

- definitions and why each definition is needed;
- symbols, assumptions, units, domains, and boundary conditions;
- theorem or rule statements and their intuitive meaning;
- proof strategy, decisive logical steps, and conclusion;
- formulas, derivations, models, and parameter effects;
- a small worked example when it reveals the pattern;
- common confusions, applicability, and transfer to variant problems.

Do not compress a proof or derivation so aggressively that the key idea disappears. Compress only routine manipulation after explaining what the step accomplishes.

### Algorithms And Data Structures

Preserve the original specialist depth for algorithms and data structures. Explain:

- the problem model, input, output, objective, and constraints;
- the naive or baseline method and why it is insufficient;
- the key algorithmic insight and how the lecture arrives at it;
- data structures, state definitions, invariants, recurrence relations, pseudocode, and calculation order;
- base cases, termination, edge cases, and implementation pitfalls;
- a step-by-step trace on a small example;
- correctness intuition or proof;
- time and space complexity, including what operation or input parameter is being counted;
- reductions, approximation guarantees, randomization assumptions, or amortized reasoning when present.

Examples include algorithm design and analysis, data structures, graph algorithms, dynamic programming, greedy methods, divide and conquer, randomized algorithms, approximation algorithms, computational complexity, automata, and formal languages.

### Computing Systems And Software

Preserve specialist depth for computing systems, software, and AI courses. Explain:

- the system goal, abstraction boundary, and why the design is needed;
- architecture, components, modules, layers, interfaces, and ownership of responsibilities;
- data flow, control flow, state transitions, protocols, timing, concurrency, synchronization, and lifecycle;
- memory, storage, networking, compilation, execution, consistency, transactions, queries, or security rules when relevant;
- code, pseudocode, configuration, schemas, or traces line by line when their details carry meaning;
- performance metrics, complexity, resource costs, reliability, security, and design tradeoffs;
- failure modes, edge cases, and how the system responds;
- one concrete end-to-end walkthrough that connects components and rules.

Examples include operating systems, networks, databases, computer architecture, software engineering, machine learning, compilers, security, distributed systems, programming languages, graphics, information theory, and AI systems. For machine learning or data science, combine this strategy with the formal and empirical strategies as needed.

### Empirical, Experimental, Or Data-Centered Material

For laboratory sciences, life and health sciences, psychology, education, social research, and other evidence-centered material, explain:

- the research question, hypothesis, and why the study or experiment is designed this way;
- variables, controls, samples, measurements, procedures, comparison groups, and sources of bias;
- table columns, chart axes, units, trends, uncertainty, effect sizes, and statistical meaning;
- the difference between observations, results, interpretations, and causal claims;
- limitations, confounders, generalizability, and what the evidence does or does not establish;
- how each experiment or dataset advances the lecture's overall argument.

### Mechanism, Process, Or Engineering Material

For physical, chemical, biological, environmental, medical, engineering, and organizational mechanisms, explain:

- the entities or components and the role of each one;
- inputs, outputs, stages, state changes, feedback, and causal links;
- the order in which the process unfolds;
- conservation rules, constraints, boundary conditions, or failure points;
- arrows, layers, cycles, spatial relationships, and time-dependent behavior;
- a small walkthrough showing how the mechanism produces an outcome.

### Conceptual, Argumentative, Historical, Or Textual Material

For humanities, law, philosophy, history, language, and qualitative social science, explain:

- the central question, thesis, concept, rule, or interpretive problem;
- how key terms differ and relate in their historical or disciplinary context;
- premises, evidence, examples, counterarguments, qualifications, and conclusions;
- chronology, causation, perspective, source type, authorship, and relevant context;
- the difference between what the slide or cited author states and what the explanation infers;
- competing interpretations and what evidence would favor one over another;
- how each text, event, quotation, or case advances the lecture's larger line of thought.

### Case-Based, Applied, Procedural, Or Creative Material

For business, economics, law, medicine, design, arts, language learning, laboratory practice, and other applied material, explain:

- the scenario, objective, stakeholders, constraints, and decision or performance criteria;
- the analytical framework, procedure, demonstrated technique, or creative method;
- how the case or example applies the preceding concepts;
- alternatives, tradeoffs, risks, failure modes, and common mistakes;
- what the learner should be able to recognize, decide, produce, interpret, or perform afterward.

## Workflow

1. Identify the target file, requested scope, and whether the user wants holistic or pagewise explanation. Ask only when one of these materially changes the task and remains ambiguous.
2. Briefly explain why local extraction, rendering, or visual inspection is needed before using tools.
3. Extract page count and text locally with available PDF tools such as `pypdf` or PyMuPDF. Use UTF-8 for text output.
4. Check extraction quality. Render and inspect pages that contain dense formulas, diagrams, charts, maps, timelines, code, animation changes, or visually important layout, especially when extracted text is sparse or garbled.
5. Build a coverage ledger and lecture map before writing:
   - title, main question, and overall topic;
   - learning goals and prerequisite concepts;
   - the mixture of content strategies required;
   - every concept, claim, source, formula, diagram, dataset, experiment, algorithm, code block, system mechanism, proof, case, example, exercise, or problem, with page numbers;
   - the teaching purpose of each major slide group;
   - notation, pseudocode, tables, graph or geometry layouts, highlights, arrows, and annotations that text extraction may lose;
   - how the lecture progresses from motivation to conclusion;
   - repeated pages and animation increments, distinguishing new information from repeated context.
6. Determine the output form from the user's request:
   - for chat explanations, answer in the conversation with clear sections and page references;
   - for document artifacts, create the requested file, render or export it, and visually validate the final result;
   - for an ambiguous request for "讲义", prefer a file artifact and ask only if the required file type cannot be inferred.
7. Organize the lesson by concepts and reasoning rather than mechanically following page order. Use page order as evidence of the lecture's intended progression, and attach page references to every covered item.
8. Select only teaching-relevant visuals. Include diagrams, tables, code screenshots, maps, timelines, plots, layouts, or multi-step examples when they are necessary for understanding. Caption them in Chinese and explain what the learner should notice.
9. Write in a teaching order appropriate to the material:
   - overall storyline and central problem;
   - learning goals and necessary background;
   - core concepts and relationships;
   - key reasoning, evidence, formulas, mechanisms, algorithms, systems, proofs, or arguments;
   - important examples, cases, experiments, visuals, or exercises;
   - how the parts connect;
   - common confusions, applicability, and final synthesis.
10. Make every major topic self-contained. Explain its motivation, definitions, relationships, workflow or reasoning, decisive evidence or symbolic step, applicability, tradeoffs or limitations, and a concrete example when useful.
11. Keep the lesson readable. Prefer focused paragraphs, compact tables, structured bullets, and small worked examples over long textbook-style exposition, but never compress away required knowledge or specialist reasoning.
12. If the scope is too large for one response, split the lesson into ordered parts by topic range. State what each part covers and continue the full coverage; do not replace later material with a brief summary.
13. Before finishing, audit the lesson against the coverage ledger. Every in-scope item must be explained, explicitly identified as repeated, or carefully marked unreadable, with page references preserved.

## Explanation Standards

### Completeness And Length

For every knowledge point, state the core idea in plain Chinese before adding detail. Then include enough explanation for a first-time learner to understand what the slides are teaching, why the material matters, how the pieces connect, and how the idea is applied.

Do not output only a review outline, list of takeaways, or executive summary when the user asks for a complete lecture explanation. "Concise" means removing irrelevant background and repetitive wording; it does not mean omitting formulas, arguments, evidence, diagrams, animation increments, proof ideas, code behavior, system rules, examples, cases, or problems.

If a topic has many details, separate "核心思想" from "展开说明" or "补充细节" so the learner can grasp the main point quickly without losing completeness.

### Page References And Coverage

Attach page references in parentheses to every concept, claim, source, formula, diagram, dataset, experiment, algorithm, code block, proof idea, mechanism, case, animation change, example, and exercise or problem, for example `主定理（第 12 页）` or `实验结果与限制（第 18-20 页）`.

Do not omit review questions, examples, counterexamples, visual highlights, small problem statements, citations, or intermediate animation states merely because the lesson is organized holistically. Group related pages when useful, but preserve the full page range and explain what each increment contributes.

### Concepts And Relationships

For each new concept, give its formal slide meaning, a plain Chinese explanation, why it appears, how it supports later material, and its page reference.

When several terms depend on one another, build a relationship map before explaining details. Clarify which terms are objects, properties, operations, rules, conditions, evidence, or conclusions, and show their hierarchy, opposition, sequence, or causal relationship.

### Claims, Arguments, Sources, And Context

Identify the question, thesis or conclusion, premises, evidence, counterarguments, qualifications, and reasoning link. Distinguish slide claims, cited-author claims, historical sources, observed evidence, and the explanation's own inference. Do not turn a contested interpretation into an uncontested fact.

### Formulas And Quantitative Models

For every important formula, explain the notation, symbol meanings, units, intuition, derivation or use, applicability conditions, parameter effects, and page reference. Include a small example or decisive intermediate step when it reveals the pattern.

For counting, capacity, conversion, probability, rate, or representation formulas, name exactly what is being counted or measured, convert units explicitly, and explain the inverse question when useful. Compress routine simplification only after the conceptual step is clear.

### Data, Experiments, And Charts

Explain what was measured or compared, how to read axes, legends, tables, uncertainty, and experimental setup, what pattern is visible, and what conclusion is warranted. Preserve the distinction between correlation, causation, estimate, uncertainty, and interpretation.

### Algorithms, Data Structures, And Code

Explain the input, output, objective, state definitions, invariants, data structures, pseudocode or code behavior, base case or termination, calculation order, correctness, complexity, edge cases, and page reference. Trace a small example when it exposes hidden state changes or control flow.

### Computing Systems And Software

Explain abstraction boundaries, components, interfaces, data and control flow, state or protocol transitions, concurrency or timing, resource costs, tradeoffs, and failure behavior. When code, memory layouts, schemas, query plans, network exchanges, or execution traces are present, connect each meaningful detail to the system's overall behavior.

### Proofs And Derivations

Identify the proof strategy or derivation goal, assumptions, decisive steps, conclusion, and page reference. Preserve central induction, contradiction, reduction, recurrence, algebraic, geometric, probabilistic, or structural reasoning. Use narrative to connect equations instead of presenting an uninterrupted formula dump.

### Mechanisms And Processes

Name the parts, inputs, outputs, stages, transitions, feedback, and causal links. Explain the order of events and why the mechanism produces the observed or intended outcome.

### Cases, Procedures, And Creative Work

Explain the scenario, criteria, method, decisions, evidence, alternatives, tradeoffs, and result. For procedures or demonstrations, state what the learner must recognize or perform and where mistakes commonly occur.

### Diagrams, Visuals, And Animations

Describe what each visual shows, why it matters, and where it appears. Explain arrows, labels, legends, maps, timelines, spatial layout, highlights, and newly added animation elements. Include the visual in a document artifact when text alone would be insufficient, but still explain it in words.

### Examples And Exercises

Explain what every example demonstrates and why it appears at that point. Include a worked example when the slides contain one, imply one, or the topic is abstract. If solving exercises is requested, identify the relevant concept or method, state the given information, show the decisive reasoning, and preserve the problem's page reference.

## Recommended Structure For Holistic Lessons

Use this general shape when it matches the lecture:

```markdown
**整体主线**
用几句话说明这套课件试图解决什么问题，以及知识如何展开。

**1. 学习目标与必要背景**
...

**2. 核心概念与关系**
...

**3. 知识如何展开**
按概念和逻辑组织，而不是逐页翻译；每个知识点保留页码。

**4. 重点推理 / 公式 / 证据 / 机制 / 算法 / 系统 / 论证**
只保留课件实际需要的类别，并完整解释其逻辑。

**5. 例子 / 案例 / 实验 / 习题**
复现关键材料并解释它为什么出现。

**6. 易混点、适用范围与限制**
...

**一句话总结**
...
```

Adapt the structure to the lecture:

- For algorithms, include problem model, baseline, key insight, state and pseudocode, trace, correctness, complexity, and edge cases.
- For computing systems, include goals, abstractions, architecture, data or control flow, protocols or state, tradeoffs, performance, and failures.
- For theoretical material, include definitions, theorem or rule statements, assumptions, proof or derivation strategy, formulas, and examples.
- For empirical material, include the research question, design, variables, data reading, findings, uncertainty, causal limits, and implications.
- For argumentative or historical material, include context, concepts, thesis, evidence, counterarguments, source interpretation, and conclusion.
- For applied or creative material, include the scenario, criteria, method, decisions, alternatives, result, and evaluation.

## Accuracy Checks

Before finalizing:

- Confirm page count, requested scope, output language, and output format.
- Confirm the user wanted holistic rather than pagewise explanation.
- Confirm that extraction did not hide a diagram-heavy, formula-heavy, code-heavy, map-heavy, or data-heavy page.
- Confirm all in-scope concepts, claims, sources, formulas, diagrams, datasets, experiments, algorithms, code blocks, proofs, mechanisms, cases, animation changes, examples, and exercises have explanations and page references.
- Confirm discipline-specific terminology, names, dates, units, notation, source attribution, and technical claims are accurate and readable.
- Confirm computer-science material retains algorithmic, code-level, systems, correctness, complexity, architecture, protocol, tradeoff, and failure-mode detail when present.
- Confirm English source content has been translated or explained in Chinese when needed, while Chinese source wording is preserved appropriately.
- Confirm repeated framework or animation pages are not redundantly explained, while their page numbers and new contributions are preserved.
- Confirm outside knowledge is clearly separated from slide content and uncertain interpretation is labeled.
- Confirm the lesson is detailed enough to substantially replace reading the slides, not merely serve as an outline.
- Perform a first-time-learner pass: add a short explanation or example wherever a sentence relies on an unexplained term, hidden calculation, diagram convention, source context, or assumed background concept.
- For document artifacts, render and visually inspect the result for clipped text, overlap, missing images, unreadable Chinese, broken captions, and excessive blank pages.

## Failure Handling

- If text extraction fails, try another local PDF tool or render pages visually.
- If formulas, code, maps, charts, or diagrams are corrupted, rely on rendered-page inspection when possible.
- If a source or visual cannot be read clearly, state what is unreadable and explain only the visible or extractable content.
- If the answer is too long, split it into ordered parts and preserve the full coverage plan instead of compressing later topics into a short summary.
