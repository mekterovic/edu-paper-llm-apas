# Test Case Generation Prompt

**Purpose**: Generate comprehensive test cases (including edge cases) for programming exam problems.

**Target Models**: GPT 5.1, GPT 4.1, Gemini 2.5 Flash

**Platform**: OpenAI API (GPT) / Google AI Studio (Gemini)

---

## System Prompt

```
You will be given a complete problem description for a programming exercise. 
Your task is to generate test cases for this problem.

For each test case, you must:
1. Identify edge cases based on input constraints and problem logic
2. Describe what each test case verifies
3. Generate concrete input examples that match the description and respect all constraints

Requirements:
- Generate "main" test cases for basic, expected conditions
- Generate edge cases for boundary conditions
- Perform self-reflection on generated edge cases to verify completeness
- Ensure each input example actually tests the described scenario
- Ensure no input violates format or defined constraints

Output format:
- Deliver as an executable Python program that generates a test_cases.json file
- Each test should contain only input (no expected output) for compatibility
- Include comments explaining the purpose of each test case (edge vs main)
- Use strict JSON format as defined below

The goal is to achieve perfect coverage with the minimum number of test cases.
```

## Input Format

The user should provide:
- Complete problem description
- Input/output specifications
- Constraints (time, memory, complexity)
- Any helper code if applicable
- Example inputs/outputs if available

## Output Format

The model should generate a Python script that creates:

```json
{
  "test_cases": [
    {
      "description": "M1: Description of main test case",
      "input": "test input here",
      "type": "main"
    },
    {
      "description": "E1: Description of edge case",
      "input": "edge case input here", 
      "type": "edge"
    }
  ]
}
```

## Evaluation Metrics

When evaluating test case generation:

| Metric | Description |
|--------|-------------|
| **Precision** | Ratio of relevant/correct test cases (1.0 = all correct) |
| **Recall** | Ratio of manual cases covered by generated cases (1.0 = full coverage) |
| **Count** | Number of generated test cases (main + edge) |
| **Ratio** | Generated count / Manual count (lower is better) |

## Example Usage

**User Input:**
```
Problem: Determine if a string is a palindrome (case-sensitive, spaces/punctuation matter)
Input: Single line string S
Output: "true" if palindrome, "false" otherwise
Constraints: None specified
```

**Expected Output:**
Python script generating test_cases.json with cases covering:
- Odd length palindromes
- Even length palindromes  
- Case sensitivity
- Spaces and punctuation
- Single character (minimum length)
- Two character palindromes
- Non-palindromes

## Notes

- The prompt asks for "minimal number of test cases achieving perfect coverage"
- This creates a good balance between coverage and avoiding redundancy
- Some overlap between edge cases is expected and should be manually reviewed
