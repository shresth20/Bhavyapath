# Bhavyapath
An intelligent navigation system that predicts waterlogging and provides safe route recommendations using LLM-powered risk assessment.

## 🚀 Features

- **Real-time Waterlogging Prediction**: Uses historical data, weather patterns, and satellite imagery
- **LLM-Powered Risk Assessment**: Intelligent analysis of road conditions and safety
- **Voice Assistant**: Hands-free navigation with live audio interaction
- **Interactive Chat**: Ask questions and get route recommendations from LLM
- **User Feedback System**: Crowdsourced data collection through images, videos, and reports
- **Google Maps Integration**: Seamless route generation and navigation
- **Continuous Learning**: Model improves with user feedback

## 🛠️ Tech Stack

### Backend
- **Python 3.10+**
- **Flask** - Web framework
- **SQLAlchemy** - ORM for database operations
- **Flask-Migrate** - Database migrations
- **LLM Integration** - For predictions and chat
- **Google Maps API** - Route generation
- **OpenWeather API** - Weather data

### Frontend
- **Vue.js 3** - Progressive JavaScript framework
- **Vuex** - State management
- **Vue Router** - Navigation
- **Axios** - HTTP client
- **Leaflet/Google Maps** - Map visualization
- **TailwindCSS** - Styling

### Database
- **PostgreSQL** - Primary database
- **Redis** - Caching and session management

## 📋 Prerequisites

- Python 3.10 or higher
- Node.js 16 or higher
- PostgreSQL 13+
- Redis 6+
- Google Maps API Key
- OpenWeather API Key
- LLM API Access (OpenAI/Anthropic/etc.)

## 🔑 Environment Variables

### Backend (.env)
```env
FLASK_APP=run.py
FLASK_ENV=development
SECRET_KEY=your-secret-key
DATABASE_URL=postgresql://user:password@localhost:5432/waterlogging_db
REDIS_URL=redis://localhost:6379/0

# API Keys
GOOGLE_MAPS_API_KEY=your-google-maps-key
OPENWEATHER_API_KEY=your-openweather-key
LLM_API_KEY=your-llm-api-key
SATELLITE_API_KEY=your-satellite-api-key

# LLM Configuration
LLM_MODEL=gpt-4
LLM_TEMPERATURE=0.7
```

### Frontend (.env)
```env
VITE_API_BASE_URL=http://localhost:5000/api
VITE_GOOGLE_MAPS_API_KEY=your-google-maps-key
VITE_WS_URL=ws://localhost:5000
```
## Project Flowchart: [View](https://www.mermaidchart.com/view/0c0f0874-30e1-402c-829c-ac7913673bf4)
## 📁 Project Structure

```
Bhavyapath/
│
├── backend/
│   ├── app/
│   │   ├── __init__.py                 # Flask app initialization and DB setup
│   │   ├── config.py                   # Configuration (API keys, DB URI, etc.)
│   │   │
│   │   ├── models/                     # SQLAlchemy ORM models
│   │   │   ├── user.py
│   │   │   ├── feedback.py
│   │   │   ├── rain_data.py
│   │   │   ├── road_condition.py
│   │   │   └── prediction.py
│   │   │
│   │   ├── routes/                     # Flask Blueprints for REST APIs
│   │   │   ├── user_routes.py
│   │   │   ├── feedback_routes.py
│   │   │   ├── prediction_routes.py
│   │   │   ├── data_routes.py
│   │   │   └── satellite_routes.py
│   │   │
│   │   ├── controllers/                # Business logic and processing
│   │   │   ├── llm_controller.py       # Core LLM query handling
│   │   │   ├── weather_controller.py   # Rain data and weather integration
│   │   │   ├── satellite_controller.py # Image/video ingestion
│   │   │   └── risk_controller.py      # Road risk prediction and analysis
│   │   │
│   │   ├── services/                   # API and LLM integrations
│   │   │   ├── llm_service.py          # Interaction with LLM (OpenAI, Ollama, etc.)
│   │   │   ├── google_maps_service.py  # Route and pathfinding via Google API
│   │   │   ├── weather_service.py      # Weather/rain data API service
│   │   │   └── satellite_service.py    # Handles satellite data sources
│   │   │
│   │   ├── utils/
│   │   │   ├── data_preprocessor.py    # Clean & format data before feeding to LLM
│   │   │   ├── coordinate_helper.py    # Handle lat-long and geospatial ops
│   │   │   └── risk_calculator.py      # Risk score calculation logic
│   │   │
│   │   ├── static/                     # Static assets (if required)
│   │   └── templates/                  # HTML templates (if Flask renders any)
│   │
│   ├── instance/
│   │   └── app.db                      # SQLite (or SQLAlchemy) local DB
│   │
│   ├── scripts/
│   │   ├── data_collector.py           # Collect data from APIs & user input
│   │   ├── model_trainer.py            # Update or fine-tune risk model
│   │   └── data_validator.py           # Validate and clean incoming data
│   │
│   ├── run.py                          # Flask app entry point
│   ├── requirements.txt                # Python dependencies
│   └── .env                            # Environment variables (API keys, DB URI)
│
├── frontend/
│   ├── public/
│   │   └── index.html                  # Vue root HTML
│   │
│   ├── src/
│   │   ├── assets/                     # Images, icons, etc.
│   │   ├── components/
│   │   │   ├── AudioAssistant.vue      # Voice interaction UI
│   │   │   ├── MapDisplay.vue          # Google Map and route visualization
│   │   │   ├── RiskAlert.vue           # Displays route risk warnings
│   │   │   └── FeedbackForm.vue        # Collects user feedback
│   │   │
│   │   ├── pages/
│   │   │   ├── Home.vue
│   │   │   ├── Navigation.vue
│   │   │   └── ReportIssue.vue
│   │   │
│   │   ├── store/
│   │   │   └── index.js                # Vuex store for state management
│   │   │
│   │   ├── services/
│   │   │   ├── api.js                  # Axios setup for backend communication
│   │   │   ├── voice_recognition.js    # Speech-to-text for audio commands
│   │   │   └── text_to_speech.js       # Converts LLM responses to voice
│   │   │
│   │   ├── App.vue
│   │   └── main.js
│   │
│   ├── package.json
│   └── vite.config.js
│
├── data/
│   ├── sample_rain_data.csv
│   ├── road_condition_data.csv
│   ├── satellite_images/
│   └── feedback_reports/
│
├── docs/
│   ├── architecture_diagram.png
│   ├── project_flowchart.png
│   └── API_documentation.md
│
└── README.md
```

## 🔄 API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout

### Location & Prediction
- `GET /api/location/current` - Get current location data
- `POST /api/prediction/waterlog` - Predict waterlogging
- `POST /api/prediction/risk` - Assess route risk

### Navigation
- `POST /api/navigation/route` - Generate route
- `GET /api/navigation/alternatives` - Get alternative routes
- `POST /api/navigation/start` - Start navigation

### Feedback
- `POST /api/feedback/report` - Submit feedback
- `POST /api/feedback/upload` - Upload images/videos
- `GET /api/feedback/history` - Get user feedback history

### Chat
- `POST /api/chat/message` - Send message to LLM
- `GET /api/chat/history` - Get chat history
- `POST /api/chat/voice` - Voice input processing

## 📊 Data Flow

1. **User Input** → Voice/Manual destination entry
2. **Data Collection** → Location, weather, satellite data
3. **LLM Processing** → Analyze and predict risks
4. **Route Generation** → Google Maps integration
5. **Navigation** → Real-time tracking and monitoring
6. **Feedback Loop** → Collect user reports for improvement

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 👥 Team

- [Shresth kasera](https://github.com/shresth20)
- [Pingaksha Sahay](https://github.com/pingaksha30)
- [Arnav Labhasetwar](https://github.com/ArnavLabh)
- [Madhav Rimal](https://github.com/madhavprapanna52)

## Resources: [view](https://docs.google.com/document/d/1Z9QdXLiajPHiqRQofQmp0IJWrJyJe3x-_geLvvRI0fY/edit?usp=sharing)
