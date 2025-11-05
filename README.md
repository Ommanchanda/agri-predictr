<div align="center">

# 🎯 Status Check Application

### *A Modern Full-Stack Status Tracking System*

[![FastAPI](https://img.shields.io/badge/FastAPI-0.110.1-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![React](https://img.shields.io/badge/React-19.0.0-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org/)
[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.4.17-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)

**A lightning-fast, beautiful web application for managing status checks with real-time tracking capabilities.**

[Features](#-features) • [Tech Stack](#️-tech-stack) • [Installation](#-quick-start) • [API Docs](#-api-reference) • [Contributing](#-contributing)

</div>

---

## ✨ Features

<table>
<tr>
<td width="50%">

### 🎨 **Beautiful Modern UI**
- Built with React 19 & Shadcn/ui
- Fully responsive design
- Dark mode ready
- Smooth animations

</td>
<td width="50%">

### ⚡ **Lightning Fast API**
- RESTful FastAPI backend
- Async operations
- Auto-generated docs
- Type-safe responses

</td>
</tr>
<tr>
<td width="50%">

### 📊 **Status Management**
- Create status checks
- Real-time tracking
- Automatic timestamps
- Client information logging

</td>
<td width="50%">

### 🔒 **Production Ready**
- CORS configuration
- Environment-based setup
- Kubernetes compatible
- Scalable architecture

</td>
</tr>
</table>

---

## 🛠️ Tech Stack

<div align="center">

### Backend Architecture
| Technology | Version | Purpose |
|------------|---------|---------|
| **FastAPI** | 0.110.1 | High-performance Python web framework |
| **Motor** | 3.3.1 | Async database driver |
| **Pydantic** | 2.6.4+ | Data validation & serialization |
| **Python** | 3.8+ | Core programming language |

### Frontend Stack
| Technology | Version | Purpose |
|------------|---------|---------|
| **React** | 19.0.0 | Modern UI library with latest features |
| **React Router** | 7.5.1 | Client-side routing & navigation |
| **Axios** | 1.8.4 | Promise-based HTTP client |
| **Tailwind CSS** | 3.4.17 | Utility-first CSS framework |
| **Radix UI** | Latest | Accessible component primitives |
| **Shadcn/ui** | Latest | Beautiful, accessible components |

</div>

---

## 📋 Prerequisites

<div align="center">

| Requirement | Version | Download |
|------------|---------|----------|
| 🟢 **Node.js** | v16+ | [Download](https://nodejs.org/) |
| 🐍 **Python** | v3.8+ | [Download](https://python.org/) |
| 📦 **Yarn** | Latest | [Install](https://yarnpkg.com/) |
| 🗄️ **Database** | v4.0+ | Auto-configured |

</div>

---

## 🚀 Quick Start

### 📥 Step 1: Clone the Repository

```bash
git clone <your-repository-url>
cd <project-directory>
```

<details>
<summary><b>🐍 Step 2: Backend Setup</b></summary>

```bash
# Navigate to backend directory
cd backend

# Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install all dependencies
pip install -r requirements.txt
```

**Configure Environment Variables** - Create `.env` file:
```env
DB_URL=<your-database-connection-string>
DB_NAME=status_check_db
CORS_ORIGINS=*
```

> 💡 **Tip**: The database connection is automatically configured for local development

</details>

<details>
<summary><b>⚛️ Step 3: Frontend Setup</b></summary>

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies with Yarn
yarn install
```

**Configure Environment Variables** - Create `.env` file:
```env
REACT_APP_BACKEND_URL=http://localhost:8001
WDS_SOCKET_PORT=443
REACT_APP_ENABLE_VISUAL_EDITS=false
ENABLE_HEALTH_CHECK=false
```

> 🎨 **Note**: Hot reload is enabled for seamless development

</details>

<details>
<summary><b>🗄️ Step 4: Database Setup</b></summary>

The application uses an async database driver for optimal performance:

```bash
# Database service starts automatically with the application
# No manual setup required for local development
```

> ✅ **Auto-configured**: Database connection is handled via environment variables

</details>

---

## 🎬 Running the Application

### 🔥 Development Mode

<table>
<tr>
<td width="50%">

**🔧 Start Backend**
```bash
cd backend

# Direct start
uvicorn server:app --reload \
  --host 0.0.0.0 --port 8001

# Or with supervisor
sudo supervisorctl restart backend
```

</td>
<td width="50%">

**🎨 Start Frontend**
```bash
cd frontend

# Development server
yarn start

# Or with supervisor
sudo supervisorctl restart frontend
```

</td>
</tr>
</table>

### 🌐 Access Your Application

<div align="center">

| Service | URL | Description |
|---------|-----|-------------|
| 🎨 **Frontend** | http://localhost:3000 | Main application UI |
| 🔌 **Backend API** | http://localhost:8001 | REST API endpoint |
| 📚 **API Docs** | http://localhost:8001/docs | Interactive Swagger UI |
| 📖 **ReDoc** | http://localhost:8001/redoc | Alternative API documentation |

</div>

### 🚀 Production Mode

```bash
# Restart all services
sudo supervisorctl restart all

# Check service status
sudo supervisorctl status

# View real-time logs
sudo supervisorctl tail -f backend
sudo supervisorctl tail -f frontend
```

> 🔄 **Hot Reload**: Both frontend and backend support hot reload - changes are reflected automatically!

---

## 📚 API Reference

<div align="center">

### 🎯 Available Endpoints

FastAPI provides **automatic interactive documentation** with beautiful UI!

[![Swagger UI](https://img.shields.io/badge/Swagger-UI-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)](http://localhost:8001/docs)
[![ReDoc](https://img.shields.io/badge/Re-Doc-8CA1AF?style=for-the-badge&logo=read-the-docs&logoColor=white)](http://localhost:8001/redoc)

</div>

### 🔌 API Endpoints

<details>
<summary><b>✅ Health Check</b> - Verify API is running</summary>

**Endpoint:** `GET /api/`

**Response:**
```json
{
  "message": "Hello World"
}
```

**Example:**
```bash
curl http://localhost:8001/api/
```

</details>

<details>
<summary><b>➕ Create Status Check</b> - Add new status entry</summary>

**Endpoint:** `POST /api/status`

**Request Body:**
```json
{
  "client_name": "Production Server"
}
```

**Response:**
```json
{
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "client_name": "Production Server",
  "timestamp": "2024-01-01T12:00:00Z"
}
```

**Example:**
```bash
curl -X POST http://localhost:8001/api/status \
  -H "Content-Type: application/json" \
  -d '{"client_name": "Production Server"}'
```

</details>

<details>
<summary><b>📋 Get All Status Checks</b> - Retrieve all entries</summary>

**Endpoint:** `GET /api/status`

**Response:**
```json
[
  {
    "id": "550e8400-e29b-41d4-a716-446655440000",
    "client_name": "Production Server",
    "timestamp": "2024-01-01T12:00:00Z"
  },
  {
    "id": "660e8400-e29b-41d4-a716-446655440001",
    "client_name": "Development Server",
    "timestamp": "2024-01-01T12:05:00Z"
  }
]
```

**Example:**
```bash
curl http://localhost:8001/api/status
```

</details>

---

### 🎨 Interactive Documentation

FastAPI automatically generates beautiful, interactive API documentation:

| Documentation | Features | URL |
|--------------|----------|-----|
| **Swagger UI** | • Interactive testing<br>• Request/response samples<br>• Schema validation | [http://localhost:8001/docs](http://localhost:8001/docs) |
| **ReDoc** | • Clean interface<br>• Downloadable specs<br>• Responsive design | [http://localhost:8001/redoc](http://localhost:8001/redoc) |

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
