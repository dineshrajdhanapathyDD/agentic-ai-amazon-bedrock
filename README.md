# Agentic AI Workshop - Weather Assistant Agent

![Weather Agent Demo](../images/Screenshot%202026-03-01%20003014.png)

## Overview

This project demonstrates the fundamental principles of **Agentic AI** through a practical weather assistant agent built using Amazon Bedrock's Claude 4.5 Sonnet and the National Weather Service API. The agent showcases how AI can think, plan, and act autonomously to solve real-world problems.

## What Makes This "Agentic"?

Our weather assistant exhibits the three key characteristics of agentic AI:

### 🤖 Autonomy
- **Location Intelligence**: Automatically interprets location descriptions and converts them to coordinates
- **API URL Construction**: Dynamically generates the correct NWS Points API URLs based on location analysis
- **Data Processing**: Decides what weather information is most relevant
- **Error Recovery**: Handles failures without human intervention

### ⚡ Reactivity
- **Flexible Input**: Adapts to city names, ZIP codes, coordinates, and descriptive locations
- **API Responses**: Processes varying data structures from NWS APIs
- **Network Issues**: Handles timeouts and connection problems
- **Data Quality**: Works with incomplete or inconsistent weather information

### 🎯 Proactivity
- **Intelligent Planning**: Generates complete API strategies from minimal input
- **Sequential Execution**: Takes concrete actions by calling Points API first, then Forecast API
- **Analysis**: Proactively identifies the most important weather insights
- **Communication**: Presents results in user-friendly formats

## Architecture

![Architecture Flow](../images/Screenshot%202026-02-28%20234629.png)

The agent follows a 6-step workflow:

1. **User Input** → Location name or description
2. **AI Planning** → Claude analyzes location and generates API calls
3. **Points API** → Get forecast office and grid coordinates
4. **Forecast API** → Retrieve detailed weather data
5. **AI Processing** → Convert raw JSON into readable summary
6. **Display Results** → Present weather forecast to user

## Features

### Command Line Interface
![CLI Demo](../images/Screenshot%202026-03-01%20005830.png)

- Direct, focused interaction
- Step-by-step workflow visualization
- Great for automation and scripting
- Perfect for developers

### Web Interface
![Web Interface](../images/Screenshot%202026-03-01%20002742.png)

- Interactive, visual experience
- Real-time progress indicators
- Professional presentation
- User-friendly for non-technical users

![Web Interface Steps](../images/Screenshot%202026-03-01%20003114.png)

## Installation

### Prerequisites
- Python 3.7+
- AWS account with Bedrock access
- AWS CLI configured
- Claude 4.5 Sonnet enabled in Amazon Bedrock

### Setup

1. **Clone or download the project files**
   ```bash
   cd agentic-ai-workshop
   ```

2. **Create virtual environment**
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure AWS credentials**
   ```bash
   aws configure
   ```

## Usage

### Command Line Version

![CLI Usage](../images/Screenshot%202026-03-01%20005931.png)

```bash
python weather_agent_cli.py
```

Enter locations like:
- "Seattle" (city names)
- "90210" (ZIP codes)
- "New York City" (multi-word cities)
- "National park near Homestead in Florida" (descriptive locations)

### Web Interface

![Web Interface Launch](../images/Screenshot%202026-03-01%20010113.png)

```bash
streamlit run weather_agent_web.py
```

Then open your browser to `http://localhost:8501`

## Example Interactions

### Location Intelligence
The agent can understand various location formats:

![Location Examples](../images/Screenshot%202026-03-01%20010142.png)

- **City Names**: "Seattle", "Miami"
- **ZIP Codes**: "90210", "10001"
- **Descriptive Queries**: "Largest city in California"
- **Complex Descriptions**: "National park near Homestead in Florida"

### API Call Generation
![API Generation](../images/Screenshot%202026-03-01%20003246.png)

The AI automatically generates the correct National Weather Service API calls:
```
https://api.weather.gov/points/47.6062,-122.3321  # For Seattle
https://api.weather.gov/points/34.0901,-118.4065  # For 90210 (Beverly Hills)
```

### Weather Data Processing
![Data Processing](../images/Screenshot%202026-03-01%20003359.png)

The agent converts complex JSON weather data into human-readable forecasts with:
- Current conditions
- Multi-day outlook
- Temperature and precipitation details
- Wind information
- Weather alerts

## Project Structure

```
agentic-ai-workshop/
├── weather_agent_cli.py      # Command-line interface
├── weather_agent_web.py      # Streamlit web interface
├── requirements.txt          # Python dependencies
└── README.md                # This file
```

## Key Components

### Core Functions

1. **`call_claude_sonnet(prompt)`** - Connects to Amazon Bedrock Claude 4.5 Sonnet
2. **`generate_weather_api_calls(location)`** - AI-powered API URL generation
3. **`execute_curl_command(url)`** - HTTP request execution
4. **`process_weather_response(raw_json, location)`** - AI-powered data analysis

### Technologies Used

- **Amazon Bedrock** - Claude 4.5 Sonnet for AI reasoning
- **National Weather Service API** - Real-time weather data
- **Python** - Core programming language
- **Streamlit** - Web interface framework
- **Boto3** - AWS SDK for Python

## Real-World Applications

The patterns demonstrated in this project apply to many domains:

### Weather & Environmental Services
- Forecast assistants with activity recommendations
- Climate monitoring and adaptation advice
- Disaster response coordination

### Travel & Transportation
- Trip planning with weather integration
- Route optimization based on conditions
- Event management with weather tracking

### Business & Finance
- Market analysis with environmental factors
- Risk assessment incorporating weather data
- Customer support with location-aware responses

## Learning Outcomes

After completing this workshop, you will understand:

✅ **Agentic AI Principles** - Autonomy, reactivity, and proactivity
✅ **Amazon Bedrock Integration** - Claude 4.5 Sonnet API usage
✅ **Prompt Engineering** - Structured prompts for specific tasks
✅ **API Integration Patterns** - Sequential API calls and data processing
✅ **Error Handling** - Graceful failure management
✅ **User Interface Design** - CLI vs web interface considerations



### Setup and Configuration
![Setup](../images/Screenshot%202026-02-28%20234716.png)

### CLI Workflow
![CLI Workflow](../images/Screenshot%202026-03-01%20010211.png)

### Web Interface Features
![Web Features](../images/Screenshot%202026-03-01%20003431.png)

### Results Display
![Results](../images/Screenshot%202026-03-01%20010250.png)

## Next Steps

### Immediate Extensions
1. **Add More APIs** - International weather services, air quality data
2. **Improve Error Handling** - Retry logic and better error messages
3. **Add Memory** - Store previous queries and learn patterns
4. **Enhance UI** - Weather maps, charts, interactive elements

### Intermediate Projects
1. **Multi-Agent Systems** - Agents working together
2. **Tool Integration** - Calculators, databases, notifications
3. **Conversation Flow** - Context maintenance across interactions
4. **Custom Models** - Fine-tuning for specific domains

### Advanced Concepts
1. **Production Deployment** - Lambda, ECS, or EKS scaling
2. **Security & Compliance** - Authentication, encryption, audit logs
3. **Performance Optimization** - Caching, parallel processing
4. **Enterprise Integration** - Business system connections

## Resources

- [Amazon Bedrock Documentation](https://docs.aws.amazon.com/bedrock/)
- [Claude Model Parameters](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters-claude.html)
- [National Weather Service API](https://www.weather.gov/documentation/services-web-api)
- [Streamlit Documentation](https://docs.streamlit.io/)

## Contributing

This project is designed for educational purposes. Feel free to:
- Extend functionality with additional APIs
- Improve error handling and user experience
- Add new interface options
- Enhance the AI prompts for better performance

## License

This project is provided for educational purposes as part of the AWS Agentic AI Workshop.

---

**Built with ❤️ Dineshraj Dhanapathy using Amazon Bedrock, Claude 4.5 Sonnet, and the National Weather Service API**
