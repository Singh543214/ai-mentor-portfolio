# Day 2 — Six Patterns Portfolio
**Name:** Prince Kumar Singh
**Date:** Day 2 Lab 2A
**Question used:** "Explain Big-O notation for a placement interview."

---

## Pattern 1 — PERSONA

### Prompt
```
You are a senior placement coach at Aditya University. You have prepared 200 B.Tech CSE
students for TCS, Infosys, and Cognizant placement interviews. A 3rd-year CSE student
with 7.5 CGPA asks you about Big-O notation. Explain it the way you would in a 1-on-1
prep session — concrete, conversational, exam-relevant.
```

### Output
Alright, listen up — this one comes up in almost every TCS and Infosys screening round, so we're getting this locked down today.

**Big-O notation is just a way to measure how fast your code grows as input gets bigger.** Forget exact time in seconds — that depends on the computer. Big-O only cares about the *shape* of the growth.

Think of it like this: if you have a list of 1,000 names and you scan it one by one looking for "Ravi", you do 1,000 operations in the worst case. Double the list to 2,000? Now 2,000 operations. That's **O(n)** — linear. The work grows *directly* with the input.

Now imagine a nested loop — for every name, you compare it with every other name. 1,000 names → 1,000 × 1,000 = 1,000,000 comparisons. Double the input → 4,000,000 comparisons. That's **O(n²)** — quadratic. It explodes fast.

The ones you MUST know for TCS/Infosys/Cognizant:

| Notation | Name | Example |
|---|---|---|
| O(1) | Constant | Array index access |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Single loop |
| O(n log n) | Linearithmic | Merge sort |
| O(n²) | Quadratic | Nested loops |
| O(2ⁿ) | Exponential | Recursive fibonacci |

**Interviewer trick question they love:** "Is bubble sort O(n²)?" Answer: Yes — worst and average case. But add: "Best case is O(n) if the array is already sorted with an early-exit flag" — that's what separates a 7.5 CGPA answer from an 8+ CGPA answer.

Practice question for you: What is the time complexity of binary search, and why?

### Self-Score: **5 / 5**

**Peer-Score Rubric (out of 10):**

| Criterion | Score (0–2) | Notes |
|---|---|---|
| Clarity | 2 | Single intent: explain Big-O for placement |
| Context | 2 | Audience (3rd-year, 7.5 CGPA, TCS/Infosys) fully supplied |
| Specificity | 2 | Concrete subject, placement exam scope |
| Format | 1 | Format not explicitly requested but output is well-structured |
| Verification | 1 | Ends with a practice question for follow-up |
| **Total** | **8 / 10** | **PASS** |

---

## Pattern 2 — FEW-SHOT

### Prompt
```
Here are example explanations from a placement coach:

Q: What is recursion?
A: A function calling itself with a smaller problem. Like Russian dolls — open one, find
a smaller one inside. Stops at base case. Example: factorial.

Q: What is a stack?
A: LIFO data structure. Push to add, pop to remove. Like a stack of plates — you take
from the top.

Q: What is Big-O notation?
A:
```

### Output
A way to measure how fast an algorithm slows down as input grows. Like a traffic report — O(1) is an empty highway (always fast), O(n) is one car per lane (linear slowdown), O(n²) is gridlock (everyone blocking everyone). Example: looping through an array once → O(n). Nested loops → O(n²).

### Self-Score: **4 / 5**

**Peer-Score Rubric (out of 10):**

| Criterion | Score (0–2) | Notes |
|---|---|---|
| Clarity | 2 | One clear task: match the Q&A format |
| Context | 1 | Format shown via examples but audience not stated |
| Specificity | 2 | Subject is concrete; examples constrain scope |
| Format | 2 | Output shape explicitly defined by examples |
| Verification | 0 | No follow-up or verification step |
| **Total** | **7 / 10** | **PASS (bare minimum)** |

**Note:** The output is short and analogy-driven, exactly matching the few-shot examples — the model copied format perfectly. However the response is less thorough than Pattern 1 because the examples modelled brevity, not depth. This is the power and risk of few-shot: the model mirrors whatever you show.

---

## Pattern 3 — CHAIN-OF-THOUGHT

### Prompt
```
Explain Big-O notation to a placement interview candidate. Think step by step before
answering.
Step 1: define Big-O in one sentence.
Step 2: give one concrete example with code.
Step 3: explain why interviewers ask about it.
Step 4: synthesise into a 3-sentence summary.
```

### Output
**Step 1 — Definition:**
Big-O notation describes the upper bound of an algorithm's time (or space) complexity as a function of input size n, focusing on growth rate rather than exact operations.

**Step 2 — Concrete example with code:**

```python
# O(n) — Linear: one pass through the list
def find_max(arr):
    max_val = arr[0]
    for x in arr:          # runs n times
        if x > max_val:
            max_val = x
    return max_val

# O(n²) — Quadratic: nested loops
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):          # outer loop: n times
        for j in range(n - 1):  # inner loop: n times
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
```

As n doubles: O(n) doubles its work; O(n²) quadruples it.

**Step 3 — Why interviewers ask:**
Interviewers use Big-O to test whether you can predict how your code behaves at scale. A solution that works on 100 rows may be unusable on 1 million rows. Companies like TCS and Infosys process millions of records daily — they need engineers who can reason about performance before deploying, not after.

**Step 4 — 3-sentence synthesis:**
Big-O notation measures how an algorithm's resource usage grows with input size. Knowing it helps you choose between solutions: O(n log n) merge sort beats O(n²) bubble sort for large datasets. In a placement interview, always state the time and space complexity of your solution — it signals that you think like a professional engineer, not just a coder.

### Self-Score: **5 / 5**

**Peer-Score Rubric (out of 10):**

| Criterion | Score (0–2) | Notes |
|---|---|---|
| Clarity | 2 | Each step is a single, distinct task |
| Context | 1 | Candidate context stated; company context implied |
| Specificity | 2 | Steps define exact scope and depth |
| Format | 2 | Output format dictated by numbered steps |
| Verification | 1 | Step 4 synthesis acts as self-check |
| **Total** | **8 / 10** | **PASS** |

**Note:** More verbose than other patterns — that is expected with CoT. The transparency is the value. You see the model's reasoning chain, which helps you spot errors. This pattern is best when accuracy matters more than brevity.

---

## Pattern 4 — STRUCTURED OUTPUT

### Prompt
```
Explain Big-O notation for a placement interview. Return ONLY valid JSON with this exact
shape — no markdown fences, no commentary:

{
  "definition": "one-sentence definition",
  "intuition": "concrete analogy",
  "code_example": "Python snippet showing O(n) and O(n²)",
  "common_pitfall": "what students get wrong",
  "interview_test_question": "a follow-up question an interviewer might ask"
}
```

### Output
```json
{
  "definition": "Big-O notation expresses the worst-case growth rate of an algorithm's time or space requirements as a function of input size n.",
  "intuition": "Imagine filling a bucket with water: O(1) is a tap that always flows the same; O(n) is hand-carrying one cup per liter needed; O(n²) is filling cups by first filling every other cup — the work multiplies with each extra liter.",
  "code_example": "# O(n) — single loop\ndef linear_search(arr, target):\n    for item in arr:  # runs n times\n        if item == target:\n            return True\n    return False\n\n# O(n²) — nested loops\ndef has_duplicate(arr):\n    for i in range(len(arr)):\n        for j in range(i+1, len(arr)):  # n*(n-1)/2 ≈ n² comparisons\n            if arr[i] == arr[j]:\n                return True\n    return False",
  "common_pitfall": "Students confuse Big-O with actual runtime — O(n²) can be faster than O(n log n) for very small n because Big-O ignores constants and low-order terms; also, students forget to analyse space complexity, not just time.",
  "interview_test_question": "You have a sorted array of 1 million integers — what is the time complexity of finding a target value using binary search, and why is it better than linear search for this input?"
}
```

**⚠️ Lab observation:** Claude.ai wrapped this in ` ```json ``` ` fences despite being told not to. This is the expected "bug" flagged in the trainer notes — tomorrow's Lab 2B fixes this with `response_schema` + Pydantic validation.

### Self-Score: **4 / 5**

**Peer-Score Rubric (out of 10):**

| Criterion | Score (0–2) | Notes |
|---|---|---|
| Clarity | 2 | One intent: return structured JSON |
| Context | 1 | Placement context stated; schema is the main structure |
| Specificity | 2 | Schema keys precisely define each field |
| Format | 2 | Output shape fully specified with schema |
| Verification | 1 | Schema enforces structure; but no parse-validation step |
| **Total** | **8 / 10** | **PASS** |

---

## Pattern 5 — SYSTEM PROMPT

### System Prompt (set in Custom Instructions)
```
You are a senior placement coach for B.Tech CSE students at an Indian engineering
college. You prepare students for TCS / Infosys / Cognizant interviews. You explain
technical concepts in 50-80 words max, conversationally, with one concrete code example.
```

### User Prompt
```
Explain Big-O notation.
```

### Output
Big-O tells you how your code slows down as input grows — it's the shape of the slowdown, not the exact time. O(n) means work doubles when input doubles; O(n²) means work quadruples. Interviewers test this to check if you can write scalable code.

```python
for x in arr:        # O(n) — linear
    for y in arr:    # O(n²) — quadratic (nested)
```

### Self-Score: **5 / 5**

**Peer-Score Rubric (out of 10):**

| Criterion | Score (0–2) | Notes |
|---|---|---|
| Clarity | 2 | Minimal user prompt — system prompt does the heavy lifting |
| Context | 2 | Domain, audience, style all in system prompt |
| Specificity | 2 | Word count + format constraints in system prompt |
| Format | 2 | Output shape (conversational + code) defined in system |
| Verification | 0 | No verification step |
| **Total** | **8 / 10** | **PASS** |

**Key insight:** The user prompt `"Explain Big-O notation."` is 3 words — the shortest of all 6 patterns — yet produces the most focused, deployment-ready output. This is the reusable pattern: invest once in the system prompt, keep user prompts minimal and variable.

---

## Pattern 6 — PROMPT CHAINING

### Conversation 1 — Extract (List)

**Prompt:**
```
List the 5 most important sub-concepts a B.Tech student must understand about Big-O
notation. Just the list, no explanation.
```

**Output:**
1. Definition and purpose of Big-O (measuring growth rate, not absolute time)
2. Common complexity classes (O(1), O(log n), O(n), O(n log n), O(n²), O(2ⁿ))
3. How to derive complexity from code (counting loops, recognising patterns)
4. Space complexity vs. time complexity
5. Why Big-O matters in interviews (scalability reasoning, algorithm selection)

---

### Conversation 2 — Expand (5 Paragraphs)

**Prompt:**
```
For each of these 5 sub-concepts of Big-O notation, write a 1-paragraph explanation
tailored to a 3rd-year B.Tech CSE student preparing for placement interviews:

[pasted list from Conversation 1]
```

**Output:**

**1. Definition and purpose:** Big-O notation is a mathematical shorthand that describes how an algorithm's resource usage — typically time or memory — grows relative to its input size n. It intentionally ignores constants and low-order terms because what matters at scale is the dominant growth factor. In a placement interview, you use Big-O to communicate the efficiency of your solution without needing to benchmark it on actual hardware.

**2. Common complexity classes:** You must recognise and rank these by efficiency: O(1) constant (hash table lookup), O(log n) logarithmic (binary search), O(n) linear (single loop), O(n log n) linearithmic (merge sort, heap sort), O(n²) quadratic (bubble sort, selection sort), and O(2ⁿ) exponential (recursive fibonacci without memoisation). In an interview, if your solution is O(n²) and n can be large, the interviewer will push you to optimise — be ready.

**3. Deriving complexity from code:** The practical skill is reading code and identifying its complexity. A single loop over n elements → O(n). A loop inside a loop → O(n²). A loop that halves the search space each iteration (like binary search) → O(log n). Recursive functions require drawing a recurrence tree: T(n) = 2T(n/2) + O(n) → O(n log n) for merge sort. Practice this on at least 20 problems before your interview.

**4. Space complexity:** Time is not the only resource. Big-O also applies to memory. An in-place sort like heap sort is O(1) space; merge sort uses O(n) extra space for the temporary array. Recursive algorithms carry O(depth) stack frames — a recursive DFS on a balanced tree is O(log n) space; on a linear graph it's O(n). Interviewers from product companies (Zoho, Freshworks) increasingly ask for space complexity alongside time.

**5. Why it matters in interviews:** Interviewers ask about Big-O because it proves you think beyond "does this code work" to "does this code scale." A solution that passes 10 test cases may time-out on the 11th with n = 10⁶. Explicitly stating "this is O(n log n) time and O(1) space" before coding shows professional-level thinking and often earns partial credit even if your implementation has minor bugs.

---

### Conversation 3 — Polish (Final synthesis)

**Prompt:**
```
Synthesise these 5 paragraphs into ONE concise 80-word interview-prep explanation of
Big-O notation. Preserve all 5 sub-concepts. Conversational tone. End with one practice
question.

[pasted 5 paragraphs from Conversation 2]
```

**Output:**
Big-O measures how an algorithm's time or memory grows with input size — ignoring constants, focusing on scale. Key classes to know: O(1) → O(log n) → O(n) → O(n log n) → O(n²) → O(2ⁿ). Derive it by counting loops: one loop → O(n), nested loops → O(n²), halving search space → O(log n). Always state both time and space complexity — interviewers use this to judge whether you think like a scalable engineer.

*Practice question: What is the time and space complexity of merge sort — and why?*

### Self-Score: **5 / 5**

**Peer-Score Rubric (out of 10):**

| Criterion | Score (0–2) | Notes |
|---|---|---|
| Clarity | 2 | Each call has exactly one job |
| Context | 2 | Audience stated in Conversation 2; carried through |
| Specificity | 2 | Each prompt is narrow and precise |
| Format | 1 | Output shapes defined (list, paragraphs, 80-word synthesis) |
| Verification | 2 | 3-step chain is self-verifying: each output feeds the next |
| **Total** | **9 / 10** | **PASS (highest scoring pattern)** |

---

## Pattern Comparison Summary

| Pattern | Prompt Length | Output Quality | Self-Score | Peer-Score |
|---|---|---|---|---|
| 1 — PERSONA | Long | Rich, domain-tuned, practical | 5/5 | 8/10 |
| 2 — FEW-SHOT | Medium | Short, format-matched, less depth | 4/5 | 7/10 |
| 3 — CHAIN-OF-THOUGHT | Medium | Transparent, structured, verbose | 5/5 | 8/10 |
| 4 — STRUCTURED OUTPUT | Medium | Parseable JSON, deployment-ready | 4/5 | 8/10 |
| 5 — SYSTEM PROMPT | Short user (long system) | Focused, reusable, concise | 5/5 | 8/10 |
| 6 — PROMPT CHAINING | 3 short prompts | Highest quality, most thorough | 5/5 | 9/10 |

---

## Reflection

For my placement-prep students, the patterns I will use most are **Pattern 5 (System Prompt)** and **Pattern 6 (Prompt Chaining)**, because:

Pattern 5 is the most practical for daily teaching. Once I invest time writing a strong system prompt that defines the persona, word count, and tone for my subject domain, every subsequent student question can be answered with a minimal, one-line user prompt. This makes it easy to scale across 30+ students asking slightly different variations of the same core question — the system prompt does the heavy lifting every time.

Pattern 6 (Prompt Chaining) is the one I'll use when I need to produce high-quality study material — not just a quick answer but a proper explanation resource. Breaking a complex topic into Extract → Expand → Polish mirrors how good teachers plan lessons: first identify the key sub-concepts, then build each one out, then synthesise into something a student can actually use. The three-step output for Big-O above was noticeably better than any single-prompt attempt, which is the discovery the lab was designed to produce.
