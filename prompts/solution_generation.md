# Solution Generation Prompt

**Purpose**: Generate correct C code solutions for programming exam problems.

**Target Models**: GPT 4.1 (sufficient for all tested cases)

**Platform**: OpenAI API

---

## System Prompt

```
You will be given the definition of a programming exercise. You must generate 
the C code necessary to solve this problem. 

Requirements:
- Do not generate functions (unless specifically required)
- You are solving CS1 (Computer Science 1) problems
- Limit yourself to the simplest tools necessary
- Reflect on your code and make sure none of it is incorrect or redundant
```

## Input Format

The user should provide:
- Complete problem statement
- Input/output specifications
- Any constraints or limitations

## Output Format

The model should generate:
- Complete, compilable C code
- Standard input/output handling
- No additional explanations (code only)

## Example

**User Input:**
```
Write a C program that reads two integers and prints their sum.
```

**Expected Output:**
```c
#include <stdio.h>

int main() {
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d\n", a + b);
    return 0;
}
```

## Results Summary

| Problem Set | GPT 4.1 Accuracy |
|-------------|------------------|
| UPRO MI (4 problems) | 100% (4/4) |
| UPRO ZI (6 problems) | 100% (6/6) |
| NASP Advanced (4 problems) | 100% (4/4) |
| **Total** | **100% (14/14)** |

## Notes

- GPT 4.1 achieved 100% accuracy on all tested problems
- Testing of GPT 5.1 and Gemini 2.5 Flash was deemed unnecessary due to GPT 4.1's success
- **Recommendation**: Always manually verify generated solutions before use
- Solutions generated were nearly identical to official exam solutions

## Tested Problems

### UPRO (Introductory Programming)
- MI1, MI2, MI3, MI4 (Midterm exams 2023/24, 1st term)
- ZI1, ZI2, ZI3 (Final exams 2024/25, 1st term)
- ZI1, ZI2, ZI3 (Final exams 2024/25, 2nd term)

### NASP (Advanced Algorithms)
- Palindrome (advanced version)
- 10x10 Tunnel
- Intersect
- Simplex Solver
