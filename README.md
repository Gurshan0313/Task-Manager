# Task Manager - Full Stack CRUD Application

A complete full-stack task management application with user authentication, built with React, Node.js, Express, and MongoDB.

## 🚀 Features

### ✅ User Authentication
- Register new account
- Login/Logout functionality
- JWT-based authentication
- Protected routes

### ✅ Task Management (CRUD Operations)
- Create new tasks
- Read/View all tasks
- Update/Edit tasks
- Delete tasks
- Mark tasks as complete/incomplete

### ✅ Task Properties
- Title and description
- Priority levels (Low, Medium, High)
- Due dates
- Completion status

### ✅ Additional Features
- Filter tasks (All, Active, Completed)
- Task statistics dashboard
- Responsive design
- Real-time updates

## 🛠️ Tech Stack

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM (Object Data Modeling)
- **JWT** - Authentication tokens
- **bcryptjs** - Password hashing
- **express-validator** - Input validation

### Frontend
- **React** - UI library
- **React Router** - Navigation
- **Axios** - HTTP client
- **Context API** - State management

## 📋 Prerequisites

Before running this project, make sure you have:
- Node.js (v14 or higher) - [Download](https://nodejs.org/)
- MongoDB (local or Atlas cloud) - [Setup Guide](https://docs.mongodb.com/guides/)
- npm or yarn package manager

## 📁 Project Structure

```
task-manager/
├── backend/
│   ├── config/
│   │   └── db.js                 # Database connection
│   ├── models/
│   │   ├── User.js               # User model schema
│   │   └── Task.js               # Task model schema
│   ├── routes/
│   │   ├── auth.js               # Authentication routes
│   │   └── tasks.js              # Task CRUD routes
│   ├── middleware/
│   │   └── auth.js               # JWT authentication middleware
│   ├── .env                      # Environment variables
│   ├── server.js                 # Main server file
│   └── package.json              # Backend dependencies
│
├── frontend/
│   ├── public/
│   │   └── index.html            # HTML template
│   ├── src/
│   │   ├── components/
│   │   │   ├── Auth/
│   │   │   │   ├── Login.jsx     # Login component
│   │   │   │   └── Register.jsx  # Registration component
│   │   │   ├── Tasks/
│   │   │   │   ├── TaskList.jsx  # Main task list view
│   │   │   │   ├── TaskItem.jsx  # Individual task item
│   │   │   │   └── TaskForm.jsx  # Task creation/edit form
│   │   │   └── Layout/
│   │   │       ├── Header.jsx    # App header
│   │   │       └── ProtectedRoute.jsx  # Route protection
│   │   ├── context/
│   │   │   └── AuthContext.jsx   # Authentication context
│   │   ├── services/
│   │   │   └── api.js            # API service layer
│   │   ├── App.jsx               # Main app component
│   │   ├── index.js              # Entry point
│   │   └── index.css             # Global styles
│   ├── .env                      # Frontend environment variables
│   └── package.json              # Frontend dependencies
│
└── README.md                     # This file
```
## 🚀 Installation & Setup
### 1️⃣ Clone or Download the Project
- Download or clone this repository to your local machine.

### 2️⃣ MongoDB Setup
- Option A: MongoDB Atlas (Cloud - Recommended)
- Go to MongoDB Atlas
- Create a free account
- Create a new cluster (M0 Free tier)
- Create a database user with username and password
- Whitelist your IP address (or use 0.0.0.0/0 for development)
- Get your connection string from "Connect" → "Connect your application"
- Option B: Local MongoDB Installation
- Download MongoDB Community Server
- Install and start MongoDB service
- MongoDB will run on mongodb://localhost:27017
  
### 3️⃣ Backend Setup
- Navigate to backend folder
- cd backend
- Install dependencies
- npm install
- Create .env file
- Copy the content below and adjust values
- Create backend/.env file:
```
env
PORT=5000
MONGODB_URI=mongodb+srv://username:password@cluster0.xxxxx.mongodb.net/taskmanager?retryWrites=true&w=majority
JWT_SECRET=your_super_secret_jwt_key_change_in_production
NODE_ENV=development
```
- For Local MongoDB:
```
env
MONGODB_URI=mongodb://localhost:27017/taskmanager
Start the backend server:

bash
# Development mode (with auto-restart)
npm run dev

# OR Production mode
npm start
```
✅ Backend will run on: http://localhost:5000

### 4️⃣ Frontend Setup
Open a new terminal window:
```
bash
# Navigate to frontend folder
cd frontend

# Install dependencies
npm install

# Create .env file
Create frontend/.env file:

env
REACT_APP_API_URL=http://localhost:5000/api
Start the frontend:

bash
npm start
```
✅ Frontend will run on: http://localhost:3000

## 🎯 Usage Guide
### 1. Register a New Account
- Open http://localhost:3000
- Click "Register here"
- Enter username, email, and password
- Click "Register"
### 2. Login
- Go to login page
- Enter your email and password
- Click "Login"
### 3. Create Tasks
- Click "+ Add Task" button
- Fill in task details:
- Title (required)
- Description (optional)
- Priority (Low/Medium/High)
- Due Date (optional)
- Click "Add Task"
### 4. Manage Tasks
- ✅ Complete Task: Click the checkbox
- ✏️ Edit Task: Click the edit icon (✏️)
- 🗑️ Delete Task: Click the delete icon (🗑️)
### 5. Filter Tasks
- Click "All" to see all tasks
- Click "Active" to see incomplete tasks
- Click "Completed" to see finished tasks
### 6. View Statistics
- See total, active, and completed task counts at the top

## 🔌 API Endpoints
### Authentication Routes
#### Method	Endpoint	Description	Auth Required
- POST	/api/auth/register	Register new user	❌
- POST	/api/auth/login	Login user	❌
- GET	/api/auth/me	Get current user	✅
### Task Routes
#### Method	Endpoint	Description	Auth Required
- GET	/api/tasks	Get all user tasks	✅
- GET	/api/tasks/:id	Get single task	✅
- POST	/api/tasks	Create new task	✅
- PUT	/api/tasks/:id	Update task	✅
- DELETE	/api/tasks/:id	Delete task	✅
### Request Headers for Protected Routes:
#### Authorization: Bearer <your_jwt_token>
- 🔒 Security Features
- ✅ Password hashing with bcryptjs
- ✅ JWT token-based authentication
- ✅ Protected API routes with middleware
- ✅ Input validation with express-validator
- ✅ CORS configuration
- ✅ MongoDB injection prevention with Mongoose
- 🐛 Troubleshooting
#### MongoDB Connection Error
**Problem:** MongoDB connection error

**Solution:**

- Ensure MongoDB is running (local) or check Atlas connection string
- Verify MONGODB_URI in .env file
- Check network access in MongoDB Atlas (whitelist IP)
- Port Already in Use
- Problem: Port 5000 is already in use

#### Solution:
```
bash
# Windows
netstat -ano | findstr :5000
taskkill /PID <PID_NUMBER> /F

# Change port in backend/.env
PORT=5001
Cannot Find Module Error
Problem: Cannot find module './context/AuthContext'
```
#### Solution:
```
bash
# Delete node_modules and reinstall
cd frontend
rmdir /s /q node_modules
del package-lock.json
npm install
CORS Issues
Problem: CORS policy: No 'Access-Control-Allow-Origin' header
```
#### Solution:

- Ensure backend is running
- Check REACT_APP_API_URL in frontend .env
- Verify CORS is enabled in backend/server.js
## 🚀 Deployment Options
### Backend Deployment
- Render (Free tier available)
- Railway (Free tier available)
- Heroku (Paid)
- AWS EC2
### Frontend Deployment
- Vercel (Recommended, Free)
- Netlify (Free)
- GitHub Pages
### Database
- MongoDB Atlas (Free tier - 512MB)
## 🎨 Future Enhancements
- Task categories/tags
- Search functionality
- Task sharing between users
- Email notifications
- Mobile app version
- Dark mode toggle
- Drag and drop task reordering
- Task attachments
- Recurring tasks
- Calendar view
## 📝 License
**MIT License** - Feel free to use this project for learning or portfolio purposes.

## 👨‍💻 Author
**Gurshan Singh Sekhon**

- **Portfolio:** [[Gurshan Sekhon](https://exquisite-zuccutto-9fa8b4.netlify.app/)]
- **GitHub:** [@Gurshan0313]
- **LinkedIn:** [[LinkedIn](https://www.linkedin.com/in/gurshan-singh-sekhon-701538237/)]
## 🙏 Acknowledgments
- Built as a portfolio project
- Demonstrates full-stack MERN development skills
- Implements best practices for authentication and CRUD operations
## 📞 Support
**If you have any questions or issues:**

- Check the Troubleshooting section
- Review the project structure
- Ensure all environment variables are set correctly
  
### Happy Task Managing! 🎉


