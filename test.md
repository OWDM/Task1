# My First Markdown File

Welcome to **Markdown**! This is a test file.

## Features

-   Bold and *italic* text
-   [Links](https://www.example.com)
-   Lists
    -   Nested list item

## Code Block

``` python
def hello():
    print("Hello, Markdown!")
```

> Blockquotes are fun!

------------------------------------------------------------------------

That's it 🎉




# LLM Prompt Structure Template

> Copy this file and replace the placeholders like `{{variable}}` with your own info.

---

## 1) System Message (Who the model is + rules)
Describe the assistant’s role, capabilities, boundaries, and style.
```
You are {{role}}. Your goal is {{goal}}.
Follow these rules:
1) Be {{tone}}.
2) Prefer {{format}} outputs.
3) Do not reveal hidden reasoning or internal chain-of-thought.
4) Ask for clarification only if {{when_to_clarify}}.
5) Refuse content that violates {{policies_or_domains}}.
```
**Non-negotiables:** {{must_do_list}}

---

## 2) Context (What the model should know)
Provide background, domain constraints, and any prior messages or docs it should consider.
- Audience: {{audience}}
- Domain/Industry: {{domain}}
- Key definitions: {{definitions}}
- Constraints (legal, compliance, brand): {{constraints}}
- External resources available (tools/APIs/files): {{resources}}

> Keep only what is relevant; delete the rest.

---

## 3) Task (What to do)
Give a crisp instruction of the desired outcome.
```
Task: {{imperative_verbs}} (e.g., "Summarize...", "Draft...", "Generate...", "Classify...")
Primary objective: {{primary_objective}}
Success criteria: {{success_criteria}}
```

---

## 4) Inputs (Data the model should use)
Attach or inline inputs. If long, summarize key points.
```
INPUT_START
{{paste_or_link_input_data_here}}
INPUT_END
```

---

## 5) Output Format (Shape of the answer)
Define the required structure explicitly (Markdown, JSON, table, etc.).
Example (JSON Schema-style):
```json
{
  "type": "object",
  "required": ["summary", "insights", "action_items"],
  "properties": {
    "summary": { "type": "string" },
    "insights": { "type": "array", "items": { "type": "string" } },
    "action_items": { "type": "array", "items": {
      "type": "object",
      "required": ["owner", "task", "due_date"],
      "properties": {
        "owner": { "type": "string" },
        "task": { "type": "string" },
        "due_date": { "type": "string", "description": "YYYY-MM-DD" }
      }
    }}
  }
}
```

If Markdown, specify sections:
- **Summary**
- **Key Points**
- **Risks/Assumptions**
- **Next Steps**

---

## 6) Style & Tone
- Tone: {{tone}} (e.g., concise, friendly, expert)
- Reading level: {{grade_level}} (e.g., 8th grade, executive brief)
- Formatting: {{formatting_prefs}} (e.g., bullets > paragraphs, headings, code fences)
- Localization: {{language}}, {{date_format}}, {{units}}

---

## 7) Constraints & Guardrails
- Word/Token budget: {{length_limit}}
- Must cite sources when: {{citation_rules}}
- Privacy: redact {{pii_rules}}
- Safety: avoid {{safety_bounds}}
- No speculation beyond {{speculation_bounds}}

> If constraints conflict, prioritize in this order: System > Safety > Task > Style.

---

## 8) Tool Use (Optional)
Describe available tools and how to call them.
```
- Web search: use to verify facts newer than {{recency_threshold}}.
- Calculator: for arithmetic; show steps only if requested.
- File reader: only for files listed in "Inputs".
```
**Tool policy:** Explain when to use each tool and when to avoid it.

---

## 9) Few-Shot Examples (Optional, highly recommended)
Show 1–3 high-quality examples. Keep them short and focused.

**Example 1**
**Instruction:** Summarize the article in 3 bullets.
**Input:** (short excerpt)
**Good Output:**
- Bullet A
- Bullet B
- Bullet C

**Bad Output (why bad):**
- Too long, ignores limit
- Adds facts not in input

---

## 10) Evaluation & Verification
- Self-checklist before answering:
  - [ ] Followed Output Format exactly
  - [ ] Met length limit
  - [ ] Used only provided inputs
  - [ ] Highlighted uncertainties
  - [ ] Included citations if required
- Post-answer verification instruction:
```
If any required field is missing or constraints are violated, regenerate with fixes.
```

---

## 11) Response Rubric (for auto-grading or human review)
Score 1–5 on:
- **Relevance** (uses provided inputs; no hallucinations)
- **Completeness** (covers all requested parts)
- **Clarity** (easy to read; proper structure)
- **Accuracy** (facts correct; math correct)
- **Actionability** (clear next steps or recommendations)

---

## 12) Meta (for your workflow)
- Version: {{prompt_version}}
- Owner: {{owner_name_or_team}}
- Last updated: {{yyyy-mm-dd}}

---

## Ready-to-Use Skeleton (Copy/paste below)
```
[SYSTEM]
You are {{role}}. {{rules_and_style}}. Do not reveal chain-of-thought.

[CONTEXT]
{{context_blurb}}

[TASK]
{{task_sentence}}

[INPUTS]
{{inputs_or_links}}

[OUTPUT_FORMAT]
{{format_spec_or_schema}}

[CONSTRAINTS]
{{hard_limits_and_policies}}

[STYLE]
{{tone_reading_level_formatting}}

[CHECKLIST]
- Follow schema
- Respect limits
- Verify facts
- Note uncertainties

[RETURN ONLY]
{{exact_format_e.g._valid_JSON_or_markdown_sections}}
```

