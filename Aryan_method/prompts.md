\---  
alwaysApply: true  
\---  
IMPORTANT: One prompt at a time. Never skip. Never assume. Never infer.
## Trigger
When user says: "I want to work on new task" or similar variants like "new task", "start task",
"next task"
---
**Phantom delivery (submission rejections):** If **4a/5a** shows **no files modified** (or only read-only exploration) and **no** test/build/CI commands with output in the trace, **4b/5b** and **Prompt 6–8** must **not** credit **pytest**, **CI**, **Docker**, **requirements** (or other dep files), or **shipped** implementation. **Search** **ResponseA.txt** / **ResponseB.txt** for every artifact you name before submit (see RULEBOOK **Phantom delivery**).

\# PROMPT 1 \- Setup  
Read project TUNA\\RULEBOOK.md word by word. Confirm. Stop.

\# PROMPT 2 \- Load context  
Read prompt.txt history completely. Confirm. Don't analyze yet.

\# PROMPT 3 \- Rate prompt  
Score 1-5. Two lines max referencing missing inputs, realism, or difficulty.

\# PROMPT 4a \- Load Response A  
Read ResponseA.txt. List only:  
\- Files modified  
\- Commands run  
\- Outputs shown  
One sentence: what did it actually accomplish? Confirm. Don't analyze yet.

\# PROMPT 4b \- Response A Strengths  
Only use evidence from your 4a list. No proof → don't write it.  
If **4a** lists **no files modified** (exploration only), strengths may only reflect **read-only** work shown in **4a**; do **not** praise tests, CI, Docker, dependency edits, or completed implementation.  
Min 200 chars. Specific files/commands. Casual tone. Under 5 lines.  
Prefer **execution proof**: what was **run** (node, pytest, build, harness), what **output** showed (pass/fail, UI check, pipeline step) — not only that the response "did" something.  
When the task implied **repo-wide** scope, strengths may highlight **manifest** + **broad search** runs shown in the trace; when **grep** output was **ambiguous**, strengths may highlight a **careful** read (**false** **positive** avoided).

\# PROMPT 4c \- Response A Weaknesses  
Check: verification, false claims, scope creep, edge cases, instructions.  
Do **not** pair **4b** praise for **minimal/focused** delivery with **`[OVERENG]`** here **only** because the transcript is long (**`[VERBOSE]`** is for read cost; **`[OVERENG]`** needs extra **executed** scope). Do **not** assert missing verification if **4b** claimed thorough testing without reconciling.  
Use category codes. No fabrication. Contradict a strength → fix it first.  
Separate **missing proof** (work in trace but no test/build output → \[VERIFY\]) from **not actually implemented** (no real deliverable → \[LAZY\]/\[INST\], not \[VERIFY\] alone). Say which case you mean in plain words (packaging critique: reviewers reject blurring these).  
Cover **several distinct** issue types if the trace has them (don't repeat one theme). For file/docs/process flags, add **functional or review risk** when the trace supports it (wrong behavior, broken entrypoint, merge/CI risk, misleading docs) — not hygiene only.  
**Implied scope:** If the user task reads **project-wide** (e.g. **"only X going forward"**, **"remove all Y"**) but the trace only touches **one** file, flag **missing** **manifest** checks (**`pubspec.yaml`**, **`package.json`**, etc.) and **broader** **`grep`/`rg`** as **\[VERIFY\]** (or **\[INST\]** if they claimed full removal) per RULEBOOK **Implied task scope**.  
**\[FALSE\]:** If no material false claims → **one line** (**not applicable**) or **omit** the bullet. **Do not** pad with repeated **"not applicable"** paragraphs.  
**Grep / command output:** Before treating a **search** hit as proof, sanity-check **false positives** (substring in **`import`**, wrong path, generated dirs) per RULEBOOK **Command output and grep hygiene**; credit sharp catches in **4b** when relevant.  
**Do not** draft 5c by copying this block's **structure** and swapping **A→B** (same code order + synonym sentences). See RULEBOOK **No mirrored A/B weakness template**.  
**\[VERBOSE\]** = **only** reviewer **readability** cost (padded transcript, noisy markdown, huge dumps that **slow skimming**). **\[OVERENG\]** = **only** unnecessary **execution** steps or **scope** beyond the ask (extra harnesses, spare features). **Don't** use **\[VERBOSE\]** for "too many commands/scripts" (**that's \[OVERENG\]**). **Don't** use **\[OVERENG\]** for "hard to read the log" alone (**that's \[VERBOSE\]**). One code per issue; see RULEBOOK **VERBOSE vs OVERENG** split.


\# PROMPT 5a \- Load Response B  
Read ResponseB.txt. List only:  
\- Files modified  
\- Commands run    
\- Outputs shown  
One sentence: what did it actually accomplish? Don't compare to A. Confirm. Don't analyze yet.

\# PROMPT 5b \- Response B Strengths  
Only use evidence from your 5a list. No proof → don't write it.  
If **5a** lists **no files modified** (exploration only), strengths may only reflect **read-only** work shown in **5a**; do **not** praise tests, CI, Docker, dependency edits, or completed implementation.  
Min 200 chars. Specific files/commands. Casual tone. Under 5 lines.  
Same execution-grounding bar as 4b (runs, outputs, harness/UI/pipeline as shown in trace), including **implied-scope** and **grep** **hygiene** wins when **5a** shows them.

\# PROMPT 5c \- Response B Weaknesses  
Check: verification, false claims, scope creep, edge cases, instructions.  
Same **4b vs 4c** consistency rule as **5b vs 5c**: **`[OVERENG]`** is **not** a synonym for “long log”; align praise in **5b** with verification claims in **5c**.  
Use category codes. No fabrication. Contradict a strength → fix it first.  
Same split as 4c: **missing proof** vs **not implemented** — pick the right code and **name** which (don't use \[VERIFY\] as a stand-in for "nothing shipped").  
Apply the same **implied scope**, **\[FALSE\]** brevity, and **grep hygiene** rules as in **4c** (RULEBOOK **Implied task scope**, **When \[FALSE\] is omitted**, **Command output and grep hygiene**). Do **not** re-copy 4c sentence-for-sentence; keep **5c** a **different** order and evidence shape (**No mirrored A/B weakness template**).  
Weaknesses should **differ in shape** from 4c: **different category order** when possible, **different** evidence and sentence shapes — not the **INST → VERIFY → ROOT** (or any fixed) ladder with **A/B** names swapped. If traces are similar, still vary **angle** (e.g. tool failure vs wrong path vs missing verification). Deepen **functional/review risk** beyond housekeeping when the trace supports it.  
**\[VERBOSE\]** vs **\[OVERENG\]**: same split as 4c (**readability** vs **steps/scope**); **one code per issue**; **don't** let a **verbosity** bullet **overlap** an **overengineering** bullet for the **same** underlying gripe.

\# PROMPT 6 \- Compare and rate  
For each of 9 dimensions write:  
\- A evidence: \[what A did\]  
\- B evidence: \[what B did\]  
\- Winner: \[A/B/tie\] because \[one reason\]  
\- Rating: \[1-8\]

**Per-dimension feedback–rating lock (required):** For **each** of the nine dimensions, **after** drafting **A evidence**, **B evidence**, **Winner**, and **Rating** for that row, do this before moving on: **(1)** If one side’s evidence says **nothing to evaluate** / **no proof** / **N/A** on **this axis** and the other cites **concrete verification** (tests, harness output, traced error path), you **must not** set **Winner** to the empty side or use a rating that favors the empty side (A better = 1–4, B better = 6–8). Either **favor the side with proof** or **tie (4–5)** and say so. **(2)** If you cannot point to **a sentence you wrote in that row** that supports a **Rating** outside **4–5**, set **Rating: 4** and **Winner: tie** (or rewrite evidence until aligned). **(3)** **Overall** preference for one response does **not** carry to dimensions where your **evidence** gives that response **no** advantage (**anti-halo**).

**Before** choosing any rating **outside 4–5**, run the **mirror test** on that dimension: could the same "because" apply to the **other** response with only names swapped (same bugfix, same kind of pytest before/after)? If **yes** → set **4** (or 5 only if there is a **trace-specific** edge).  
**Logic and Correctness:** if 4b and 5b both praise the **same** logic change and **same class of regression proof**, rating here must stay **4–5** — do not favor B (or A) with a 6 or 3 on vibes.  
**Comments and Documentation:** non-4 needs **different** comment/doc/README evidence in the traces; else **4**.  
**Review Ready:** Before favoring one response (**Rating** outside **4–5**), re-read **4c** and **5c**. If only one side has **`[TOOL]`**, execution failures, or workaround-heavy tooling and both delivered **similar** completeness, **do not** rate the **tool-friction** side as **more** merge-ready without explicit compare text that overrides; default **tie** or favor the **cleaner** trace.

Then add **one standalone sentence** in this **same compare block** (reviewers read compare as a unit — do not leave the pick implied only by per-dimension winners or tally of "Winner:" lines):  
**Overall:** Response \[A or B\] is better overall because \[one clear reason tied to task\].  
That sentence must **state the winner and why** explicitly (not "both have tradeoffs" without a pick).  

Then check:  
Similar weaknesses → 4-5 only  
Parallel logic/test story in strengths → Logic and Correctness 4-5  
No evidence for a dimension → change to 4  
One completely fails → only then use 1-2 or 7-8  
All 9 identical → automatic rejection, vary them using **real** axes (scope, honesty, review-ready, etc.) — not fake Logic spread  
**Reread Prompt 6 dimension-by-dimension:** for **each** row, **Winner** + **Rating** must not contradict **A evidence** / **B evidence** / **Winner because** (see RULEBOOK **Per-dimension rating must follow your own compare prose**).

\# PROMPT 7 \- Verify ratings  
List all 9 ratings. One justification sentence each.  
No justification → change to 4\.  
Worse response must have higher numbers.  
"Similar" or "both" in evidence → must be 4-5.  
**Contradiction sweep:** Re-read **Prompt 6** **A evidence / B evidence / Winner / Rating** for **each** dimension. If any **Rating** or **Winner** conflicts with those lines (e.g. **B** has test proof on that axis, **A** has nothing to evaluate, but **Rating** favors **A**), **correct to 4–5** or fix **Prompt 6** prose.  
**Honesty:** If **4b/4c/5b/5c** and compare **do not** state a **concrete** transparency or accuracy difference, set **Honesty to 4** (no gut lean).  
**Review Ready vs 4c/5c:** If **4c** (or **5c**) attributes **`[TOOL]`** / failed commands / workarounds to **one** response and the **other** lacks that weakness while outcomes are **similar**, **Review Ready** must **not** favor the **tool-error** side (**1–4** for A or **6–8** for B depending on which was dinged). Align with RULEBOOK **Review Ready vs weakness analysis**.  
Re-read 4b/5b: if Logic strengths are **parallel** (same fix + comparable tests), Logic and Correctness cannot be 3 vs 6 — fix to 4-5.  
Re-read doc/comment evidence: Comments and Documentation needs a **concrete** asymmetry or stay at 4\.  
Skim 4c/5c: weaknesses should feel **multi-axis** and **not** copy-paste; **4c vs 5c** must not be the **same template** twice (RULEBOOK **No mirrored A/B weakness template**). At least one hygiene-style point has **functional or review risk** called out if the trace supports it (not hygiene-only).  
Re-check **implied task scope** and **\[FALSE\]** sections: no **single-file** "complete" story when the prompt was **repo-wide** without evidence; no **padded** **not-applicable** **\[FALSE\]** blocks.  
Confirm Prompt 6 output contains the **Overall:** sentence in the compare section and that it is **not** inferable-only from dimension blurbs.  
Show corrected final ratings.

\# PROMPT 8 \- Rationale  
Must match every rating from Prompt 7\.  
Min 200 chars. Casual Slack tone. No banned phrases.  
No two sentences start the same way.  
Include **one explicit sentence** naming **which response is better overall and why** (same winner as Prompt 6; do not leave this implied only by the rest of the paragraph or by dimension scores).  
Specific to this task only. Stop.  