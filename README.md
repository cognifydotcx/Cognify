
# Cognify: AI Agents from Scratch

![Cognify Cover](https://pbs.twimg.com/profile_banners/1881392041885851648/1737393982/1500x500)

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Agents](#agents)
  - [Main Agents](#main-agents)
  - [Validator Agents](#validator-agents)
- [Logging](#logging)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

## Overview

**Cognify** is a Python-based multi-agent system designed to demonstrate how AI agents can perform specialized tasks collaboratively without relying on orchestration frameworks like Crew AI, AutoGen, or LangGraph. Built for educational purposes, Cognify helps beginners and developers understand the fundamentals of multi-agent architecture and operations.

Leveraging OpenAI's **GPT-4o** model and a user-friendly **Streamlit interface**, Cognify features agents for:

- Summarizing medical texts.
- Writing research articles.
- Sanitizing medical data (removing Protected Health Information, or PHI).

Each task agent is paired with a validator agent to ensure quality and accuracy, showcasing a lightweight yet robust framework for multi-agent systems.

Official Website: [Cognify.cx](https://www.cognify.cx)  
Follow Us: [Twitter](https://x.com/cognifydotcx)

---

## Features

- **Medical Text Summarization**: Generate concise summaries from lengthy medical documents.
- **Research Article Writing**: Create well-structured research articles based on topics or outlines.
- **PHI Data Sanitization**: Remove sensitive information from medical datasets.
- **Quality Assurance**: Each primary agent is complemented by a validator agent for output validation.
- **Streamlit Interface**: An intuitive, web-based frontend for easy interaction.
- **Comprehensive Logging**: Detailed logs for monitoring, debugging, and tracking system performance.

---

## Architecture

```
+-------------------+
|       User        |
+---------+---------+
          |
          | Interacts via
          v
+---------+---------+
|    Streamlit App  |
+---------+---------+
          |
          | Sends task requests to
          v
+---------+---------+
|  Agent Manager    |
+---------+---------+
          |
          +---------------------------------------------+
          |                      |                      |
          v                      v                      v
+---------+---------+  +---------+---------+  +---------+---------+
|  Summarize Agent  |  |  Write Article    |  |  Sanitize Data    |
|  (Generates summary)| |  (Generates draft)| |  (Removes PHI)    |
+---------+---------+  +---------+---------+  +---------+---------+
          |                      |                      |
          v                      v                      v
+---------+---------+  +---------+---------+  +---------+---------+
|Summarize Validator|  | Refiner Agent      |  |Sanitize Validator |
|      Agent        |  |  (Enhances draft)  |  |      Agent        |
+---------+---------+  +---------+----------+ +----------+--------+
          |                      |                      |
          |                      |                      |
          +-----------+----------+-----------+----------+
                      |                      |
                      v                      v
                +-----+-------+        +-----+-------+
                |   Logger    |        |   Logger    |
                +-------------+        +-------------+
```

### Components Breakdown

1. **User**
   - Interacts with the system through the Streamlit-based web app.
   - Selects tasks and provides input data.

2. **Streamlit App**
   - Frontend interface to interact with agents.
   - Sends user requests to the **Agent Manager**.
   - Displays results and validator feedback.

3. **Agent Manager**
   - Central controller for delegating tasks to agents and validators.

4. **Main Agents**
   - **Summarize Agent**: Produces summaries of medical texts.
   - **Write Article Agent**: Creates drafts of research articles.
   - **Sanitize Data Agent**: Removes PHI from datasets.

5. **Validator Agents**
   - **Summarize Validator**: Validates the summaries.
   - **Refiner Validator**: Enhances article drafts.
   - **Sanitize Validator**: Ensures effective PHI removal.

6. **Logger**
   - Tracks system activity, errors, and debugging data.

---

## Installation

### Prerequisites

- **Python 3.8 or higher**: [Download Python](https://www.python.org/downloads/)
- **OpenAI API Key**: [Get your API Key](https://platform.openai.com/signup)

### Steps

1. **Clone the Repository**

   ```bash
   git clone https://github.com/cognifydotcx/Cognify.git
   cd Cognify
   ```

2. **Create a Virtual Environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Set Up Environment Variables**

   Create a `.env` file:

   ```dotenv
   OPENAI_API_KEY=your-api-key-here
   ```

---

## Usage

1. **Activate the Virtual Environment**

   ```bash
   source venv/bin/activate
   ```

2. **Run the App**

   ```bash
   streamlit run app.py
   ```

3. **Access the App**

   Open `http://localhost:8501` in your browser.

4. **Select and Perform Tasks**

   - Input data for summarization, article writing, or PHI sanitization.
   - View and download results.

---

## Agents

### Main Agents

- **Summarize Agent**
  - **Input**: Medical text.
  - **Output**: Concise summaries.
- **Write Article Agent**
  - **Input**: Topic and optional outline.
  - **Output**: Research article draft.
- **Sanitize Data Agent**
  - **Input**: Raw medical data.
  - **Output**: Sanitized dataset without PHI.

### Validator Agents

- **Summarize Validator**: Evaluates summaries for completeness and accuracy.
- **Refiner Validator**: Refines research articles for quality improvements.
- **Sanitize Validator**: Validates the PHI removal process.

---

## Logging

- **Location**: Logs are stored in the `logs/` directory.
- **Files**:
  - `multi_agent_system.log`: Contains all activity and error logs.
- **Customization**: Adjust logging in `utils/logger.py`.

---

## Contributing

1. **Fork the Repository**
2. **Create a Branch**

   ```bash
   git checkout -b feature/YourFeature
   ```

3. **Submit a Pull Request**

We welcome bug fixes, feature requests, and suggestions!

---

## License

This project is licensed under the [MIT License](LICENSE).

---

## Acknowledgements

- [OpenAI](https://openai.com/) for GPT-4 API.
- [Streamlit](https://streamlit.io/) for the web app framework.
- [Loguru](https://github.com/Delgan/loguru) for logging.

Follow us at [Cognify.cx](https://www.cognify.cx) or on [Twitter](https://x.com/cognifydotcx) for updates.
