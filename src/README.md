# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Sign up for activities
- Unregister from activities
- Activity data stored in external JSON file for easy updates without editing Python code

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Sign up for an activity                                             |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister a student from an activity                           |

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

### Data Storage

Activities are stored in an external `activities.json` file in the `src/` directory. This design allows administrators to easily add, remove, or modify activities without editing the Python code. The application loads all activities from this JSON file at startup.

**Example activities.json structure:**
```json
{
  "Activity Name": {
    "description": "Activity description",
    "schedule": "Meeting time",
    "max_participants": 20,
    "participants": ["student@email.com"]
  }
}
```

All participant data is stored in memory during the session, which means participant changes will reset when the server restarts. To persist participant changes, integrate with a permanent database (see future enhancements).
