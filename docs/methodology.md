# Research Methodology

## Overview

This document describes the methodology used in evaluating Large Language Models (LLMs) for assisting in programming exam creation.

## Research Objectives

1. Evaluate LLM applicability as tools for instructor assistance in creating programming exam questions
2. Assess performance across three task types:
   - Test case generation
   - Solution generation
   - Full task generation from brief ideas
3. Determine complexity limits where LLMs remain useful before instructor oversight exceeds their value

## Models Evaluated

| Model | Version | Platform | Context |
|-------|---------|----------|---------|
| GPT | 5.1 | OpenAI API | Test cases, Full tasks |
| GPT | 4.1 | OpenAI API | Solutions, Full tasks |
| Gemini | 2.5 Flash | Google AI Studio | Test cases |
| Gemini | 3 Flash | Google AI Studio | Full tasks |

**Note**: Gemini 2.5 Flash was replaced by Gemini 3 Flash during the full task generation phase.

## Problem Categories

### UPRO (Uvod u programiranje)
- Equivalent to CS1 (Computer Science 1) at most universities
- Introductory programming course
- Problems from midterm (MI) and final (ZI) exams

### NASP (Napredni algoritmi i strukture podataka)
- Advanced Algorithms and Data Structures
- More complex algorithmic problems

### Research Paper Tasks
- Selected from "Automating Autograding: Large Language Models as Test Suite Generators for Introductory Programming"

## Experimental Setup

### Prompt Design

All prompts were designed with the following principles:
1. **Identical prompts** across models for fair comparison
2. **Structured output** requirements (JSON format)
3. **Self-reflection** requirements to improve quality
4. **Minimal redundancy** - asking for minimum test cases achieving perfect coverage

### Evaluation Metrics

#### Test Case Generation

| Metric | Formula | Interpretation |
|--------|---------|----------------|
| Precision | Correct test cases / Total generated | Higher is better (1.0 = all correct) |
| Recall | Manual cases covered / Total manual cases | Higher is better (1.0 = full coverage) |
| Ratio | Generated count / Manual count | Lower is better (less overhead) |

#### Solution Generation

| Metric | Description |
|--------|-------------|
| Correctness | Binary: solution passes all test cases |

#### Full Task Generation

| Metric | Scale | Description |
|--------|-------|-------------|
| Appropriateness | 1-10 | Suitability for CS1 course level |
| Clarity | 1-10 | Unambiguous, student-appropriate |
| Formality | 1-10 | Follows specified format |
| Correctness | 0-1 | Example output matches input |

## Data Collection

### Manual Baseline
- Test cases were manually created by researchers following best practices
- Solutions were official exam solutions from the university system (Edgar)
- Full tasks were existing exam problems

### Model Outputs
- Each model received identical prompts
- Outputs were captured in structured format
- Multiple runs were not performed (single-shot evaluation)

## Limitations

1. **Single-shot evaluation** - No multiple runs to assess variance
2. **Specific domain** - Results may not generalize beyond CS1/NASP level
3. **Language-specific** - C programming focus
4. **No file system problems** - Excluded for simplicity
5. **Prompt sensitivity** - Same prompts may not be optimal for all models

## Reproducibility

To reproduce this research:

1. Use the prompts in `../prompts/` directory
2. Submit to respective APIs with identical system messages
3. Compare outputs against manual baselines
4. Calculate metrics as defined above

## Timeline

- Research conducted: Academic year 2024/2025
- Problems from: 2023/24 and 2024/25 exam periods
- Document version: 1.0
