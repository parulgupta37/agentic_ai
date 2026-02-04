AI Email Classification & Response Agent

A LangGraph‑powered workflow that reads incoming emails, classifies urgency and topic, and generates a professional response using an LLM (Ollama + Qwen model).

This project demonstrates how to build a multi‑step AI agent using LangGraph, TypedDict state, and ChatOllama, with a clear flow:

Classify urgency

Classify topic

Route complex issues to a human

Generate a helpful email response

Visualize the workflow as a Mermaid diagram

🚀 Features

🔍 Email Understanding

The agent analyzes the email content to determine:

Urgency (High / Medium / Low)

Category (Bug, Technical, Billing, Feature Request, Password, Other)

Whether the issue is too complex and needs human escalation

🧠 LLM‑Generated Responses

Using the Qwen model via Ollama, the agent writes:

Polite

Professional

Context‑aware

Helpful

email replies tailored to the sender’s issue.

🕸️ LangGraph Workflow

The entire logic is built as a graph:

START → read_email_urgency → read_email_topic → (human_response OR response_for_email) → END

A Mermaid PNG diagram is automatically generated.

📦 Requirements

Make sure you have:

Python 3.10+

A virtual environment (recommended)

Ollama installed locally

The Qwen model pulled:

ollama pull qwen3:0.6b

Install Python dependencies:

pip install langchain-ollama langgraph typing_extensions

🧩 Project Structure

project/
│
├── email_agent.py             # Main script
├── email_graph_ai.png         # Auto‑generated workflow diagram
└── README.md                  # This file

🧠 How It Works

1. State Definition

A TypedDict defines all fields the graph will read or write:

email content

sender

urgency

category

generated response

manual escalation flag

timestamp

2. Nodes

Each node updates the state:

Node Name

Purpose

read_email_urgency

Detect urgency level

read_email_topic

Classify topic

check_if_critical

Decide if human escalation is needed

human_response

Mark issue for manual handling

response_for_email

Generate final email

3. Graph Execution

The graph runs step‑by‑step and returns the final state with the generated email.

▶️ Running the Agent

Run the script:

python email_agent.py

You’ll see:

The full state returned by the graph

The urgency classification

The topic classification

Whether it was escalated

The generated email response

🖼️ Workflow Diagram

The script automatically generates:

email_graph_ai.png

This PNG shows the full LangGraph workflow using Mermaid.

🛠️ Example Input

initial_state = {
    "email_sender": "Parul",
    "email_cntnt": "I need help resetting my password urgently.",
    "email_classify_urg": "",
    "email_classify_category": "",
    "response_email": "",
    "manual_help": "",
    "date_time": "2026-02-03"
}

📤 Example Output

Urgency: High

Category: Password / Access

Escalation: No

Generated Email:A polite, helpful response with steps to reset the password.




or a version with architecture diagrams included

Just tell me what style you want.
