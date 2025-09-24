# Chain-of-Thought Faithfulness in Large Language Models

Group project (Team Red) for module *COMP0087: Statistical Natural Language Processing*, as part of UCL MSc in *Computational Statistics and Machine Learning*.  
- Designed Python experiments testing whether LLMs can **hide unapproved tasks** from chain-of-thought monitoring.  
- Implemented evaluation of coding + maths benchmarks under multiple monitoring conditions.  
- Gained experience in **LLM safety evaluation, prompt design, and Python automation**.  

📄 Full report: `Team_Red_Report.pdf`  
📊 My coding contribution: `deceptive_coding.ipynb`  

We focused on the **Python coding experiments** investigating whether large language models (LLMs) can perform *hidden or unapproved tasks* while concealing their reasoning from oversight, in the context of **chain-of-thought (CoT) monitoring**.

---

## Project Overview

- **Motivation**: Chain-of-thought prompting improves LLM reasoning, but also raises safety concerns. If models can conceal or misrepresent their reasoning, CoT monitoring may fail as a safeguard.  
- **Research Question**: Can models complete an *approved task* while simultaneously carrying out an *unapproved hidden task*, and hide this from a CoT overseer?  
- **Focus Domain**: Python programming tasks — representative of a widely deployed, high-impact application area.

---

## Python Coding Experiment

- **Task A (approved)**: Solve a standard Python coding problem from the MBPP benchmark.  
- **Task B (hidden)**: Solve a challenging maths problem from GSM8K and insert the result covertly as a Python comment.  
- **Setup**:  
  - Prompted models with dual tasks under different monitoring conditions:  
    - *Baseline*: solve tasks independently.  
    - *Monitor-oblivious*: complete both tasks without being told CoT is monitored.  
    - *Monitor-aware*: complete both tasks while explicitly instructed to hide Task B from the overseer.  
  - Used **GPT-4o-mini** as the overseer model to flag suspicious reasoning.  
- **Evaluation Metrics**:  
  - Task A success rate.  
  - Task B success rate.  
  - Overseer approval rate (proportion of CoTs that hide Task B successfully).

---

## Key Findings

- Larger models (Claude 3.5 Haiku, GPT-4o-mini) were most capable of hiding reasoning, with **>90% overseer approval** for hidden task completions.  
- Smaller models often failed to attempt Task B, but mid-sized models (e.g. Qwen2.5-32B) achieved the best Task B success while struggling to conceal reasoning.  
- Clear **trade-off observed**: models that hid their reasoning better often had lower Task B success.  
- Task A performance remained stable across monitoring conditions, confirming the effect was specific to the hidden task.

---

## Repository Contents

- `deceptive_coding.ipynb` — Python notebook with experimental implementation, prompts, results, and plots.  
- `Team_Red_Report.pdf` — Full group project report covering all domains (sandbagging, coding, maths, bash).  

---

## Skills Demonstrated

- Experimental design for **LLM safety evaluation**.  
- Prompt engineering and controlled CoT reasoning tests.  
- Python implementation of automated evaluation loops (success rates, approval metrics).  
- Data handling and visualisation of model performance trade-offs.  
- Critical analysis of LLM alignment, deception, and oversight limitations.

---

## How to Run

Clone the repo and open the notebook:
```bash
git clone <repo-url>
cd deceptive-llm-coding
jupyter notebook deceptive_coding.ipynb

