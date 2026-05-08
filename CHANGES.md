# Change Log

## [v1.1.0] - 2026-05-08

### Added
- **External Activity Configuration File**: Activities are now stored in `src/activities.json` instead of being hardcoded in `src/app.py`
  - Teachers and administrators can now easily add, modify, or remove activities without editing Python code
  - Reduces risk of breaking the application when making activity updates
  - Makes the system more maintainable and user-friendly

- **DELETE Endpoint**: Added `/activities/{activity_name}/unregister` endpoint to allow students to unregister from activities
  - Includes validation to ensure the student is actually signed up before unregistering

### Changed
- Refactored `src/app.py` to load activities from external JSON file at application startup
- Updated documentation in `src/README.md` to explain the new data storage model

### Technical Details
- New function `load_activities()` in `src/app.py` handles JSON file loading with error handling
- Graceful error messages if `activities.json` is missing or has invalid JSON syntax
- All 9 existing activities are now maintained in `src/activities.json`

### Benefits
- **Ease of Use**: Non-technical users (teachers) can now manage activities through simple JSON file editing
- **Safety**: Reduces risk of introducing Python syntax errors when adding/removing activities
- **Maintainability**: Clear separation between business logic (Python) and data (JSON)
- **Scalability**: Foundation for future database integration

### Related Issues
- Closes #3: "Hard to change activities"

---

## Previous Releases

### [v1.0.0] - Initial Release
- Basic FastAPI application for activity signup
- View all available activities
- Sign up for activities (POST endpoint)
- In-memory data storage
