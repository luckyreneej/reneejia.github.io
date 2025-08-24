---
title: "Reasoning in Large Language Models: A Research-Centric Overview"
date: 2025-05-25
categories:
  - AI Learning Guide
  - AI Research
  - Large Language Models
  - Machine Learning
tags:
  - reasoning
  - large language models
  - chain of thought
  - research overview
  - transformers
read_time: "15-25 min read"
---

Large Language Models (LLMs) such as GPT, PaLM, and Gemini have demonstrated emergent capabilities across a wide range of natural language tasks. A central research question remains: *can LLMs reason*? This blog synthesizes a recent CS25 lecture by **Denny Zhou (Google DeepMind)** ([YouTube Lecture](https://www.youtube.com/watch?v=ebnX5Ur1hBk)) with relevant foundational and contemporary research. The objective is to position reasoning in LLMs not as a philosophical debate but as a technical construct grounded in formal definitions, theoretical analysis, and empirical methodology.

---

## 1. Formalizing Reasoning in LLMs

Zhou emphasizes that the debate on "reasoning" often lacks rigor due to ambiguous definitions. His working definition is:

*Reasoning in LLMs is the generation of intermediate tokens (steps) between input and final output.*

These *reasoning tokens* represent step-by-step thought processes (e.g., stepwise solutions in math problems). This definition is concrete, measurable, and aligns with both theoretical and empirical findings.

**Example – Last Letter Concatenation Task:**
- Input: *"artificial intelligence"*  
- Without reasoning: Output → `LE`  
- With reasoning: Output → *"The last letter of artificial is L. The last letter of intelligence is E. Concatenating gives LE."*

---

## 2. Theoretical Underpinnings

- **Boolean Circuit Complexity (Zhou et al. + Stanford collaboration):** Any function computable by Boolean circuits of size *T* can be solved by a constant-size transformer generating *O(T)* intermediate tokens.  
  → Suggests *intermediate reasoning steps serve as computational depth surrogates*.

- **Neuro-Symbolic Precedents:** Intermediate steps mirror methods in program synthesis and symbolic AI, where reasoning chains reduce combinatorial explosion.

- **DeepMind (2017):** Introduced natural language intermediate tokens for math problem solving ([link](https://arxiv.org/abs/1706.01340)).

---

## 3. Techniques for Inducing and Enhancing Reasoning

### 3.1 Chain-of-Thought (CoT) Prompting
- *Wei et al., 2022* ([arXiv:2201.11903](https://arxiv.org/abs/2201.11903)).
- Adds exemplars or triggers such as *"Let's think step by step"* to reshape output distribution toward reasoning traces.

### 3.2 Self-Consistency
- *Wang et al., 2022* ([arXiv:2203.11171](https://arxiv.org/abs/2203.11171)).
- Sample multiple reasoning paths → marginalize over answers → select most frequent.

**Pseudocode:**
```
Algorithm SelfConsistency(Prompt x, Model M, Samples N):
    answers = []
    for i in 1..N do
        reasoning, answer = Sample(M, x)
        answers.append(answer)
    return Mode(answers)
```

### 3.3 Decoding Strategies
- Greedy decoding suppresses reasoning.  
- **CoT decoding:** Expand beyond top-1 candidates; select outputs with higher *final-answer confidence*.

### 3.4 Supervised Fine-Tuning (SFT)
- Train on human-annotated reasoning traces (e.g., GSM8K [Cobbe et al., 2021](https://arxiv.org/abs/2110.14168)).
- Limitation: poor generalization.

### 3.5 Reinforcement Learning Fine-Tuning (RLFT / RLAIF)
- *STAR: Self-Taught Reasoner* ([Zelikman et al., 2022](https://arxiv.org/abs/2203.14465)).
- Models generate traces; verifier filters correct ones → iterative improvement.

**Pseudocode:**
```
Algorithm RLFT(Prompt x, Model M, Verifier V, Iterations T):
    for t in 1..T do
        reasoning, answer = Sample(M, x)
        if V(answer) == correct then
            Update(M, reasoning, answer)
    return M
```

### 3.6 Scaling Chain-of-Thought Length
- Longer reasoning traces → stronger generalization.
- Sometimes more impactful than scaling parameter count.

---

## 4. Retrieval and Aggregation as Enhancements

- **Aggregation Approaches:** Self-consistency, consensus decoding, ensembles (OpenAI's o1 model, 2024).
- **Retrieval-Augmented Reasoning:** Analogical reasoning via recalling related problems. E.g., *step-back prompts* for geometry tasks.

---

## 5. Related Work: Comparison of Methods

| Method                   | Core Idea | Strengths | Weaknesses |
|--------------------------|-----------|-----------|-------------|
| **Chain-of-Thought (CoT)** | Prompting model with exemplars or "Let's think step by step" | Simple, effective for many tasks | Requires careful prompt design; inconsistent |
| **Self-Consistency**     | Sample multiple reasoning paths, choose most frequent | Improves accuracy significantly; uncertainty calibration | Computationally expensive (multiple samples) |
| **Decoding (CoT Decoding)** | Explore beyond greedy decoding, select based on confidence | Surfaces latent reasoning already in pretrained models | Still heuristic; may miss optimal reasoning path |
| **Supervised Fine-Tuning (SFT)** | Train on human-annotated reasoning traces | Strong performance on seen distributions | Poor generalization; costly human annotation |
| **RL Fine-Tuning (RLFT)** | Model generates reasoning traces, verifier selects correct ones | Generalizes better, reduces human dependency | Requires reliable verifiers; limited to verifiable tasks |
| **Retrieval + Reasoning** | Recall related problems/knowledge during reasoning | Extends reasoning to broader knowledge | Retrieval quality critical; risk of overfitting to retrieved context |

---

## 6. Limitations and Open Research Problems

- **Non-verifiable tasks** (creative writing, real-world programming).  
- **Hallucinations**: Confidence estimation imperfect.  
- **Benchmark saturation**: Need new evaluations measuring compositional generalization and real-world robustness.

---

## 7. Future Research Directions

1. **Beyond Verifiable Tasks:** Extending RLFT to subjective domains.  
2. **Scaling Dimensions:** Reasoning length, verifier accuracy, retrieval breadth.  
3. **Hybrid Neuro-Symbolic Systems:** E.g., Logic-LM ([Xu et al., 2023](https://arxiv.org/abs/2305.12295)).  
4. **Application-Level Reasoning:** Coding assistants, theorem proving, decision-support.

---

## 8. Key References

- Wei et al., 2022 – Chain-of-Thought Prompting ([arXiv:2201.11903](https://arxiv.org/abs/2201.11903))  
- Wang et al., 2022 – Self-Consistency ([arXiv:2203.11171](https://arxiv.org/abs/2203.11171))  
- Cobbe et al., 2021 – GSM8K ([arXiv:2110.14168](https://arxiv.org/abs/2110.14168))  
- Zelikman et al., 2022 – STAR ([arXiv:2203.14465](https://arxiv.org/abs/2203.14465))  
- Xu et al., 2023 – Logic-LM ([arXiv:2305.12295](https://arxiv.org/abs/2305.12295))  
- Reasoning in LLMs: A Geometric Perspective (2024) ([arXiv:2407.02678](https://arxiv.org/abs/2407.02678))  
- Survey of Reasoning in LLMs (2025) ([arXiv:2502.17419](https://arxiv.org/abs/2502.17419))  
- Sutton, 2019 – *The Bitter Lesson* ([link](http://www.incompleteideas.net/IncIdeas/BitterLesson.html))

---

## Summary

Reasoning in LLMs can be understood as the probabilistic generation of intermediate steps, rather than symbolic deduction. Zhou's lecture demonstrates that pretrained models already contain latent reasoning abilities; the research challenge is to surface and refine these capabilities through prompting, decoding, fine-tuning, and scaling. The comparative analysis highlights trade-offs: **CoT is simple but fragile, self-consistency is powerful but costly, and RLFT generalizes well but relies on verifiability**. Retrieval offers another layer of enhancement, but with dependency on retrieval quality. Open research problems remain in **non-verifiable domains, hybrid neuro-symbolic frameworks, and application-level deployments**.

> *"The truth always turns out to be simpler than you thought."* — Richard Feynman

---

{% include citation.html 
  title="Reasoning in Large Language Models: A Research-Centric Overview"
  author="Renee Jia"
  journal="renee-jia.github.io"
  year="2025"
  url="https://renee-jia.github.io/ai-learning-guide/llm-reasoning-research-overview/"
  bibtex_key="reneejia2025llmreasoning"
%}
