# Smart Academic Notes Management System - Setup Instructions

## Prerequisites

### Backend Requirements
- Java 11 or higher
- Maven 3.6 or higher
- IDE (IntelliJ IDEA, Eclipse, or VS Code with Java extensions)

### Frontend Requirements
- Node.js 16 or higher
- npm or yarn package manager

## Setup Instructions

### 1. Backend Setup (Java Spring Boot)

#### Step 1: Navigate to Backend Directory
```bash
cd backend
```

#### Step 2: Install Dependencies
```bash
mvn clean install
```

#### Step 3: Run the Backend Server
```bash
mvn spring-boot:run
```

**Alternative: Run from IDE**
- Open the `backend` folder in your Java IDE
- Run the `SmartNotesApplication.java` file
- The server will start on `http://localhost:8080`

#### Verify Backend is Running
- Open browser and go to `http://localhost:8080`
- You should see a Spring Boot default page or error (this is normal)
- Backend APIs are available at `http://localhost:8080/api/`

### 2. Frontend Setup (React)

#### Step 1: Navigate to Frontend Directory
```bash
cd frontend
```

#### Step 2: Install Dependencies
```bash
npm install
```

#### Step 3: Start the Development Server
```bash
npm start
```

The React application will start on `http://localhost:3000` and automatically open in your browser.

### 3. Database Setup (JSON Files)

The JSON database files are already created in the `database/` directory:
- `users.json` - Contains user credentials
- `notes.json` - Contains sample academic notes

**No additional setup required** - the application will automatically create and manage these files.

## Demo Credentials

### Admin Users
- **Username:** `admin` | **Password:** `admin123`
- **Username:** `teacher1` | **Password:** `teacher123`

### Student Users
- **Username:** `student1` | **Password:** `student123`
- **Username:** `student2` | **Password:** `student123`
- **Username:** `john_doe` | **Password:** `john123`

## Application URLs

- **Frontend (React):** http://localhost:3000
- **Backend (Spring Boot):** http://localhost:8080
- **API Base URL:** http://localhost:8080/api

## Testing the Application

### 1. Login Testing
1. Go to `http://localhost:3000`
2. Use demo credentials to login
3. Test both Admin and Student roles

### 2. Admin Features Testing
1. Login as admin
2. Upload new notes via "Upload Notes" page
3. Search for topics
4. View dashboard statistics

### 3. Student Features Testing
1. Login as student
2. Browse available notes
3. Search for topics and generate summaries
4. Download notes

### 4. Topic Summarization Testing
1. Search for topics like:
   - "inheritance" (Java Programming)
   - "arrays" (Data Structures)
   - "SQL" (Database Management)
   - "HTML" (Web Development)
2. Verify summary generation works correctly

## Project Structure

```
smart-notes-system/
├── backend/                    # Java Spring Boot Backend
│   ├── src/main/java/com/smartnotes/
│   │   ├── controller/        # REST Controllers
│   │   ├── service/          # Business Logic Services
│   │   ├── model/            # Data Models (User, Note, Summary)
│   │   ├── util/             # Utility Classes
│   │   ├── exception/        # Custom Exceptions
│   │   └── main/             # Main Application Class
│   ├── src/main/resources/   # Configuration Files
│   └── pom.xml              # Maven Dependencies
├── frontend/                  # React Frontend
│   ├── public/               # Static Files
│   ├── src/
│   │   ├── components/       # Reusable Components
│   │   ├── pages/           # Page Components
│   │   ├── services/        # API Services & Auth Context
│   │   └── styles/          # CSS Styles
│   └── package.json         # NPM Dependencies
├── database/                 # JSON Database Files
│   ├── users.json           # User Credentials
│   └── notes.json           # Academic Notes
└── README.md                # Project Documentation
```

## Features Implemented

### Backend (Java - OOPS Implementation)
✅ **Classes & Objects:** User, Admin, Student, Note, Summary classes
✅ **Inheritance:** Admin and Student extend User class
✅ **Polymorphism:** Abstract methods implemented differently in subclasses
✅ **Interfaces:** Summarizer interface with RuleBasedSummarizer implementation
✅ **Exception Handling:** Custom exceptions for different error scenarios
✅ **File Handling:** JSON file operations for data persistence
✅ **REST APIs:** Complete API endpoints for all operations

### Frontend (React)
✅ **Modern UI:** Clean, colorful, responsive design
✅ **Role-based Access:** Separate Admin and Student dashboards
✅ **Authentication:** Login system with role validation
✅ **File Upload:** Notes upload functionality for admins
✅ **Search & Summarization:** Topic search with intelligent summaries
✅ **Download Feature:** Download notes and summaries
✅ **Smooth Animations:** CSS transitions and hover effects

### Database (JSON)
✅ **User Management:** Role-based user storage
✅ **Notes Storage:** Subject-wise note organization
✅ **Sample Data:** Pre-loaded with test data

## Troubleshooting

### Backend Issues
- **Port 8080 in use:** Change port in `application.properties`
- **Java version:** Ensure Java 11+ is installed
- **Maven issues:** Run `mvn clean install` to resolve dependencies

### Frontend Issues
- **Port 3000 in use:** React will automatically suggest another port
- **Node version:** Ensure Node.js 16+ is installed
- **Dependencies:** Delete `node_modules` and run `npm install` again

### CORS Issues
- Backend is configured to allow requests from `http://localhost:3000`
- If using different ports, update CORS configuration in controllers

### Database Issues
- JSON files are created automatically in the `database/` directory
- If files are corrupted, delete them and restart the backend

## Development Notes

### Adding New Features
1. **Backend:** Add new controllers, services, and models as needed
2. **Frontend:** Create new components and pages following existing patterns
3. **Database:** Extend JSON structure or add new files

### Code Quality
- Backend follows Spring Boot best practices
- Frontend uses modern React patterns with hooks
- Proper error handling and validation throughout
- Responsive design for mobile compatibility

## Production Deployment

### Backend Deployment
1. Build JAR file: `mvn clean package`
2. Run JAR: `java -jar target/smart-notes-backend-1.0.0.jar`
3. Configure production database if needed

### Frontend Deployment
1. Build production files: `npm run build`
2. Serve static files using nginx or similar
3. Update API URLs for production backend

---

**Smart Academic Notes Management System v1.0**
*Complete Full-Stack Java Project with React Frontend*