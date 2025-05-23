# 🌞 Solar-Sage: Intelligent Solar Energy Assistant

Solar-Sage is a domain-aware AI assistant designed to support engineers, site operators, and analysts in the solar energy lifecycle — from site planning to QA audits and performance diagnostics. Powered by LLMs and integrated with geospatial pipelines (e.g., point cloud analysis, CAD deviation detection, thermal anomaly classification), it answers questions, explains results, and guides workflows through a conversational interface.

## 🤖 Agentic RAG Chatbot

Solar-Sage has evolved into an **Agentic RAG Chatbot** that not only provides information but can also take actions, make decisions, and interact with external systems. By integrating weather data with RAG systems, it offers solar recommendations, insights, alerts, degradation estimates, and automation workflows. The core agent framework has been implemented, including the Tool Registry, Memory System, Agent Engine, and Weather Tools. See the [Agentic RAG documentation](#agentic-rag-chatbot) for implementation details.

## 🌟 What Can It Do?

### Current Capabilities

- Answer questions about solar panels, installation, and energy
- Provide weather-enhanced solar insights
- Work completely offline on your computer
- Provide accurate information from reliable solar energy sources
- Remember your conversation history
- Switch between light and dark mode for comfortable viewing
- Generate solar production forecasts based on weather data
- Provide maintenance recommendations based on weather conditions
- Identify optimal times for solar production
- Analyze weather impact on solar production

### Upcoming Agentic Capabilities

- Analyze performance data and detect issues
- Schedule alerts and notifications
- Connect with smart home systems and inverter monitoring APIs
- Provide system configuration recommendations
- Implement user authorization for sensitive tools

## 🚀 Quick Start Guide (For Everyone)

### Prerequisites

Before you begin, make sure you have:

1. **Python 3.9+** installed on your computer

   - [Download Python](https://www.python.org/downloads/) if you don't have it

2. **Git** to download the project

   - [Download Git](https://git-scm.com/downloads) if you don't have it

3. **Node.js 16+** for the frontend
   - [Download Node.js](https://nodejs.org/) if you don't have it

### Step 1: Download the Project

Open your terminal (Command Prompt on Windows) and run:

```bash
git clone https://github.com/alphapebble/solar-sage.git
cd solar-sage
```

### Step 2: Set Up the Backend Environment

Create a virtual environment and install the required packages:

```bash
# Create a virtual environment
python -m venv venv

# Activate the virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install required packages
pip install -r requirements.txt
```

### Step 3: Set Up the Frontend Environment

```bash
# Navigate to the frontend directory
cd frontend

# Install dependencies
npm install

# Return to the project root
cd ..
```

### Step 4: Start the Application

You can run the application using our convenient startup script:

```bash
# Start all components (API, Next.js, Ollama)
./solar_sage.sh start

# Or start components individually
./solar_sage.sh api start 8000    # Start FastAPI server on port 8000
./solar_sage.sh next start 3000   # Start Next.js on port 3000
./solar_sage.sh ui start 7860     # Start Gradio UI on port 7860
./solar_sage.sh ollama start      # Start Ollama

# Check status of all components
./solar_sage.sh status

# Stop all components
./solar_sage.sh stop

# Get help on all available commands
./solar_sage.sh help
```

For a complete reference of all available shell commands, see the [Shell Commands Documentation](docs/shell_commands.md).

Keep the terminal windows open while using the application.

> **Note:** All scripts automatically set up the Python path and environment variables for you. If you need to customize settings, you can create a `.env` file in the project root.

### Alternative: Start Components Manually

If you prefer to start the components manually:

```bash
# Start the FastAPI backend (in one terminal)
# First, add src to your Python path
export PYTHONPATH=$PYTHONPATH:$(pwd)/src  # Linux/macOS
# OR
set PYTHONPATH=%PYTHONPATH%;%cd%\src     # Windows

# Run the API server
python -m cli.main server

# Start the Next.js frontend (in another terminal)
cd frontend
npm run dev
```

### Step 5: Access the UIs

Once all components are running, you can access the UIs in your web browser:

#### Next.js Frontend (Primary UI)

- **Main UI**: http://localhost:3000
- **Chat Interface**: http://localhost:3000/chat
- **Solar Forecast**: http://localhost:3000/solar-forecast
- **Evaluation Dashboard**: http://localhost:3000/evaluation

#### Gradio UI (Alternative)

- **Main UI**: http://localhost:7860
- **Evaluation Dashboard**: http://localhost:7860/?view=evaluation

#### API Documentation

- **Swagger UI**: http://localhost:8000/docs
- **ReDoc**: http://localhost:8000/redoc

### Step 6: Use the Application

#### Next.js UI (Primary)

1. Open your web browser and go to http://localhost:3000
2. Navigate to the Chat page to ask questions about solar energy
3. Use the Solar Forecast page to generate solar production forecasts
4. Explore the Evaluation page to view system performance metrics
5. Explore the About page to learn more about the system

#### Gradio UI (Alternative)

1. Open your web browser and go to http://localhost:7860
2. Use the chat interface to ask questions about solar energy
3. Adjust system settings in the sidebar
4. Access the evaluation dashboard by clicking the "Evaluation" link

## 🔍 Using Advanced Features

### Location Settings

In the Chat and Solar Forecast pages, you can customize your location settings:

- **Latitude and Longitude**: Set your geographical coordinates
- **Location ID**: Provide a name for your location
- **System Capacity**: Specify the size of your solar system in kW
- **Electricity Rate**: Set your electricity rate in $/kWh
- **Feed-in Tariff**: Set your feed-in tariff in $/kWh

### Solar Forecasting

The Solar Forecast page provides detailed information about your solar system's performance:

- **Daily Forecast**: View expected production and demand for each day
- **Hourly Forecast**: See hourly production and demand patterns
- **Cost Savings**: Analyze financial benefits and ROI
- **Insights**: Get actionable insights based on the forecast data

### Chat Interface

The Chat page allows you to interact with the AI assistant:

- **Natural Language**: Ask questions in plain English
- **Context-Aware**: The assistant remembers your conversation history
- **Weather-Enhanced**: Get location-specific insights based on weather data
- **Solar-Enhanced**: Receive solar production forecasts and recommendations

## 🛠️ Troubleshooting

### Common Issues and Solutions

1. **"Connection Error" when asking a question**

   - Make sure the backend server is running (Step 3)
   - Check that you're using the correct URL in your browser

2. **"Module not found" errors**

   - Make sure you've activated the virtual environment
   - Try reinstalling the requirements: `pip install -r requirements.txt`

3. **Slow responses**

   - The AI model needs time to think, especially on the first question
   - Responses should get faster after the first few questions

4. **Application crashes or freezes**
   - Restart both the backend server and the UI
   - Make sure your computer meets the minimum requirements

### Getting Help

If you encounter problems not covered here:

1. Check the [GitHub Issues](https://github.com/alphapebble/solar-sage/issues) page
2. Create a new issue with details about your problem

## 📚 For Developers

If you're a developer interested in the technical details or want to contribute to the project, check out the [Developer Documentation](docs/development/DEVELOPERS.md).

### Setting Up Your Development Environment

#### Marking the Source Root

The project uses a `src` directory as the source root. You should mark this directory as a source root in your IDE:

**PyCharm:**

1. Right-click on the `src` directory
2. Select "Mark Directory as" > "Sources Root"

**VS Code:**

1. Add this to your `.vscode/settings.json`:
   ```json
   {
     "python.analysis.extraPaths": ["./src"]
   }
   ```
2. If using a virtual environment, make sure to select it as your Python interpreter

**Command Line:**
If you're not using an IDE, you can add the `src` directory to your Python path:

```bash
# Linux/macOS
export PYTHONPATH=$PYTHONPATH:$(pwd)/src

# Windows (Command Prompt)
set PYTHONPATH=%PYTHONPATH%;%cd%\src

# Windows (PowerShell)
$env:PYTHONPATH += ";$(Get-Location)\src"
```

### Agentic RAG Chatbot

Solar Sage has been extended with agentic capabilities to provide not just information but also take actions, make decisions, and interact with external systems. The core agent framework has been implemented, including the Tool Registry, Memory System, Agent Engine, and Weather Tools.

#### Documentation

Comprehensive documentation is available in the `docs/` directory, organized by category:

##### Architecture Documentation

- [Agentic RAG Chatbot Architecture](docs/architecture/agentic_rag_chatbot.md) - Complete architecture documentation including dual-agent implementation
- [UI Architecture](docs/architecture/ui_architecture.md) - Overview of the dual UI architecture
  - [Next.js Frontend Architecture](docs/architecture/nextjs_frontend.md) - Detailed documentation for the Next.js frontend
  - [Gradio UI Architecture](docs/architecture/gradio_ui.md) - Detailed documentation for the Gradio UI
- [API Architecture](docs/architecture/api_architecture.md) - Overview of the API architecture

##### Guides

- [Quick Start Guide](docs/guides/agentic_quickstart.md) - Get started quickly with the agentic chatbot
- [Testing Guide](docs/guides/testing_guide.md) - Instructions for running tests and evaluations

##### Reference Documentation

- [Shell Commands Reference](docs/reference/shell_commands.md) - Comprehensive reference for all shell commands
- [Implementation Reference](docs/reference/agent_implementation_guide.md) - Reference guide for the implemented components

##### Development Documentation

- [Project Roadmap](docs/development/agentic_rag_roadmap.md) - Implementation timeline and phases
- [Implementation Status](docs/development/implementation_status.md) - Current status and next steps
- [Agentic System Vision](docs/development/agentic_vision.md) - Future vision for true agentic capabilities
- [RAG Improvements Plan](docs/development/rag_improvements_plan.md) - Advanced RAG techniques for energy sector applications

### Project Structure

The codebase follows a modular structure with a clean separation of concerns. The project is organized into several key components:

- **src/** - Backend source code (marked as source root)

  - **agents/** - Agent components for autonomous reasoning
    - **tools/** - Tool implementations for agent actions
    - **integrations/** - Integration with external systems
    - **types/** - Specialized agent types
    - **tool_registry.py** - Tool registration and execution
    - **memory_system.py** - Conversation history and preferences
    - **agent_engine.py** - Core agent logic
    - **initialize.py** - Agent initialization
  - **app/** - FastAPI server and API endpoints
  - **core/** - Core utilities and configuration
  - **ingestion/** - Document processing pipeline
  - **llm/** - LLM integration with various backends
  - **rag/** - Retrieval-Augmented Generation system
  - **retrieval/** - Vector database retrieval

- **ui/** - Gradio UI components (alternative UI)

  - **api/** - API client for backend communication
  - **components/** - UI components and views
  - **utils/** - Utility functions
  - **templates/** - HTML/CSS/JS templates

- **frontend/** - Next.js frontend (primary UI)

  - **src/** - React components and pages
    - **api/** - API client and types
    - **components/** - React components
    - **pages/** - Next.js pages
  - **public/** - Static assets
  - **styles/** - CSS and styling

For a detailed breakdown of the project structure, please see the [Developer Documentation](docs/development/DEVELOPERS.md).

### RAG System

Solar Sage uses a Retrieval Augmented Generation (RAG) system to provide accurate, up-to-date information about solar energy. The RAG system:

1. Retrieves relevant information from a knowledge base
2. Augments the LLM's context with this information
3. Generates accurate, contextual responses

The system includes:

- **Vector Database**: LanceDB for efficient similarity search
- **Embedding Model**: Sentence transformers for document and query embedding
- **Chunking Strategy**: Optimized document splitting for better retrieval
- **Weather Enhancement**: Integration of real-time weather data for location-specific insights

#### Planned RAG Improvements

We're implementing advanced RAG techniques based on the [langchain-ai/rag-from-scratch](https://github.com/langchain-ai/rag-from-scratch) repository to enhance our system for energy sector applications:

- **Query Expansion**: Generate multiple query variations to improve recall
- **Reranking**: Apply a second-stage ranking to improve precision
- **Hybrid Search**: Combine semantic and keyword search for better results
- **FLARE**: Implement iterative retrieval for complex energy sector queries

See the [RAG Improvements Plan](docs/rag_improvements_plan.md) for a detailed roadmap and energy sector applications.

### Solar Energy Forecasting

Solar Sage includes a comprehensive solar energy forecasting system that provides:

1. **Solar Production Forecasts**: Predict energy production based on weather and system specifications
2. **Energy Demand Forecasts**: Analyze historical usage patterns to predict future demand
3. **Cost Savings Analysis**: Calculate financial benefits based on electricity rates and feed-in tariffs

The forecasting system integrates:

- **Weather Data**: Cloud cover, temperature, and precipitation forecasts
- **Solar Irradiance Models**: Calculate expected solar radiation based on location and time
- **Historical Usage Patterns**: Analyze past energy consumption to predict future needs
- **Financial Analysis**: Calculate ROI and payback periods for solar installations
- **Semantic Metric Layer**: All calculations use a [semantic layer of metrics and formulas](docs/architecture/semantic_metric_layer.md) for transparency and consistency

#### Using the Solar Forecasting API

```bash
# Get a solar energy forecast
curl -X POST "http://localhost:8000/solar/forecast" \
  -H "Content-Type: application/json" \
  -d '{
    "latitude": 37.7749,
    "longitude": -122.4194,
    "location_id": "home",
    "system_capacity_kw": 5.0
  }'

# Get a cost savings analysis
curl -X POST "http://localhost:8000/solar/cost-savings" \
  -H "Content-Type: application/json" \
  -d '{
    "latitude": 37.7749,
    "longitude": -122.4194,
    "location_id": "home",
    "system_capacity_kw": 5.0,
    "electricity_rate": 0.15,
    "feed_in_tariff": 0.08
  }'

# Get a solar-enhanced RAG response
curl -X POST "http://localhost:8000/solar/rag" \
  -H "Content-Type: application/json" \
  -d '{
    "query": "How much money will I save with a 5kW solar system?",
    "latitude": 37.7749,
    "longitude": -122.4194,
    "location_id": "home",
    "system_capacity_kw": 5.0,
    "electricity_rate": 0.15,
    "feed_in_tariff": 0.08
  }'
```

The Solar Forecasting UI provides an interactive interface for exploring forecasts and cost savings.

### Command-Line Interface

Solar Sage provides a command-line interface (CLI) for common tasks:

```bash
# Run the API server
python -m cli.main server [--host HOST] [--port PORT]

# Run the UI
python -m cli.main ui [--port PORT]

# Ingest a document
python -m cli.main ingest SOURCE [--db-path DB_PATH] [--table TABLE] [--model MODEL] [--strategy STRATEGY]

# List ingested documents
python -m cli.main list [--db-path DB_PATH] [--table TABLE]
```

For help on any command:

```bash
python -m cli.main --help
python -m cli.main COMMAND --help
```

> **Note:** The CLI commands assume that you have added the `src` directory to your Python path or marked it as a source root in your IDE.

### Configuration System

Solar Sage uses a flexible configuration system that supports:

1. **Environment Variables**: Set variables with the `SOLAR_SAGE_` prefix
2. **Configuration Files**: Environment-specific settings in `config/environments/`
3. **Default Values**: Fallback values defined in `config/default.py`
4. **Formula Definitions**: Mathematical formulas and constants defined in `config/formulas.yaml`

To configure the application:

1. Copy `.env.example` to `.env` and customize settings:

   ```bash
   cp .env.example .env
   ```

2. Edit the `.env` file with your preferred settings:

   ```
   SOLAR_SAGE_ENV=development
   SOLAR_SAGE_LOG_LEVEL=INFO
   SOLAR_SAGE_API_HOST=0.0.0.0
   SOLAR_SAGE_API_PORT=8000
   SOLAR_SAGE_UI_PORT=8502
   SOLAR_SAGE_LLM_PROVIDER=ollama
   SOLAR_SAGE_LLM_MODEL=mistral
   ```

3. Access configuration in code:

   ```python
   from core.config import get_config

   # Get a configuration value with a default fallback
   api_port = get_config("api_port", 8000)
   ```

For information about the semantic metric layer used for calculations, see the [Semantic Metric Layer Documentation](docs/architecture/semantic_metric_layer.md).

### Running with Different Models

You can use different AI models by setting the appropriate environment variables:

```bash
# Using Mistral model (with src in Python path)
SOLAR_SAGE_LLM_PROVIDER=ollama SOLAR_SAGE_LLM_MODEL=mistral PYTHONPATH=$PYTHONPATH:$(pwd)/src python -m cli.main server

# Using Llama model (with src in Python path)
SOLAR_SAGE_LLM_PROVIDER=ollama SOLAR_SAGE_LLM_MODEL=llama PYTHONPATH=$PYTHONPATH:$(pwd)/src python -m cli.main server
```

Or by editing your `.env` file:

```
SOLAR_SAGE_LLM_PROVIDER=ollama
SOLAR_SAGE_LLM_MODEL=mistral
```

### Docker Deployment

You can deploy Solar Sage using Docker:

```bash
# Build and run with Docker Compose
docker-compose -f deployment/docker/docker-compose.yml up -d

# Or use the deployment script
bash deployment/scripts/deploy.sh
```

> **Note:** The Docker Compose file is located in the `deployment/docker/` directory. There is no Docker Compose file in the root directory.

The Docker setup includes:

- API server container
- UI container
- Ollama container for local LLM support
- Shared volume for data persistence

### Testing

Solar Sage includes a comprehensive test suite and evaluation system:

- **Unit Tests**: Test individual components and functions
- **RAG Evaluation**: Measure the quality of responses using multiple metrics
- **AI Testing**: Planned integration with Giskard for specialized AI testing

For detailed instructions on running tests and evaluations, see the [Testing Guide](docs/guides/testing_guide.md).

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Built with [Next.js](https://nextjs.org/) and [Gradio](https://gradio.app/) for the user interfaces
- Powered by [Mistral AI](https://mistral.ai/) models
- Uses [LanceDB](https://lancedb.github.io/lancedb/) for knowledge retrieval
