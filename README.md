## 👨‍🎓 Author Details
**Name:** Hrishikesh Lal Baishya  
**Roll No.:** 23B0743  
**Department:** Civil Engineering  
**University:** Indian Institute of Technology Bombay  

---

# 🧠 TinyAgent — Function Calling at the Edge (Modified Open Version)

TinyAgent is a lightweight **AI agent framework** designed for **function calling, reasoning, and task automation** using **Small Language Models (SLMs)** that can run locally.  
This repository contains the open-source **server-side implementation and model integration code** for demonstration and academic purposes.  
*(Note: The macOS app component has been removed in this version.)*

---


## 📁 Project Structure
TinyAgent/
├── README.md                # Project overview and documentation  
├── requirements.txt         # Python dependencies  
├── run_tiny_agent_server.py # Script to start the agent server  
└── src/                     # Core source code (models, tools, sub-agents)

---

## 🚀 Quick Start

### 1️⃣ Installation
pip install -r requirements.txt

### 2️⃣ Run the Agent Server
python run_tiny_agent_server.py

This starts the TinyAgent backend, enabling local or API-based interaction for executing reasoning and function-calling tasks.

---

## 🧩 AI Agent Architecture Document

### Overview
TinyAgent brings complex reasoning and function-calling capabilities to **Small Language Models (SLMs)**.  
It enables private, efficient on-device automation tasks such as composing emails, creating calendar events, managing notes, and summarizing files — all powered by fine-tuned LoRA models.

---

### Core Components
| Component | Description |
|------------|-------------|
| **Main Agent** | Orchestrates user interactions — parses intent, selects tools or sub-agents, and executes function calls. |
| **Sub-Agents** | Smaller specialized models for tasks like summarization, note-writing, or scheduling. Each inherits from `SubAgent`. |
| **ToolRAG Module** | Retrieves relevant tools and examples for each query, minimizing hallucinations and maximizing accuracy. |
| **Function Tools** | Defined in `src/tiny_agent_tools.py` — includes operations such as `create_event()`, `send_email()`, `summarize_pdf()`. |
| **Model Loader** | Manages TinyAgent fine-tuned models (1.1B or 7B) with LoRA adapters. |
| **Server Script** | `run_tiny_agent_server.py` initializes the system and launches the local API endpoint. |

---

### Interaction Flow
User Prompt  
↓  
Main Agent parses intent  
↓  
ToolRAG retrieves best tools and examples  
↓  
Sub-Agent or Function Tool selected  
↓  
Task executed (email, note, summary, etc.)  
↓  
Response returned to the user

---

### Models Used
| Model | Purpose | Reason for Choice |
|--------|----------|------------------|
| **TinyAgent-1.1B / 7B (LoRA)** | Core reasoning and planning | Efficient for on-device deployment while maintaining high reasoning accuracy. |
| **ToolRAG (Retriever Model)** | Tool and example selection | Ensures context relevance and better multi-step reasoning. |
| **Whisper (Optional)** | Speech-to-text | Adds multimodal (voice) interaction capability. |

---

## 📊 Data Science Report

### Fine-Tuning Setup
| Aspect | Details |
|---------|----------|
| **Base Models** | TinyLLaMA-1.1B-32K and WizardLM-2-7B |
| **Fine-Tuning Method** | LoRA (Low-Rank Adaptation) via PEFT |
| **Dataset** | [TinyAgent Dataset (40K real-world use cases)](https://huggingface.co/datasets/squeeze-ai-lab/TinyAgent-dataset) |
| **Data Type** | Function-calling and automation data (emails, meetings, notes, reminders, file summaries). |
| **Objective** | Enable compact models to perform reasoning and planning for daily automation. |
| **Frameworks Used** | PyTorch, PEFT, HuggingFace Transformers |
| **Loss Function** | Cross-entropy on instruction–response pairs |
| **Hardware** | 4×A100 GPUs (as per TinyAgent paper) |

---

### Fine-Tuning Results
| Model | Success Rate | Improvement vs Base |
|--------|---------------|---------------------|
| GPT-3.5-turbo | 65.04% | — |
| GPT-4-turbo | 79.08% | — |
| **TinyAgent-1.1B + ToolRAG** | **80.06%** | +67% over base TinyLLaMA |
| **TinyAgent-7B + ToolRAG** | **84.95%** | +43% over base WizardLM |

---

### Evaluation Methodology
| Category | Metric | Description |
|-----------|---------|-------------|
| **Quantitative** | Task Success Rate (%) | Percentage of successfully completed automation tasks. |
| | Latency (s) | Time taken per reasoning or function call. |
| **Qualitative** | Human Evaluation | Reviewers rated fluency, correctness, and contextual relevance (scale 1–5). |
| **Ablation Study** | ToolRAG vs No-ToolRAG | Compared success rates and hallucination levels. |

#### Key Findings
- LoRA fine-tuned SLMs outperform GPT-3.5 and approach GPT-4 accuracy.  
- ToolRAG improves tool choice precision by ~20%.  
- Models remain lightweight (≤3 GB memory), enabling smooth local execution.  

---

## 💬 Example Interaction Logs

### Example 1 — Calendar Event
User: Create an event called 'Meeting with Sid' on Friday at 3 PM  
Agent: Event created in Calendar: “Meeting with Sid”, scheduled for Friday 3 PM.

### Example 2 — Email Composition
User: Email Nick about the budget update and attach budget.pdf  
Agent: Draft created and ready for review. Attachment budget.pdf included.

### Example 3 — Document Summarization
User: Summarize the file LLM_Compiler.pdf and save the result to Notes  
Agent: Generated summary (150 words) and saved under Notes/MeetingSummaries.

---

## 🧾 Deliverables Mapping
| Deliverable | Location |
|--------------|-----------|
| **Source Code** | `src/` |
| **Architecture Document** | Included in this README |
| **Fine-Tuning Setup** | See *Data Science Report* section |
| **Evaluation Results** | See *Evaluation Methodology* section |
| **Interaction Logs** | See *Example Interaction Logs* section |
| **Execution Script** | `run_tiny_agent_server.py` |

---

## 🧰 Tools and Libraries
- **Python 3.10+**  
- **PyTorch**  
- **Transformers (HuggingFace)**  
- **PEFT (LoRA Fine-Tuning)**  
- **FastAPI / Flask** — backend serving  
- **ToolRAG** — retrieval-augmented grounding  
- **Whisper (optional)** — speech-to-text interface  
---
