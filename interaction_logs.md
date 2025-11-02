# 💬 Interaction Logs — TinyAgent

This document provides example user–agent interactions that demonstrate the fine-tuned **TinyAgent** model’s reasoning, function-calling, and task execution capabilities.  
Each example captures the **prompt**, **model’s reasoning**, **tool invocation**, and **final response** to show end-to-end workflow automation.

---

## 🧠 Session Metadata

| Property | Details |
|-----------|----------|
| **Model Used** | TinyAgent-1.1B (LoRA fine-tuned) |
| **Retriever** | ToolRAG |
| **Interface** | Local FastAPI server |
| **Mode** | Function Calling + Text Response |
| **Evaluator** | Hrishikesh Lal Baishya — IIT Bombay |
| **Date** | November 2025 |

---

## 🗓️ Example 1 — Calendar Scheduling

**Prompt:**  
> "Schedule a meeting with Prof. Nirmale on Wednesday at 4 PM to discuss CE465 project progress."

**Agent Internal Reasoning:**  
- Intent identified: *create calendar event*.  
- Extracted entities: Prof. Nirmale, Wednesday, 4 PM, CE465 project progress.  
- Selected tool: `create_event()` from calendar tools.

**Function Call (Simulated):**
```json
{
  "function": "create_event",
  "parameters": {
    "title": "Meeting with Prof. Nirmale",
    "datetime": "2025-11-05T16:00:00",
    "description": "Discussion on CE465 project progress"
  }
}
