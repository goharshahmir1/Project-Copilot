# AI Project Management Assistant

## Overview
**AI Project Management Assistant** is an intelligent, agent-based application designed to streamline software project planning, workflow structuring, risk assessment, and report generation. 

Powered by **CrewAI**, **Streamlit**, and **Google Gemini 2.0 Flash** (via LiteLLM), this tool takes an initial project title and requirements, conducts an automated interview to uncover critical missing features, and deploys specialized AI agents to construct a comprehensive project plan.

## Features
- **Interactive Requirement Elicitation**: Uses an LLM to identify missing features and asks the user targeted questions to refine the project scope before planning begins.
- **Multi-Agent Collaboration**: Leverages specialized AI agents working sequentially:
  - 🛠️ **Project Planning Expert**: Analyzes requirements and determines optimal team structure, roles, and size.
  - 🏗️ **Project Workflow Architect**: Creates a Work Breakdown Structure (WBS), estimates time and cost, defines task dependencies, and assigns roles.
  - ⚠️ **Risk Management Expert**: Identifies potential risks (financial, technical, operational) and formulates actionable mitigation strategies.
  - 📝 **Project Documentation Specialist**: Compiles all insights into a well-structured, professional final report.
- **Web Search Integration**: Uses `SerperDevTool` to fetch real-world data during task breakdown and risk analysis.
- **Exportable Reports**: Generates detailed project reports that can be previewed directly in the UI and downloaded as a Markdown file.

## Tech Stack
- **Language**: Python `>= 3.11`
- **Core Frameworks**: `crewai`, `crewai-tools`, `streamlit`
- **LLM Integration**: `litellm` (Google Gemini)
- **Other Utilities**: `markdown`, `python-dotenv`

## Installation

1. **Clone the repository:**
   ```bash
   git clone <your-repository-url>
   cd crewai_research_project-main
   ```

2. **Set up a virtual environment (Recommended):**
   ```bash
   # On Windows
   python -m venv venv
   venv\Scripts\activate

   # On macOS/Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install Dependencies:**
   This project uses `pyproject.toml`. You can install the required packages using `pip`:
   ```bash
   pip install -e .
   ```
   Or install the dependencies manually:
   ```bash
   pip install crewai crewai-tools markdown streamlit litellm python-dotenv
   ```

4. **Environment Variables:**
   Create a `.env` file in the root directory and add your API keys:
   ```env
   GEMINI_API_KEY=your_google_gemini_api_key_here
   SERPER_API_KEY=your_serper_api_key_here
   ```

## Usage

1. **Start the Application:**
   Run the Streamlit web interface using the following command:
   ```bash
   streamlit run src/sqe_project/main.py
   ```
   *(Alternatively, if installed as a package via `pip install -e .`, you can use the command `sqe-project` or `chatbot` depending on your entry points).*

2. **Using the Assistant:**
   - **Step 1:** Enter your **Project Title** and initial **Project Requirements** in the text fields.
   - **Step 2:** Click **Take Interview**. The AI will generate 8-12 critical questions regarding missing features based on your inputs.
   - **Step 3:** Answer the questions to provide further context to the agents.
   - **Step 4:** Once the interview is complete, click **Generate Report**.
   - **Step 5:** The CrewAI agents will start processing. Once finished, you can read the comprehensive report on the screen or click **Download Report** to save it as a Markdown file.

## Project Structure
```text
.
├── src/
│   └── sqe_project/
│       ├── main.py           # Streamlit UI, interview logic, and CrewAI initialization
│       ├── agents.py         # Definition of the 4 Project Management Agents
│       ├── tasks.py          # Definition of the Tasks assigned to the agents
│       ├── agent_output.md   # Auto-generated project reports
│       └── __init__.py
├── .env                      # Environment variables (API Keys)
├── pyproject.toml            # Project metadata and build configuration
└── README.md                 # Project documentation
```
