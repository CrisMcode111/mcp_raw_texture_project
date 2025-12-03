


# Mini-Project – Part 1  
## MCP Client + Third-Party Servers Integration (Colab Version)

This folder contains all the work for **Part 1** of the MCP Mini-Project.  
The goal of this part is to build an **LLM-driven agentic workflow** that integrates **third-party MCP servers**, discovers tools dynamically, and executes a multi-step plan to achieve a user goal.

---

##  Objective

Build an end-to-end agent that:

- Connects to **two or more third-party MCP servers** from the official community list.  
- Discovers tools exposed by those servers.  
- Uses an **LLM (GroqCloud)** to decide which tool to use at each step.
- Executes multi-step reasoning with re-prompting and context accumulation.
- Implements basic **error handling, retry logic and fallback**.
- Logs all tool calls for **observability**.
- Runs entirely in **Google Colab**.

This Part 1 is designed to demonstrate that an LLM can orchestrate tool calls using community MCP servers without requiring custom server code.

---

##  Architecture Overview



LLM Planner (GroqCloud)
↓
MCP Client (Python)
↓
Third-Party MCP Servers
• search / web / scholar
• files / CSV / markdown
↓
Tools: fetch → clean → summarize → store


The agent dynamically chooses the order of tool calls depending on the user goal.

---

##  Contents of This Folder

- **`part1.ipynb`**  
  Main Colab notebook containing:
  - MCP client setup  
  - Server connections  
  - Tool discovery  
  - LLM orchestration logic  
  - Step-by-step execution  
  - Logging and error handling  

- **`requirements.txt`** (optional but recommended)  
  List of Python packages used in the notebook.

- **Any helper `.py` files** exported from Colab (if applicable).

---

##  How to Run Part 1

1. Open the notebook `part1.ipynb` in Google Colab or Jupyter.
2. Install dependencies:
   ```bash
   pip install mcp python-dotenv groq


Set the LLM backend (GroqCloud):

import os
os.environ["GROQ_API_KEY"] = "your_key_here"


Start the MCP client inside the notebook.

Connect to the selected third-party servers.

Run the orchestration cell:

run_agent("your user goal here")

 Example Goal Used

For this mini-project, the agent was tested using:

“tiger nut hydration behavior”

The workflow executed:

Search using a third-party search server

Extract scientific insights

Clean results

Generate raw dessert-specific interpretation

Save final output to markdown

The outcome is available in final_raw.md in the main repository.

Functional Requirements Checklist
Requirement	Status
≥ 2 third-party MCP servers	
LLM-driven planning	
Dynamic tool discovery	
Error handling	
Observability logs	
Env-based config	
Reproducible setup	
Notes

This Part 1 complements Part 2, where a fully custom MCP server is built in a multi-file Python project, integrated with the external servers used here.

Both parts together demonstrate the full MCP workflow:
using tools → creating tools → composing agents.

## 🧩 Architecture Overview

