# ✈️ TripMate AI | Multi-Agent Travel Planner

**Plan smarter journeys with AI-powered travel research and personalized itineraries.**

TripMate AI is a multi-agent travel planning application built with Python, LangGraph, LangChain, and FastAPI. It transforms natural-language travel requests into organized travel plans by coordinating specialized AI agents for travel research, accommodation discovery, and itinerary generation.

## 🌍 Overview

Planning a trip often involves switching between flight-search websites, hotel platforms, and itinerary tools. TripMate AI brings these tasks into a single web application, using AI agents to help users explore travel options and create personalized plans.

## ✨ Key Features

* 🤖 **Multi-Agent Architecture** — Coordinates specialized agents through a LangGraph workflow.
* 🗺️ **Personalized Itineraries** — Generates structured, day-by-day travel plans based on user requests.
* 🏨 **Hotel Research** — Uses Tavily-powered web search to find accommodation ideas.
* ✈️ **Flight Research** — Includes an AviationStack integration for flight-related information when configured and available.
* 🧠 **LLM-Powered Planning** — Uses Groq-hosted language models to process requests and generate travel recommendations.
* 🌐 **Interactive Web Interface** — Provides a simple frontend connected to a FastAPI backend.
* 💾 **Conversation Persistence** — Uses PostgreSQL-backed checkpointing to preserve workflow state.

## 🛠️ Tech Stack

| Category                | Technologies                         |
| ----------------------- | ------------------------------------ |
| Language                | Python                               |
| Backend                 | FastAPI                              |
| Agent Orchestration     | LangGraph, LangChain                 |
| Language Model          | Groq                                 |
| Search Integration      | Tavily API                           |
| Flight Data Integration | AviationStack API                    |
| Database                | PostgreSQL                           |
| Frontend                | HTML, CSS, JavaScript                |
| Deployment              | Render and Neon PostgreSQL (planned) |

## 🏗️ Architecture

```text
User Travel Request
        |
        v
 FastAPI Web Application
        |
        v
 LangGraph Workflow
        |
        +------------------+
        |                  |
        v                  v
   Flight Research    Hotel Research
        |                  |
        +--------+---------+
                 |
                 v
       Itinerary Planning
                 |
                 v
        Final AI Response
                 |
                 v
        Personalized Plan
```

*The diagram illustrates the intended workflow; the exact execution path depends on the implementation and API availability.*

## 📁 Project Structure

```text
TripMate-AI/
├── app/
│   └── app.py             # FastAPI application entry point
├── tools/
│   ├── __init__.py
│   ├── flight_tool.py     # Flight research integration
│   └── tavily_tool.py     # Web search integration
├── static/
│   ├── script.js          # Frontend interactions
│   └── style.css          # UI styling
├── templates/
│   └── index.html         # Web interface
├── backend.py             # Multi-agent travel workflow
├── requirements.txt       # Python dependencies
├── Dockerfile             # Container configuration
├── .dockerignore
├── .gitignore
└── README.md
```

## ⚙️ Getting Started

### Prerequisites

* Python 3.10 or newer
* A PostgreSQL database
* API credentials for Groq and Tavily
* AviationStack credentials if using its flight-data integration

### 1. Clone the repository

```bash
git clone https://github.com/Sushmitha005/Multi-Agent-AI-Travel-Planner-.git
cd Multi-Agent-AI-Travel-Planner-
```

### 2. Create and activate a virtual environment

**Windows PowerShell**

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
py -m pip install -r requirements.txt
```

### 4. Configure environment variables

Create a `.env` file in the project root. Add your own credentials:

```env
DATABASE_URL=your_postgresql_connection_string
GROQ_API_KEY=your_groq_api_key
TAVILY_API_KEY=your_tavily_api_key
AVIATIONSTACK_API_KEY=your_aviationstack_api_key
DEFAULT_ORIGIN_IATA=DAC
```

Keep your `.env` file private. Never commit API keys or database credentials to GitHub.

### 5. Run the application

From the project root, run:

```powershell
py -m uvicorn app.app:app --reload --host 127.0.0.1 --port 8000
```

Open your browser at:

**http://127.0.0.1:8000/**

## 🔌 API Endpoint

### `POST /api/travel`

Submit a natural-language travel request to generate a travel plan.

Example request body:

```json
{
  "message": "Plan a 3-day trip to Tokyo with a budget of $1200"
}
```

The available response fields and behavior depend on the application's implementation and configured integrations.

## 🔐 Environment Variables

| Variable                | Purpose                               |
| ----------------------- | ------------------------------------- |
| `DATABASE_URL`          | PostgreSQL connection string          |
| `GROQ_API_KEY`          | Access to Groq-hosted language models |
| `TAVILY_API_KEY`        | Web search for travel research        |
| `AVIATIONSTACK_API_KEY` | Flight-data integration               |
| `DEFAULT_ORIGIN_IATA`   | Default departure airport code        |

## 🚀 Future Improvements

* Deploy the application for public access.
* Improve flight-data availability and error handling.
* Add more destination and accommodation filters.
* Enhance itinerary customization and budget breakdowns.
* Expand automated testing and monitoring.

## 🤝 Contributing

Contributions, ideas, and bug reports are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Make your changes and test them.
4. Submit a pull request.

## 📄 License

See the [LICENSE](LICENSE) file for licensing details.

---

**Built with Python, LangGraph, LangChain, and FastAPI.**
