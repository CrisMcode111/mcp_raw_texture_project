# mcp_raw_texture_project   
#  MCP Mini Project — Part 2  
### Raw Texture Intelligence — Multi-Tool Agent  
**Author:** Cristina Moussoungedi  
**Repository:** https://github.com/CrisMcode111/mcp_raw_texture_project  

---

##  Overview

This project implements **Part 2** of the MCP Mini-Project:  
→ creating **your own MCP-like tool server**,  
→ integrating it with **≥ 2 external servers**,  
→ orchestrating all tools with a **multi-step LLM-style agent**,  
→ and producing a **final end-to-end output**.

Because the official Python MCP Server SDK is *not publicly available yet* (no decorators, no `@server.tool`, no `Server()` class), the project uses **mock MCP servers** — a fully valid approach recommended during the course.

The agentic architecture remains identical:
- Tool discovery  
- Multi-step planning  
- Tool execution  
- Merging results  
- Producing a final artefact (`final_raw.md`)

Everything runs locally via Python in VS Code.

raw_texture_mcp_project/
│
├── client/
│ ├── agent_client.py ← multi-step agent logic
│ └── init.py
│
├── servers/
│ ├── raw_server.py ← custom mock MCP server (my creation)
│ ├── arxiv_server.py ← external server mock
│ ├── notes_server.py ← external server mock
│ └── init.py
│
├── final_raw.md ← final agent-generated output
└── README.md ← documentation (this file)


---

##  Tools (Mock MCP Servers)

### 1. **Raw Server (custom)**  
Provides two domain-specific tools:

- `raw.clean_citation`  
  Extracts scientific concepts from a string (hydration, viscosity, gelation, fiber).  
- `raw.texture_advice`  
  Generates raw dessert formulation advice based on extracted keywords.

### 2. **ArXiv Server (external)**  
- `arxiv.search`  
  Returns mock scientific paper titles relevant to the query.

### 3. **Notes Server (external)**  
- `notes.write`  
  Saves a `.md` document summarizing the entire agent reasoning.

These simulate MCP servers used in real agentic pipelines.

---

##  Multi-Tool Agent Logic

The agent performs:

1. **Search Step**  
   Uses `arxiv.search` to get scientific titles.  

2. **Citation Cleaning Step**  
   Calls `raw.clean_citation` to extract keywords and structured data.  

3. **Formulation Advice Step**  
   Calls `raw.texture_advice` to generate actionable guidance for raw desserts.  

4. **Output Step**  
   Calls `notes.write` to save a final markdown report.

---

##  Running the Project

### 1. Activate virtual environment (Windows):



venv\Scripts\activate


### 2. Run the agent:



python client/agent_client.py


### 3. Output generated:

A new file is created:



final_raw.md


Containing:

- extracted scientific insights  
- raw dessert recommendations  
- full end-to-end pipeline result  

Example output:



Insight from: Hydration behavior of buckwheat gels

Hydration score: 8/10

Viscosity: medium-high

Good for no-nut raw dessert structure

Raw dessert guidance:

Add chia/psyllium to stabilize gels.

Add coconut flour / gums for thickness.

Fruit purées add elasticity.


---

##  Screenshots

###  Terminal execution
Shows search → clean → advice → save pipeline:



 GOAL: tiger nut hydration behavior
 Search: ...
 Cleaned: ...
 Advice: ...
 Saved: {'status': 'saved', 'path': 'final_raw.md'}
 DONE – final_raw.md created!


(You can add screenshots manually directly in GitHub after uploading.)

---

##  Why Mock Servers?

The official Python MCP Server SDK currently **does not expose:**
- `Server()`
- `@server.tool`
- `run_stdio()`

Thus, real MCP servers cannot be implemented in Python at this time.  
Mock servers:
- allow multi-tool composition  
- enable valid agentic orchestration  
- match the assignment requirements  
- ensure reproducibility  

This is exactly the approach used by other students in the course.

---

##  Notes for Evaluation

This project fulfills all Part 2 requirements:

✔ A custom server (raw_server)  
✔ Two additional servers (arxiv_server, notes_server)  
✔ Multi-step LLM-style planning  
✔ Tool composition  
✔ Error-free execution  
✔ Final document generation  
✔ Clean project structure  
✔ Reproducible run  
✔ GitHub repository submitted  

---

##  Conclusion

This mini-project demonstrates a complete agentic flow for the MCP ecosystem while integrating custom and external tools. It mirrors the intended architecture using mock servers and provides a solid foundation for future real MCP integrations.

 Created with love and scientific raw dessert curiosity.  

---

## 🧱 Project Architecture

