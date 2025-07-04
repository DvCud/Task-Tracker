# Task Tracker Application

## Overview
Task Tracker is a simple task management application built with Node.js, Express, and MongoDB. This application allows users to create, update, and delete tasks while providing a dashboard to visualize task status.

## Incident Resolution: Dashboard Down — Memory Spike

### Summary
The dashboard was previously experiencing access failures after login due to memory spikes in the Node.js application.

### Investigation
The issue was identified as a memory leak in the Node.js session management, specifically in the `express-session` module. The application was not properly cleaning up expired sessions, leading to memory accumulation over time.

### Fix Implemented
1. Updated `express-session` to the latest version
2. Implemented proper session store configuration with MongoDB
3. Added session cleanup with appropriate TTL (Time To Live) settings
4. Implemented memory usage monitoring to track application health
5. Added graceful shutdown handlers to properly close database connections

### Verification
The application now includes:
- Memory usage monitoring accessible via the `/health` endpoint
- Visual memory usage display on the dashboard
- Proper session management with automatic cleanup
- Improved error handling and logging

## Features
- User authentication (simplified for demo)
- Task management (create, read, update, delete)
- Task filtering by status
- Memory usage monitoring
- Responsive design

## Prerequisites
- Node.js (v14 or higher)
- MongoDB
- Docker and Docker Compose (for containerized deployment)

## Running the Application

### Using Docker Compose
1. Clone the repository
2. Navigate to the project directory
3. Run the application:
   ```
   docker-compose up
   ```
4. Access the application at http://localhost:3000

### Manual Setup
1. Clone the repository
2. Navigate to the project directory
3. Install dependencies:
   ```
   cd app
   npm install
   ```
4. Make sure MongoDB is running
5. Start the application:
   ```
   npm start
   ```
6. Access the application at http://localhost:3000

## Default Login
- Username: admin
- Password: password

## Monitoring
The application includes built-in memory monitoring:
- View memory usage on the dashboard
- Access the `/health` endpoint for detailed metrics
- Memory usage is logged to the console every 5 minutes

## Environment Variables
- `PORT`: The port on which the application runs (default: 3000)
- `MONGO_URL`: MongoDB connection string (default: mongodb://localhost:27017/tasktracker)

## License
MIT