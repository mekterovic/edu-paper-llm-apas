# Evolving Programming Education with AI: Opportunities and Challenges of LLM-Integrated Assessment Systems

[![Research](https://img.shields.io/badge/Research-Academic-blue)](https://github.com)
[![Language](https://img.shields.io/badge/Language-C%2FC%2B%2B-orange)](<https://en.wikipedia.org/wiki/C_(programming_language)>)
[![LLM](https://img.shields.io/badge/LLM-GPT%20%7C%20Gemini-green)](https://openai.com)

> **Technical Documentation v1.0**  
> Research on using Large Language Models (LLMs) to assist instructors in creating programming exam questions for computer science courses.

## Overview

This repository contains supplementary materials for research evaluating LLMs as tools for assisting instructors in creating programming exam questions. The research focuses on three key aspects of exam creation:

1. **Test Case Generation** - Automatically generating edge cases and test inputs
2. **Solution Generation** - Creating correct reference solutions
3. **Full Task Generation** - Generating complete exam problems from brief instructor ideas

### Models Evaluated

| Model            | Platform         | Use Case               |
| ---------------- | ---------------- | ---------------------- |
| GPT 5.1          | OpenAI API       | Test cases, Full tasks |
| GPT 4.1          | OpenAI API       | Solutions, Full tasks  |
| Gemini 2.5 Flash | Google AI Studio | Test cases             |
| Gemini 3 Flash   | Google AI Studio | Full tasks             |

### Problem Categories

- **UPRO** - Introductory Programming (equivalent to CS1)
- **NASP** - Advanced Algorithms and Data Structures

## Repository Structure

```
rag-exam-generation/
├── README.md                 # This file
├── prompts/                  # LLM prompts used in research
│   ├── test_case_generation.md
│   ├── solution_generation.md
│   └── full_task_generation.md
├── data/                     # Research results (CSV format)
│   ├── test_case_results.csv
│   ├── solution_results.csv
│   └── full_task_results.csv
├── examples/                 # Example LLM outputs
│   ├── task_generation/
│   ├── test_case_generation/
└── docs/                     # Additional documentation
    ├── methodology.md
    └── findings.md
```

### Viewing Results

All experimental results are in CSV format in the `data/` directory for easy analysis:

```python
import pandas as pd

# Load test case generation results
df = pd.read_csv('data/test_case_results.csv')
print(df.groupby('model')[['precision', 'recall']].mean())
```

## Key Findings

### Test Case Generation

| Model            | Precision | Recall | Avg Test Cases (main+edge) | Ratio to Manual |
| ---------------- | --------- | ------ | -------------------------- | --------------- |
| GPT 5.1          | 1.00      | 0.91   | -                          | 1.29            |
| GPT 4.1          | 0.98      | 0.87   | -                          | 1.62            |
| Gemini 2.5 Flash | 0.99      | 0.88   | -                          | 1.67            |

**Winner: GPT 5.1** - Best precision and recall with minimal overhead

### Solution Generation

All models achieved **100% accuracy** on CS1-level problems. GPT 4.1 was sufficient for all test cases.

### Full Task Generation

| Model          | Appropriateness | Clarity | Formality | Correctness |
| -------------- | --------------- | ------- | --------- | ----------- |
| GPT 5.1        | 10.0            | 8.31    | 9.77      | 0.69        |
| GPT 4.1        | 9.08            | 7.92    | 8.92      | 0.69        |
| Gemini 3 Flash | 9.92            | 8.08    | 9.92      | 0.92        |

**Recommendation**: Use GPT for pedagogical quality, Gemini for correctness verification.

## Citation

If you use this work in your research, please cite:

```bibtex
@misc{edu-paper-llm-apas,
  title={Evolving Programming Education with AI: Opportunities and Challenges of LLM-Integrated Assessment Systems},
  author={Mekterovi{\'c}, I and Brki{\'c}, Lj and Tadijal, M and Vanjak, T},
  booktitle={2026 MIPRO 49th ICT and Electronics Convention},
  year={2026},
  organization={IEEE}
}
```

## References

1. Mekterović, I., Brkić, L. (2025). "Can LLM Pass a CS1 Course?" MIPRO 48th ICT and Electronics Convention

## License

This research material is provided for academic use. See [LICENSE](LICENSE) for details.

## Contact

For questions about this research, please contact the authors or open an issue in this repository.
