# ✈️ TripMate — Multi-Agent AI Travel Planning System

TripMate is an **AI-powered multi-agent travel planning system** that helps users create personalized travel plans using multiple specialized AI agents.

The system uses **LangGraph for agent orchestration** and **Model Context Protocol (MCP)** to connect AI agents with external tools such as weather services and travel-related utilities.

---

## 🚀 Features

* 🤖 **Multi-Agent Architecture**
* 🔗 **LangGraph** for agent orchestration
* 🔌 **Model Context Protocol (MCP)** for external tool integration
* 🌤️ **Custom Weather MCP Server**
* 💬 Natural-language travel planning
* 🗺️ Destination and travel research
* 📅 Itinerary generation
* 🔄 Stateful agent workflow
* 🌐 FastAPI backend
* 🎨 Web-based frontend
* 🔐 Environment-variable based API configuration

---

# 🏗️ System Architecture

TripMate uses a **multi-agent architecture** where specialized agents handle different travel-related tasks.

```text
                         ┌─────────────────────┐
                         │       User          │
                         │  Travel Request     │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │   Travel Planning  │
                         │      Workflow      │
                         └──────────┬──────────┘
                                    │
                    ┌───────────────┼────────────────┐
                    │               │                │
                    ▼               ▼                ▼
             ┌────────────┐  ┌────────────┐  ┌──────────────┐
             │  Weather   │  │   Travel   │  │  Research /  │
             │   Agent    │  │   Agent    │  │ Other Agents │
             └─────┬──────┘  └────────────┘  └──────────────┘
                   │
                   ▼
             ┌──────────────┐
             │   MCP Client │
             └──────┬───────┘
                    │
                    ▼
             ┌────────────────────┐
             │ Custom Weather MCP │
             │      Server        │
             └─────────┬──────────┘
                       │
                       ▼
                  Weather API
                       │
                       ▼
             ┌─────────────────────┐
             │ Final Travel Plan   │
             │ + Recommendations   │
             └─────────────────────┘
```

---

# 🧠 Multi-Agent Workflow

TripMate divides travel planning into specialized tasks.

### 1. User

The user provides a natural-language travel request.

Example:

```text
Plan a 5-day trip to Goa for 2 people.
I want beaches, sightseeing and a budget-friendly itinerary.
```

---

### 2. Specialized Agents

Different agents can handle different parts of the travel-planning process.

For example:

```text
Weather Agent
    ↓
Weather information

Travel Agent
    ↓
Travel planning and recommendations

Research Agent
    ↓
Destination information

Itinerary Agent
    ↓
Day-by-day travel plan
```

The agents work together through the application workflow to generate the final travel plan.

---

# 🔌 Model Context Protocol (MCP)

TripMate uses **Model Context Protocol (MCP)** to connect AI agents with external tools.

MCP provides a standardized interface between the AI application and external tools.

In this project, a custom weather MCP server exposes weather functionality to the application.

```text
AI Agent
   │
   ▼
MCP Client
   │
   ▼
MCP Protocol
   │
   ▼
Weather MCP Server
   │
   ▼
Weather API
```

This architecture makes it easier to add additional tools without tightly coupling external API logic to the agents.

Possible future MCP tools include:

* ✈️ Flight search
* 🏨 Hotel search
* 🌤️ Weather
* 💱 Currency conversion
* 🗺️ Maps
* 🍴 Restaurant search
* 🎟️ Attractions
* 🚆 Train information

---

# 🌤️ Custom Weather MCP Server

The repository contains:

```text
custom_weather_mcp_server.py
```

This server exposes weather functionality as an MCP tool.

The application can request weather information through MCP instead of directly embedding weather API logic inside the agent.

Example flow:

```text
Travel Agent
     ↓
MCP Client
     ↓
Weather MCP Server
     ↓
OpenWeather API
     ↓
Weather Result
     ↓
Travel Agent
```

---

# 🧩 Project Structure

```text
TripMate-Mulit-Agent-System/
│
├── app.py
├── backend.py
├── mcp_client.py
├── custom_weather_mcp_server.py
├── mcp_client_test.py
├── test.py
│
├── requirements.txt
├── .env.example
├── .gitignore
│
├── templates/
│   └── ...
│
├── static/
│   └── ...
│
├── tools/
│   └── ...
│
└── README.md
```

### `app.py`

Main application entry point.

Responsible for:

* Starting the FastAPI application
* Defining API routes
* Connecting the frontend with the backend

### `backend.py`

Contains the core travel-agent logic.

Responsibilities include:

* Agent workflow
* LangGraph execution
* Travel planning
* State management
* Agent communication

### `mcp_client.py`

Handles communication between the application and MCP servers.

Responsibilities include:

* Connecting to MCP servers
* Discovering available tools
* Calling MCP tools
* Returning tool results to agents

### `custom_weather_mcp_server.py`

Custom MCP server that exposes weather functionality.

### `mcp_client_test.py`

Used to test MCP client functionality and MCP tool communication.

### `test.py`

Used for testing the travel-agent workflow.

### `templates/`

Contains HTML templates used by the web interface.

### `static/`

Contains frontend assets such as:

* CSS
* JavaScript
* Images

### `tools/`

Contains supporting tools used by the application.

---

# 🛠️ Technology Stack

| Category               | Technology              |
| ---------------------- | ----------------------- |
| Language               | Python                  |
| Backend                | FastAPI                 |
| Agent Framework        | LangGraph               |
| LLM Framework          | LangChain               |
| AI Model               | Gemini / LLM Provider   |
| Tool Protocol          | MCP                     |
| Weather                | OpenWeather API         |
| Frontend               | HTML / CSS / JavaScript |
| Environment Management | python-dotenv           |
| HTTP Client            | Requests                |
| Async Runtime          | asyncio                 |

---

# 🔄 End-to-End Workflow

```text
1. User enters travel request
            ↓
2. FastAPI receives request
            ↓
3. Travel planning workflow starts
            ↓
4. Required agents process the request
            ↓
5. Agents use MCP tools when required
            ↓
6. MCP Client communicates with MCP Server
            ↓
7. External APIs provide required information
            ↓
8. Results are returned to the agents
            ↓
9. Agents generate the travel plan
            ↓
10. Final travel plan is returned to the user
```

---

# ⚙️ Installation

## 1. Clone the repository

```bash
git clone https://github.com/manojchebrolu/TripMate-Mulit-Agent-System.git
```

```bash
cd TripMate-Mulit-Agent-System
```

---

## 2. Create a virtual environment

### Windows

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
```

```bash
source venv/bin/activate
```

---

## 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

# 🔐 Environment Variables

Create a `.env` file:

```env
GOOGLE_API_KEY=your_google_api_key
OPENWEATHER_API_KEY=your_openweather_api_key
```

Add any other API keys required by your configured agents or tools.

### Important

Never commit the `.env` file to GitHub.

Your `.gitignore` should contain:

```gitignore
.env
venv/
__pycache__/
*.pyc
```

---

# ▶️ Running the Application

Start the FastAPI application:

```bash
python app.py
```

Or using Uvicorn:

```bash
uvicorn app:app --reload
```

The application should be available at:

```text
http://127.0.0.1:8000
```

---

# 🔌 Running the MCP Server

The custom weather MCP server can be started separately:

```bash
python custom_weather_mcp_server.py
```

The MCP client can then communicate with the server and provide its tools to the travel-planning workflow.

---

# 🧪 Testing

Run the MCP client test:

```bash
python mcp_client_test.py
```

Run the application workflow test:

```bash
python test.py
```

---

# 💡 Example Query

```text
Plan a 5-day trip to Hyderabad.

I want:

- Budget-friendly hotels
- Popular tourist attractions
- Local food
- Weather information
- A day-by-day itinerary
```

TripMate processes the request through its multi-agent workflow and generates a consolidated travel plan.

---

# 📈 Why Multi-Agent Architecture?

Travel planning involves multiple types of tasks.

Instead of putting all responsibilities into one agent, TripMate separates tasks into specialized agents.

```text
                    Travel Request
                          │
                          ▼
                 Multi-Agent Workflow
                          │
          ┌───────────────┼───────────────┐
          │               │               │
          ▼               ▼               ▼
      Weather          Travel         Research
       Agent            Agent           Agent
          │               │               │
          └───────────────┼───────────────┘
                          │
                          ▼
                   Itinerary Agent
                          │
                          ▼
                    Final Plan
```

This architecture makes the application easier to:

* Extend
* Debug
* Test
* Maintain
* Add new agents
* Add new MCP tools
* Integrate external APIs

---

# 🔮 Future Enhancements

* ✈️ Flight-search MCP server
* 🏨 Hotel-search MCP server
* 🗺️ Maps MCP server
* 💱 Currency MCP server
* 🍴 Restaurant MCP server
* 🚆 Transportation MCP server
* 💰 Automatic trip-budget calculation
* 📍 Location-based recommendations
* 🧳 AI packing-list agent
* 📄 PDF itinerary generation
* 🔐 Authentication and user accounts
* 🐳 Docker containerization
* 🔄 CI/CD pipeline
* ☁️ Cloud deployment
* 📊 AI workflow observability
* 💾 Persistent conversation memory

---

# 📚 Key Concepts Demonstrated

This project demonstrates practical implementation of:

* Large Language Models (LLMs)
* Generative AI
* AI Agents
* Multi-Agent Systems
* LangChain
* LangGraph
* Model Context Protocol (MCP)
* MCP Client/Server Architecture
* Tool Calling
* FastAPI
* External API Integration
* Stateful AI Workflows
* Async Programming

---

# 👨‍💻 Author

**Manoj Chebrolu**

GitHub:
https://github.com/manojchebrolu

---

# ⭐ Project

If you find this project useful, consider giving it a ⭐ on GitHub.

**TripMate — Intelligent travel planning powered by Multi-Agent AI + LangGraph + MCP.**
