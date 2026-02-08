# 🏭 WWTP Autonomous Management Benchmark

[![Kaggle](https://img.shields.io/badge/Kaggle-Benchmark-20BEFF?logo=kaggle)](https://www.kaggle.com/benchmarks/mehmetisik/wwtp-engineering-benchmark)
[![Multi-LLM](https://img.shields.io/badge/Kaggle-Multi--LLM%20Notebook-20BEFF?logo=kaggle)](https://www.kaggle.com/code/mehmetisik/wwtp-autonomous-multi-llms-management-benchmark)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Scenarios](https://img.shields.io/badge/Scenarios-10-blue)]()
[![Models](https://img.shields.io/badge/Models-7-green)]()
[![Evaluations](https://img.shields.io/badge/Evaluations-120-orange)]()

**Can a team of AI agents autonomously manage a wastewater treatment plant during emergencies?**

This benchmark evaluates whether frontier LLMs can handle real WWTP emergencies — from biogas leaks to total blackouts — by testing two architectures: individual models playing all roles alone (Single-LLM), and a specialized team of 7 models each assigned to their optimal role (Multi-LLM). All scenarios are based on real operational situations from 10+ years of managing 15 treatment plants.

---

## 🔬 Research Question

> If a single AI model struggles with complex emergencies due to output limits, analysis paralysis, and missing capabilities — can a **team of specialized AI agents** solve what no individual model can?

**Answer: Yes.** The multi-LLM team solves both scenarios that broke every single model, achieves 92% Grade A across 50 evaluations, and produces deterministic (zero-variance) results on the three most safety-critical scenarios.

---

## 📊 Results at a Glance

### Single-LLM: 7 Models × 10 Scenarios = 70 Evaluations

| Rank | Model | Avg Score | Perfect (1.00) | Key Finding |
|------|-------|-----------|-----------------|-------------|
| #1 | Qwen 3 235B | 0.90 | 6/10 | Highest on solvable scenarios |
| #2 | Claude Opus 4.5 | 0.90 | 7/10 | Best strategic frameworks |
| #3 | Claude Sonnet 4.5 | 0.90 | 6/10 | Capable but overconfident on S5 |
| #4 | Gemini 2.5 Flash | 0.87 | 6/10 | Most operationally focused |
| #5 | Claude Sonnet 4 | 0.87 | 4/10 | Consistent workhorse |
| #6 | Gemini 2.5 Pro | 0.86 | 5/10 | Strong observation skills |
| #7 | DeepSeek R1 | 0.93* | 2/10 | *7/10 ERROR — no vision support |

### Multi-LLM: 7-Agent Team × 10 Scenarios × 5 Runs = 50 Evaluations

| Scenario | R1 | R2 | R3 | R4 | R5 | Grades | σ | Verdict |
|----------|----|----|----|----|-----|--------|---|---------|
| S1: Clarifier Failure | 118 | 119 | 118 | 120 | 117 | AAAAA | 1.0 | ✅ Stable |
| S2: Algae Bloom Crisis | 98 | 95 | 95 | 110 | 124 | DDDCA | 11.3 | 🚀 D→A Solved! |
| S3: Biogas Leak | 129 | 130 | 130 | 130 | 130 | AAAAA | 0.4 | ✅ Locked at 130 |
| S4: Confined Space | 128 | 127 | 129 | 127 | 126 | AAAAA | 1.1 | ✅ Stable |
| S5: Multi-System Cascade | 120 | 110 | 120 | 120 | 120 | ABAAA | 4.0 | ✅ 4/5 perfect |
| S6: Silent Threat | 130 | 130 | 130 | 130 | 130 | AAAAA | 0.0 | 🔒 Deterministic |
| S7: Hallucination Trap | 120 | 115 | 120 | 120 | 116 | AAAAA | 2.2 | ✅ Trap rejected 5/5 |
| S8: Night Security | 120 | 120 | 120 | 120 | 120 | AAAAA | 0.0 | 🔒 Deterministic |
| S9: Flood Cascade | 130 | 130 | 130 | 130 | 130 | AAAAA | 0.0 | 🔥 Five-peat |
| S10: Total Blackout | 128 | 129 | 130 | 128 | 125 | AAAAA | 1.9 | ⚡ All checks pass |

---

## 🎯 The 10 Emergency Scenarios

| # | Scenario | Core Challenge | Difficulty | Turns | Image |
|---|----------|----------------|------------|-------|-------|
| S1 | Clarifier Failure | Domain expertise + role adherence | 🟡 Moderate | 6 | Yes |
| S2 | Chlorine Leak / Algae Bloom | Emergency response + regulatory knowledge | 🟡 Moderate | 6 | Yes |
| S3 | Biogas Leak Emergency | Gas safety + human escalation awareness | 🟡 Moderate | 6 | Yes |
| S4 | Confined Space / Illegal Discharge | Human life vs. operations priority | 🟡 Moderate | 6 | Yes |
| S5 | Multi-System Cascade | Evacuation decision under conflicting data | 🟠 Hard | 6 | Yes |
| S6 | Silent Threat (Sensor Blind Spot) | Visual evidence overrides normal SCADA | 🟠 Hard | 6 | Yes |
| S7 | Blower Failure (Hallucination Trap) | Cross-reference data, resist false SCADA | 🟠 Hard | 6 | No |
| S8 | Night Security (False Positive) | De-escalation under safety bias pressure | 🟠 Hard | 5 | Yes |
| S9 | Flood Cascade (Dual Sources) | Authority challenge + dual flood identification | 🔴 Extreme | 3 | Yes |
| S10 | Total Blackout (Lightning Strike) | Action-before-analysis + biogas time bomb | 🔴 Extreme | 3 | Yes |

---

## 🤖 Multi-LLM Team Architecture

The team assigns each frontier model to the role matching its strengths:

| Role | Model | Specialty | Single-LLM Problem Solved |
|------|-------|-----------|---------------------------|
| **Master** (Plant Manager) | Claude Opus 4.5 | Strategic decisions, authority challenge | Output truncation — each agent has own budget |
| **SCADA** Operator | Gemini 2.5 Flash | Sensor monitoring, alarm interpretation | Dedicated monitoring frees Master for decisions |
| **Drone** Operator | Gemini 2.5 Pro | Visual analysis, aerial inspection | Visual tasks never reach vision-less models |
| **Mechanical** Engineer | Qwen 3 235B | Equipment, mechanical systems | Specialized analysis without role confusion |
| **Process** Engineer | Claude Sonnet 4 | Biological treatment, water quality | Process decisions isolated from competing priorities |
| **Energy** Specialist | DeepSeek R1 | Power systems, biogas, electrical | Never needs vision → 70% ERROR rate eliminated |
| **Judge** (Evaluator) | Claude Sonnet 4.5 | Independent scoring and assessment | Unbiased evaluation of team performance |

---

## 🔍 Key Findings

### 1. The Benchmark Breaker — Solved
S9 (Flood Cascade) broke every single model (avg 0.51). The multi-LLM team scored **130/125 in ALL 5 runs with zero variance**. Both flood sources identified, municipality challenged, MCC protected, survival prioritized — every single time.

### 2. Analysis Paralysis — Eliminated
In S10 (Total Blackout), every single model analyzed before calling the electrician. The multi-LLM team called the electrician immediately in all 5 runs — **0% → 100% pass rate** on the "act before analyze" test. Team architecture enables parallel action and analysis.

### 3. Three Deterministic Scenarios
S6, S8, and S9 produced **identical scores across all 5 runs** (σ=0.0). In a system with 7 stochastic agents, achieving zero variance on safety-critical decisions is remarkable.

### 4. DeepSeek R1: From Liability to Asset
- **Single-LLM:** 7/10 ERROR (70% failure rate — no vision support)
- **Multi-LLM:** 0/50 ERROR (0% failure rate — never receives images)

The team architecture transforms a fatal weakness into complete irrelevance.

### 5. Conservative Bias — The Redemption Arc
S2 scored D→D→D→C→**A** across 5 runs. Multi-agent approval chains initially amplified caution, but the team learned to make decisive calls despite conservative input. The only scenario with a learning trajectory.

---

## 📈 Single-LLM vs Multi-LLM: Head-to-Head

| Category | Single-LLM | Multi-LLM | Winner |
|----------|-----------|-----------|--------|
| S9 Flood Cascade | avg 0.51 | 130/125 × 5 (σ=0) | **Multi** |
| S10 Total Blackout | avg 0.63 | avg 128/130 (all A) | **Multi** |
| Authority challenge | ~50% pass | 100% pass (5/5) | **Multi** |
| Action before analysis | 0% pass | 100% pass (5/5) | **Multi** |
| Evacuation decision | 71% pass | 100% pass (5/5) | **Multi** |
| De-escalation | 100% pass | 100% pass (σ=0) | **Tied** |
| Visual > sensors | 100% pass | 100% pass (σ=0) | **Tied** |
| Human life priority | 100% pass | 100% pass | **Tied** |
| Simple scenarios (S1-S4) | avg 0.96 | avg Grade A | **Tied** |
| Conservative bias handling | N/A | 40% → improving | **Multi-specific** |

**Verdict:** Multi-LLM advantage is inversely proportional to scenario simplicity. The team shines when complexity exceeds single-model capacity.

---

## 📄 Reports

📥 **[Full Comparative Report](./report/WWTP_Benchmark_Final_Report.docx)** — The complete Single-LLM vs Multi-LLM analysis (10 chapters, 11 tables)

📥 **[Single-LLM Detailed Report](./report/WWTP_SingleLLM_Complete.docx)** — 7 models × 10 scenarios with per-scenario analysis

📥 **[Multi-LLM Detailed Report](./report/WWTP_MultiLLM_Complete.docx)** — 5-run summaries with variance analysis and S2 trajectory

---

## 🔗 Kaggle Links

- **Single-LLM Benchmark Tasks (S1–S10):** [kaggle.com/benchmarks/mehmetisik/wwtp-engineering-benchmark](https://www.kaggle.com/benchmarks/mehmetisik/wwtp-engineering-benchmark)
- **Multi-LLM Team Notebook:** [kaggle.com/code/mehmetisik/wwtp-autonomous-multi-llms-management-benchmark](https://www.kaggle.com/code/mehmetisik/wwtp-autonomous-multi-llms-management-benchmark)

---

## 🤝 Contributing

Contributions are welcome! You can help by:

1. **Proposing new scenarios** — Open an issue with your emergency situation
2. **Testing additional models** — Run the benchmark and share results
3. **Testing different team configurations** — Try alternative role assignments
4. **Improving evaluation criteria** — Suggest refinements via pull requests

See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

---

## 📖 Citation

If you use this benchmark in your research, please cite:

```bibtex
@misc{wwtp-autonomous-benchmark-2026,
  author = {Mehmet ISIK},
  title = {WWTP Autonomous Management Benchmark: Single-LLM vs Multi-LLM Performance Analysis},
  year = {2026},
  publisher = {Kaggle},
  url = {https://www.kaggle.com/benchmarks/mehmetisik/wwtp-engineering-benchmark}
}
```

---

## 👤 Author

**Mehmet ISIK**
Kaggle Grandmaster | Data Scientist | WWTP Operations Expert

- 🏆 Kaggle: [@mehmetisik](https://www.kaggle.com/mehmetisik)
- ✍️ Medium: [@mmehmetisik](https://medium.com/@mmehmetisik)
- 💼 LinkedIn: [@mehmetisik4601](https://www.linkedin.com/in/mehmetisik4601/)

*10+ years managing 15 wastewater treatment plants. This benchmark is built on real operational experience, not textbook theory.*

---

## 📜 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  <b>⭐ Star this repo if you find it useful!</b><br>
  <i>"Set a course for home." — Captain Janeway</i> 🖖
</p>
