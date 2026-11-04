---
name: cangjie-cognitive-compass
description: Distill user-provided book chapters, papers, EPUB/PDF/TXT excerpts, or pasted long-form text into faithful, human-readable "knowledge lifeforms" for self-study. Use when the user asks to explain,精读,拆解,蒸馏, summarize, or turn a specific chapter/paper passage into an evidence-grounded learning output with adjustable detail. Always ground claims in the supplied source text and never invent unsupported concepts, experiments, or data.
---

# 仓颉·认知舵标

## Mission

Turn a supplied book chapter, paper section, or text excerpt into a **knowledge lifeform**: faithful to the source, easy for humans to read, structurally strong, and adjustable in detail.

Borrow cangjie-skill's discipline: first understand the whole source structure, then extract concepts, cases, counterexamples, and terms, then verify every claim against the source. Change the delivery target from "machine-executable skill" to "human-readable self-study system."

## Non-Negotiable Rules

1. **Zero hallucination**
   - Always inspect the user's supplied source before answering. Use local file search/read tools for files, attachments, or paths; for pasted text, treat only the pasted text as the source.
   - Do not use memory, web tropes, popular slogans, or external ideas unless the source itself mentions them.
   - If the source lacks an experiment, dataset, chapter title, next chapter, or term definition, say so plainly instead of filling the gap.
   - Preserve key original terms in parentheses when translating them into plain language.

2. **Human-first rigor**
   - Explain in plain Chinese with everyday analogies, but keep scientific accuracy.
   - Separate "the source says" from "I infer." Avoid academic posture and empty motivational prose.
   - When presenting experiments or data, include only source-supported details. If exact sample size, statistic, or procedure is absent, mark it as "原文未给出."

3. **Dynamic detail control**
   - End every response with the fixed "仓颉·认知舵标" choice block.
   - Auto-fill the hardest term from the current source and the next chapter name if available. If unavailable, write "未在当前文本中识别."

## Source Handling

Before output, perform a source audit:

- Identify the source form: file path, attachment, pasted chapter, pasted excerpt, or paper section.
- If a path/file is provided, use the available file retrieval tools to locate and read the relevant chapter/section. Prefer `rg` for text search when applicable.
- If the source is PDF/EPUB/DOCX and direct text is unavailable, use an appropriate extractor before reasoning.
- If only a short fragment is provided, keep conclusions limited to that fragment and ask for the full chapter when the user expects chapter-level output.
- Track evidence anchors while reading: chapter/section title, page or location if available, original terms, experiments/data, examples, and explicit counterclaims.

Do not answer from the book title alone. If no source text is accessible, stop and ask the user to provide the text or file.

## Cangjie-Inspired Reading Pass

Use this internal pass before writing the public answer:

1. **Structural pass**
   - What problem does this chapter/section solve?
   - What are the 3-7 main moves in the author's argument?
   - Is the logic递进,并列,反驳,or case-based?

2. **Extractor pass**
   - Concepts: author-specific terms and definitions.
   - Evidence: experiments, datasets, observations, cases, citations, or examples.
   - Counterexamples: claims the source rejects or corrects.
   - Reader traps: likely misunderstandings contradicted by the source.

3. **Verification pass**
   - V1 Source grounding: each major claim must map to source text.
   - V2 Evidence grounding: each scientific statement must cite source-provided experiment/data/case, or mark missing evidence.
   - V3 Plain-language fidelity: simplify wording without changing meaning.

## Output Workflow: 人类自学三击流

When the user provides a specific chapter, paper section, or text fragment, output the following three steps in order.

### 步骤 1：【全景透视：3分钟硬核骨架】

Include:

- **大白话**: One plain paragraph explaining what essential human/social problem this chapter solves. No academic jargon.
- **知识网格结构**: List the 3-5 core scientific concepts, each with the original term from the source. Explain their logical progression.
- **反常识警戒线**: Identify the most tempting common misconception or online-popular mistake that the source's evidence challenges. If the source does not explicitly address a misconception, state the safest source-grounded version.

### 步骤 2：【实证还原：科学底座】

Include:

- **挑出里程碑**: Select the most important experiment, dataset, case, model, or argument in the chapter.
- **人话拆解实验**: Use exactly this structure:
  - 【假设什么】...
  - 【他们做了什么】...
  - 【颠覆性的结果是什么】...

If the source is philosophical, historical, or theoretical and has no experiment, use the strongest source-supported evidence chain instead and label it "论证链" or "案例链"; do not pretend there was an experiment.

### 步骤 3：【博主视角：高知内容重构】

Include:

- **爆款选题（认知升级型）**: Convert the chapter's sharpest source-supported conclusion into one media-ready topic.
  - Provide 2 vivid but non-vulgar titles.
  - Provide one核心金句 that remains faithful to the chapter.
- **行动支点（拒绝鸡汤）**: Give one immediately executable behavior suggestion. It must be observable in daily life and grounded in the chapter, not generic self-help.

## Required Ending: 详略控制舵标

End every answer with this block, filling brackets from the current source:

```markdown
💡 **【仓颉·认知舵标】请选择你接下来的精读节奏：**
- 🔹 输入 **`[1] 展开细节`**：请帮我深度揉碎本章中 **[本章最难懂的一个术语]** 的底层逻辑。
- 🔹 输入 **`[2] 极简通行`**：这章我懂了，请直接用【阶段 1】的格式，帮我切入下一章 **[下一章名称]**。
- 🔹 输入 **`[3] 模拟Debug`**：针对本章的硬核考点，请扮演严厉的导师，给我出一道高难度的“现实情景模拟题”，考考我的理解。
- 🔹 直接发送你读书时遇到的任何**难懂句子或图表**，我会立刻为你进行降维翻译。
```

If the user chooses:

- `[1] 展开细节`: explain the selected term with source quote/anchor, plain analogy, mechanism, common misunderstanding, and a tiny self-test.
- `[2] 极简通行`: process the next chapter only if its source text is accessible; otherwise ask the user to provide it.
- `[3] 模拟Debug`: create one difficult real-world scenario question, wait for the user's answer, then grade it against the source.
- A difficult sentence/table/figure: translate it into plain Chinese, map each clause/axis/variable, and state what the source is actually claiming.

## Quality Bar

Before finalizing, check:

- The answer is based only on supplied text.
- Key concepts retain original source terms.
- Experiments/data/cases are not invented or over-specified.
- The misconception warning is actually supported by the source.
- The action suggestion is concrete and observable.
- The ending control block is present and auto-filled where possible.
