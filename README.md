# Status Check Application

A full-stack web application for managing status checks with real-time tracking. Built with FastAPI, React, and MongoDB.

## 🚀 Features

- **Status Check Management**: Create and retrieve status checks with client information
- **Real-time Tracking**: Automatic timestamp tracking for all status checks
- **Modern UI**: Built with React 19 and Shadcn/ui components
- **RESTful API**: Well-structured FastAPI backend with proper routing
- **MongoDB Integration**: Efficient data storage with async operations
- **CORS Support**: Configured for cross-origin requests

## 🛠️ Tech Stack

### Backend
- **FastAPI** (0.110.1) - Modern, fast Python web framework
- **Motor** (3.3.1) - Async MongoDB driver
- **Pydantic** (2.6.4+) - Data validation and settings management
- **Python 3.8+** - Core language

### Frontend
- **React** (19.0.0) - UI library
- **React Router DOM** (7.5.1) - Client-side routing
- **Axios** (1.8.4) - HTTP client
- **Tailwind CSS** (3.4.17) - Utility-first CSS framework
- **Radix UI** - Accessible component primitives
- **Shadcn/ui** - Beautiful, accessible components

### Database
- **MongoDB** - NoSQL database for flexible data storage

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- **Node.js** (v16 or higher)
- **Python** (v3.8 or higher)
- **MongoDB** (v4.0 or higher)
- **Yarn** package manager

## 🔧 Installation

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd <project-directory>
```

### 2. Backend Setup

```bash
# Navigate to backend directory
cd backend

# Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Configure environment variables
cp .env.example .env
# Edit .env with your configuration
```

**Backend Environment Variables** (`.env`):
```
MONGO_URL=mongodb://localhost:27017
DB_NAME=test_database
CORS_ORIGINS=*
```

### 3. Frontend Setup

```bash
# Navigate to frontend directory
cd ../frontend

# Install dependencies
yarn install

# Configure environment variables
cp .env.example .env
# Edit .env with your configuration
```

**Frontend Environment Variables** (`.env`):
```
REACT_APP_BACKEND_URL=http://localhost:8001
WDS_SOCKET_PORT=443
REACT_APP_ENABLE_VISUAL_EDITS=false
ENABLE_HEALTH_CHECK=false
```

### 4. Database Setup

Ensure MongoDB is running on your system:

```bash
# Start MongoDB service
# On Linux/Mac:
sudo systemctl start mongod

# On Windows:
net start MongoDB

# Verify MongoDB is running
mongo --eval "db.version()"
```

## 🚀 Running the Application

### Development Mode

**Start Backend** (from `/backend` directory):
```bash
# Using uvicorn directly
uvicorn server:app --reload --host 0.0.0.0 --port 8001

# Or using supervisor (production-like)
sudo supervisorctl restart backend
```

**Start Frontend** (from `/frontend` directory):
```bash
# Start development server
yarn start

# Or using supervisor (production-like)
sudo supervisorctl restart frontend
```

The application will be available at:
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:8001
- **API Documentation**: http://localhost:8001/docs (FastAPI auto-generated)

### Production Mode

**Using Supervisor**:
```bash
# Restart all services
sudo supervisorctl restart all

# Check service status
sudo supervisorctl status

# View logs
sudo supervisorctl tail -f backend
sudo supervisorctl tail -f frontend
```

## 📚 API Documentation

### Endpoints

#### 1. Health Check
```
GET /api/
```
**Response**:
```json
{
  "message": "Hello World"
}
```

#### 2. Create Status Check
```
POST /api/status
```
**Request Body**:
```json
{
  "client_name": "string"
}
```

**Response**:
```json
{
  "id": "uuid-string",
  "client_name": "string",
  "timestamp": "2024-01-01T12:00:00Z"
}
```

#### 3. Get All Status Checks
```
GET /api/status
```
**Response**:
```json
[
  {
    "id": "uuid-string",
    "client_name": "string",
    "timestamp": "2024-01-01T12:00:00Z"
  }
]
```

### Interactive API Documentation

FastAPI provides automatic interactive API documentation:
- **Swagger UI**: http://localhost:8001/docs
- **ReDoc**: http://localhost:8001/redoc

## 📁 Project Structure

```
.
├── backend/                    # FastAPI backend
│   ├── server.py              # Main application file
│   ├── requirements.txt       # Python dependencies
│   └── .env                   # Environment variables
│
├── frontend/                   # React frontend
│   ├── public/                # Static files
│   ├── src/
│   │   ├── App.js            # Main React component
│   │   ├── App.css           # Component styles
│   │   ├── index.js          # Entry point
│   │   └── index.css         # Global styles
│   ├── package.json          # Node dependencies
│   ├── tailwind.config.js    # Tailwind configuration
│   ├── craco.config.js       # CRACO configuration
│   └── .env                  # Environment variables
│
├── tests/                      # Test files
├── test_result.md             # Testing documentation
└── README.md                  # This file
```

## 🔐 Key Design Decisions

1. **UUID Instead of ObjectID**: Using UUID for primary keys instead of MongoDB's ObjectID for better JSON serialization and cross-platform compatibility

2. **Async/Await Pattern**: Motor driver enables async operations for better performance and scalability

3. **API Prefix**: All backend routes use `/api` prefix for clear separation and easier nginx/ingress configuration

4. **CORS Configuration**: Environment-based CORS configuration for flexible deployment options

5. **Timestamp Handling**: Automatic UTC timestamp generation with proper ISO string serialization for MongoDB storage

## 🧪 Testing

### Backend Testing

```bash
cd backend
pytest
```

### Frontend Testing

```bash
cd frontend
yarn test
```

## 🔍 Troubleshooting

### Backend Issues

**MongoDB Connection Error**:
```bash
# Check if MongoDB is running
sudo systemctl status mongod

# Check MongoDB logs
sudo tail -f /var/log/mongodb/mongod.log
```

**Backend Not Starting**:
```bash
# Check backend logs
sudo supervisorctl tail -f backend

# Or check supervisor error logs
tail -n 100 /var/log/supervisor/backend.err.log
```

### Frontend Issues

**Build Errors**:
```bash
# Clear cache and reinstall
rm -rf node_modules yarn.lock
yarn install
```

**Port Already in Use**:
```bash
# Find process using port 3000
lsof -i :3000

# Kill the process
kill -9 <PID>
```

### Database Issues

**Connection Refused**:
- Ensure MongoDB is running: `sudo systemctl start mongod`
- Check MongoDB port: Default is `27017`
- Verify `MONGO_URL` in backend `.env` file

## 🚢 Deployment

### Environment-Specific Configuration

**Production Backend URL**: Update `REACT_APP_BACKEND_URL` in frontend `.env`:
```bash
REACT_APP_BACKEND_URL=https://your-domain.com
```

**Database**: Update `MONGO_URL` in backend `.env` for production MongoDB instance

### Kubernetes Deployment

This application is configured for Kubernetes deployment with:
- Ingress rules routing `/api/*` to backend (port 8001)
- Frontend served on port 3000
- Supervisor for process management

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Style

**Backend**:
- Follow PEP 8 style guide
- Use type hints
- Run `black` for formatting
- Run `flake8` for linting

**Frontend**:
- Follow ESLint configuration
- Use functional components with hooks
- Maintain component modularity

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👥 Authors

- Your Team Name

## 📞 Support

For issues and questions:
- Create an issue in the repository
- Contact: your-email@example.com

## 🙏 Acknowledgments

- FastAPI for the excellent Python web framework
- React team for the powerful UI library
- MongoDB for flexible data storage
- Shadcn for beautiful UI components
- Tailwind CSS for utility-first styling

---

**Built with ❤️ using FastAPI, React, and MongoDB**
