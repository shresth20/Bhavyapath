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

## 🔧 Installation

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/waterlogging-navigation-system.git
cd waterlogging-navigation-system
```

### 2. Backend Setup

```bash
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Copy environment variables
cp .env.example .env
# Edit .env with your configuration

# Initialize database
flask db init
flask db migrate -m "Initial migration"
flask db upgrade

# Run the backend
python run.py
```

### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env
# Edit .env with your configuration

# Run development server
npm run dev
```

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

## 📁 Project Structure

```
├── backend/          # Flask backend
│   ├── app/         # Application code
│   │   ├── models/  # Database models
│   │   ├── routes/  # API endpoints
│   │   ├── services/# Business logic
│   │   ├── ml/      # Machine learning
│   │   └── utils/   # Utilities
│   └── tests/       # Backend tests
│
├── frontend/        # Vue.js frontend
│   ├── src/
│   │   ├── components/ # Vue components
│   │   ├── views/      # Page views
│   │   ├── store/      # Vuex store
│   │   └── router/     # Vue Router
│   └── public/         # Static assets
│
├── data/            # Data storage
│   ├── raw/        # Raw data
│   ├── processed/  # Processed data
│   └── models/     # ML models
│
└── docs/           # Documentation
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

## 🧪 Testing

### Backend Tests
```bash
cd backend
pytest tests/
```

### Frontend Tests
```bash
cd frontend
npm run test
```

## 🐳 Docker Deployment

```bash
# Build and run with Docker Compose
docker-compose up -d

# Access the application
# Frontend: http://localhost:3000
# Backend API: http://localhost:5000
```

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

## 🙏 Acknowledgments

- Google Maps API for navigation
- OpenWeather for weather data
- Satellite imagery providers
- LLM providers for AI capabilities
