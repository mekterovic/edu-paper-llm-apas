# Full Task Generation Prompt

**Purpose**: Generate complete programming exam tasks from brief instructor ideas.

**Target Models**: GPT 5.1, GPT 4.1, Gemini 3 Flash

**Platform**: OpenAI API (GPT) / Google AI Studio (Gemini)

---

## System Prompt

```
Here is a step-by-step guide that you should follow to answer me.

You are going to receive a programming problem description. You are required to 
generate a clear and detailed problem statement based on the provided description, 
and generate the solution, and extra code if any. 

The problem statement must set up certain input assumptions and limits on input. 
The detailed problem statement must only have the following 5 sections:
1. The problem scenario
2. The problem inputs  
3. The problem outputs
4. An example
5. A limits section (memory limits, time limits, or code complexity limits)

If you cannot generate an example, fill the Example section with "None".
If no limits are defined and cannot be inferred, fill with "Not Available".

After providing the detailed problem statement:
1. Reflect on it to ensure sections correctly represent the problem
2. Point out any mistakes found during reflection
3. Take feedback into account and fix any issues
4. Print the final improved version

Final output format:
Print only the native JSON object with keys: "scenario", "inputs", "outputs", 
"example", "limits". Each value must be a string. No comments in JSON.
```

## Input Format

The user provides a **brief idea** (concise description) of the desired problem:

```
C program that takes two lines (y=ax+b) and outputs where the two lines intersect.
```

## Output Format

The model generates a JSON object:

```json
{
  "scenario": "Clear description of the problem scenario...",
  "inputs": "Detailed input specification...",
  "outputs": "Detailed output specification...",
  "example": "Input: ...\nOutput: ...",
  "limits": "Time Limit: Xs. Memory Limit: YMB. Additional constraints..."
}
```

## Evaluation Criteria

Tasks are evaluated on four metrics (scale 1-10):

| Criterion | Description |
|-----------|-------------|
| **Appropriateness** | Suitability for target course level (CS1 intro course) |
| **Clarity** | Unambiguous text, appropriate for first-year CS students |
| **Formality** | Follows specified format with clearly defined sections |
| **Correctness** | Logical correctness (example output matches input) |

## Results Summary

| Model | Appropriateness | Clarity | Formality | Correctness |
|-------|-----------------|---------|-----------|-------------|
| GPT 5.1 | 10.0 | 8.31 | 9.77 | 0.69 |
| GPT 4.1 | 9.08 | 7.92 | 8.92 | 0.69 |
| Gemini 3 Flash | 9.92 | 8.08 | 9.92 | 0.92 |

### Key Insights

1. **Gemini 3 is most correct** (0.92 vs 0.69) - better at converting text to logically correct code
2. **GPT 5.1 excels in pedagogical quality** - best for educational content
3. **GPT models have similar error rates** - both GPT 4.1 and 5.1 have ~31% correctness issues
4. **Prompt adaptation needed** - Same prompts produce different output volumes; prompts should be tailored per model

## Example Output

**User Input:**
```
C program that takes two lines (y=ax+b) and outputs where the two lines intersect.
```

**Gemini 3 Flash Output:**
```json
{
  "scenario": "You are given two straight lines defined by the linear equations y = a1x + b1 and y = a2x + b2. Your goal is to determine the point (x, y) where these two lines intersect on a 2D plane.",
  "inputs": "Four floating-point numbers: a1 (slope of line 1), b1 (y-intercept of line 1), a2 (slope of line 2), and b2 (y-intercept of line 2).",
  "outputs": "If the lines intersect, output the coordinates as 'Intersect at (x, y)'. If the slopes are equal but intercepts are different, output 'Lines are parallel'. If both slopes and intercepts are equal, output 'Lines are identical'.",
  "example": "Input: a1=2, b1=1, a2=-1, b2=7. Output: Intersect at (2.00, 5.00).",
  "limits": "Time Limit: 1.0s. Memory Limit: 256MB. Calculation should use double precision for floating-point variables."
}
```

## Recommended Workflow

For instructors using this system:

1. **Define brief idea** - Outline the concept/algorithm to test
2. **Generate with GPT** - Use GPT 5.1 for pedagogical quality
3. **Verify with Gemini** - Use Gemini 3 for correctness checking
4. **Manual review** - Always have instructor as final evaluator

## Notes

- Gemini 2.5 Flash was replaced by Gemini 3 Flash during research
- Estimated Gemini 2.5 performance: between GPT 4.1 and GPT 5.1
- LLMs are not interchangeable - prompts should be adapted per model
- Hybrid approach recommended: GPT for structure/pedagogy, Gemini for verification
