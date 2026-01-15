# Personalized Study Assistant Feature

## Overview
The Personalized Study Assistant is a new feature that tracks student search patterns and provides intelligent topic recommendations to enhance their learning experience.

## Features Implemented

### 1. Search Activity Tracking
- **Automatic Tracking**: Every time a student searches for a topic, the system automatically records:
  - Topic name
  - Subject
  - Search count
  - Timestamp
- **Data Storage**: All search activity is stored in `backend/database/search_activity.json`

### 2. Personalized Suggestions
- **Smart Recommendations**: Based on search history, the system suggests:
  - Related topics from frequently searched subjects
  - Popular topics from the same subject area
  - Default suggestions for new users
- **Display Location**: Suggestions appear on the Student Dashboard in an attractive card

### 3. Search History
- **Track Progress**: Students can view their search history
- **Top Searches**: See most frequently searched topics
- **Analytics**: Understand learning patterns

## Object-Oriented Design

### Interfaces
- **`StudyAnalyzer`**: Interface defining study analysis operations
  - `trackSearch()`: Record a topic search
  - `getSearchHistory()`: Retrieve search history
  - `generateSuggestions()`: Create personalized recommendations
  - `getTopSearches()`: Get most searched topics

### Classes
- **`PersonalizedStudyAnalyzer`**: Implementation of StudyAnalyzer
  - Uses dependency injection (Spring @Service)
  - Implements intelligent suggestion algorithm
  - Handles JSON file operations

- **`SearchActivity`**: Model class for search data
  - Stores username and search map
  - Inner class `TopicSearch` for individual topic data
  - Tracks count and timestamps

- **`StudyAssistantController`**: REST controller
  - Handles HTTP requests for study assistant features
  - Provides endpoints for tracking and suggestions
  - Proper exception handling

### Inheritance
- **User Hierarchy**: Existing User → Student → Admin structure maintained
- **Service Layer**: StudyAnalyzer interface → PersonalizedStudyAnalyzer implementation

## API Endpoints

### 1. Track Search
```
POST /api/study-assistant/track
Body: {
  "username": "student1",
  "topic": "arrays",
  "subject": "Data Structures"
}
```

### 2. Get Suggestions
```
GET /api/study-assistant/suggestions/{username}
Response: {
  "success": true,
  "suggestions": ["topic1", "topic2", ...]
}
```

### 3. Get Search History
```
GET /api/study-assistant/history/{username}
Response: {
  "success": true,
  "history": { "topic1": 5, "topic2": 3 },
  "topSearches": [...]
}
```

## Frontend Components

### StudySuggestions Component
- **Location**: `frontend/src/components/StudySuggestions.js`
- **Features**:
  - Fetches personalized suggestions on load
  - Displays suggestions in clickable cards
  - Navigates to topic search when clicked
  - Shows loading and error states
- **Styling**: Custom CSS with gradient background and hover effects

### Integration
- **Student Dashboard**: Suggestions displayed prominently after statistics
- **Topic Search**: Automatically tracks searches with username
- **API Service**: New `studyAssistantAPI` methods added

## Exception Handling

### Backend
- **FileProcessingException**: Thrown when JSON operations fail
- **Try-Catch Blocks**: All service methods wrapped with proper error handling
- **Graceful Degradation**: Returns default suggestions if tracking fails
- **Logging**: Console logging for debugging

### Frontend
- **Error States**: UI shows friendly error messages
- **Loading States**: Spinner while fetching data
- **Empty States**: Helpful messages for new users
- **Network Errors**: Handled by axios interceptors

## Data Flow

1. **Student searches topic** → TopicSearchPage
2. **Search request sent** → NotesController (with username)
3. **Summary generated** → NotesService
4. **Search tracked** → StudyAnalyzer.trackSearch()
5. **Data saved** → search_activity.json
6. **Dashboard loads** → StudySuggestions component
7. **Suggestions fetched** → StudyAssistantController
8. **Algorithm analyzes** → PersonalizedStudyAnalyzer
9. **Suggestions displayed** → Student Dashboard

## Algorithm Logic

### Suggestion Generation
1. **Check search history**: If empty, return default suggestions
2. **Identify top subjects**: Find most frequently searched subjects
3. **Find related topics**: Extract topics from notes in same subject
4. **Rank suggestions**: Based on search frequency and relevance
5. **Return top 5**: Limit to 5 most relevant suggestions

### Related Topic Discovery
- Analyzes note content for keyword matches
- Extracts multi-word phrases from relevant sentences
- Filters out duplicate and irrelevant terms
- Prioritizes topics from frequently searched subjects

## Testing

### Manual Testing Performed
✅ Track search for "arrays" in Data Structures
✅ Track search for "polymorphism" in Java Programming
✅ Track search for "encapsulation" in Java Programming
✅ Verify JSON file updated correctly
✅ Fetch suggestions for student1
✅ Fetch search history for student1
✅ Display suggestions on dashboard

### Test Results
- All endpoints working correctly
- Data persisted to JSON file
- Suggestions generated based on history
- UI displays suggestions properly
- Search tracking integrated with topic search

## Files Created/Modified

### Backend (Java)
- ✅ `StudyAnalyzer.java` - Interface
- ✅ `PersonalizedStudyAnalyzer.java` - Implementation
- ✅ `SearchActivity.java` - Model
- ✅ `StudyAssistantController.java` - REST Controller
- ✅ `NotesController.java` - Modified to track searches

### Frontend (React)
- ✅ `StudySuggestions.js` - Component
- ✅ `StudySuggestions.css` - Styling
- ✅ `StudentDashboard.js` - Modified to include suggestions
- ✅ `TopicSearchPage.js` - Modified to pass username
- ✅ `api.js` - Added study assistant API methods

### Database
- ✅ `search_activity.json` - Search data storage

## Usage Instructions

### For Students
1. **Login** to your student account
2. **Search topics** using the Topic Search feature
3. **View suggestions** on your dashboard
4. **Click suggestions** to explore recommended topics
5. **Track progress** through search history

### For Developers
1. **Backend**: All services use dependency injection
2. **Frontend**: Import `StudySuggestions` component
3. **API**: Use `studyAssistantAPI` methods from api.js
4. **Testing**: Check `backend/database/search_activity.json`

## Future Enhancements
- Add visualization of search patterns
- Implement machine learning for better suggestions
- Add collaborative filtering (suggest what similar students search)
- Create study streaks and achievements
- Export search history reports
- Add topic difficulty ratings

## Conclusion
The Personalized Study Assistant successfully implements OOP principles, proper exception handling, and seamless integration with the existing SmartNotes application. It provides valuable insights to students and enhances their learning experience through intelligent recommendations.
