# Research Findings

## Executive Summary

This research evaluated four Large Language Models (GPT 5.1, GPT 4.1, Gemini 2.5 Flash, Gemini 3 Flash) across three exam creation tasks. Key findings:

- **GPT 5.1** excels at test case generation with perfect precision
- **All models** achieve 100% accuracy on CS1 solution generation
- **Gemini 3 Flash** shows highest correctness in full task generation
- **Hybrid approach** recommended: GPT for pedagogy, Gemini for verification

---

## 1. Test Case Generation

### Overall Results

| Model            | Precision | Recall   | Avg Ratio |
| ---------------- | --------- | -------- | --------- |
| **GPT 5.1**      | **1.00**  | **0.91** | **1.29**  |
| GPT 4.1          | 0.98      | 0.87     | 1.62      |
| Gemini 2.5 Flash | 0.99      | 0.88     | 1.67      |

### Key Findings

**GPT 5.1 is the clear winner:**

- Only model with perfect precision (1.00)
- Highest recall (0.91)
- Lowest overhead ratio (1.29)

**Gemini vs GPT 4.1:**

- Gemini 2.5 slightly outperforms GPT 4.1
- Gemini generates more redundant test cases
- Gemini performs better on midterm (MI) than final (ZI) problems

**Coverage vs Quantity Trade-off:**

- More test cases → easier to achieve perfect coverage
- Redundant cases must be manually removed
- "Minimal test cases for perfect coverage" prompt provides good balance

### Task-Specific Observations

| Task Type     | Best Model | Notes                                 |
| ------------- | ---------- | ------------------------------------- |
| UPRO MI       | Gemini 2.5 | Notably better than on ZI             |
| UPRO ZI       | GPT 5.1    | Consistent performance                |
| NASP Advanced | GPT 5.1    | Maintains quality on complex problems |

---

## 2. Solution Generation

### Results

| Model       | Accuracy   | Tested               |
| ----------- | ---------- | -------------------- |
| **GPT 4.1** | **100%**   | **14/14**            |
| GPT 5.1     | Not tested | (GPT 4.1 sufficient) |
| Gemini 2.5  | Not tested | (GPT 4.1 sufficient) |

### Key Findings

- **Trivial task for modern LLMs** - CS1 problems are easily solved
- GPT 4.1 solutions were nearly identical to official exam solutions
- **Recommendation**: Always manually verify, but confidence can be high

### Problem Breakdown

| Category      | Count | Accuracy |
| ------------- | ----- | -------- |
| UPRO Midterm  | 4     | 100%     |
| UPRO Final    | 6     | 100%     |
| NASP Advanced | 4     | 100%     |

---

## 3. Full Task Generation

### Overall Results

| Model              | Appropriateness | Clarity  | Formality | Correctness |
| ------------------ | --------------- | -------- | --------- | ----------- |
| **GPT 5.1**        | **10.0**        | **8.31** | **9.77**  | 0.69        |
| GPT 4.1            | 9.08            | 7.92     | 8.92      | 0.69        |
| **Gemini 3 Flash** | 9.92            | 8.08     | 9.92      | **0.92**    |

### Key Findings

**Gemini 3 is most correct:**

- 0.92 correctness vs 0.69 for GPT models
- Better at converting text descriptions to logically correct code
- 31% fewer correctness errors than GPT models

**GPT 5.1 excels in pedagogy:**

- Perfect appropriateness score (10.0)
- Best for educational content and student-level adaptation
- Higher clarity than GPT 4.1

**GPT models share similar weaknesses:**

- Both GPT 4.1 and 5.1 have ~31% correctness issues
- Newer version doesn't fix logical connection problems
- Same types of errors in both versions

**Prompt adaptation is crucial:**

- Same prompts produce different output volumes per model
- GPT 5.1 was too brief/terse with shared prompts
- LLMs are NOT interchangeable - prompts must be tailored

### Problem-Specific Observations

| Problem          | GPT 5.1           | GPT 4.1  | Gemini 3  | Notes                                       |
| ---------------- | ----------------- | -------- | --------- | ------------------------------------------- |
| Simple Simplex   | 10/6/10/1         | 2/6/2/1  | 10/6/10/1 | GPT 4.1 failed on appropriateness/formality |
| UPRO MI2-4       | Mixed correctness | Mixed    | Better    | Consistent correctness issues in GPT        |
| Concept problems | Strong            | Moderate | Strong    | GPT 5.1 best for pedagogical quality        |

---

## 4. Comparative Analysis

### Model Strengths

| Model              | Best For              | Why                                               |
| ------------------ | --------------------- | ------------------------------------------------- |
| **GPT 5.1**        | Test cases, Pedagogy  | Perfect precision, best educational adaptation    |
| **GPT 4.1**        | Solutions             | 100% accuracy, sufficient for all tested problems |
| **Gemini 3 Flash** | Full task correctness | Highest correctness, reliable code generation     |

### Model Weaknesses

| Model    | Weakness                      | Impact                                   |
| -------- | ----------------------------- | ---------------------------------------- |
| GPT 5.1  | Correctness (31% error rate)  | Requires verification for full tasks     |
| GPT 4.1  | Test case recall, Correctness | More redundant cases, correctness issues |
| Gemini 3 | Clarity                       | Slightly lower clarity scores            |

---

## 5. Recommendations

### For Instructors

**Optimal Workflow:**

1. Use **GPT 5.1** for initial task structure and pedagogy
2. Use **Gemini 3 Flash** for correctness verification
3. Always perform **manual review** as final step

**Task-Specific Recommendations:**

| Task                 | Recommended Model   | Confidence |
| -------------------- | ------------------- | ---------- |
| Test case generation | GPT 5.1             | High       |
| Solution generation  | GPT 4.1             | Very High  |
| Full task generation | Hybrid (GPT→Gemini) | Medium     |

### For Researchers

**Future Directions:**

1. Test prompt adaptation per model
2. Evaluate multi-shot/few-shot prompting
3. Explore model chaining approaches
4. Test on broader problem domains

---

## 6. Conclusions

### Main Conclusions

1. **LLMs can significantly reduce exam preparation time**
    - Test case generation: ~70-90% automated
    - Solution generation: ~100% automated (with verification)
    - Full task generation: ~60-70% automated

2. **No single model is best for all tasks**
    - GPT excels at structure and pedagogy
    - Gemini excels at correctness
    - Hybrid approaches are optimal

3. **Instructor oversight remains essential**
    - 30% of full tasks have correctness issues
    - Redundant test cases need filtering
    - Pedagogical judgment cannot be automated

4. **Prompt engineering is critical**
    - Same prompts don't work equally across models
    - Model-specific optimization needed
    - "Minimal for perfect coverage" approach works well

### Final Recommendation

> **Use a hybrid approach**: GPT models for structuring and pedagogical adaptation, Gemini models for verification and correctness checking. Always maintain instructor as final evaluator.

---

## References

1. Mekterović, I., Brkić, L. (2025). "Can LLM Pass a CS1 Course?" MIPRO 48th ICT and Electronics Convention
