# Flask CRUD Lab

A minimal Flask app demonstrating Create/Read/Update/Delete with SQLite & SQLAlchemy.

## Quickstart

```bash
# 1) Create & activate a virtual environment (Windows PowerShell)
python -m venv env
.\env\Scripts\Activate.ps1

# macOS/Linux
python3 -m venv env
source env/bin/activate

# 2) Install dependencies
pip install -r requirements.txt

# 3) Run the app
python app.py

# Open http://localhost:5000/
```

## Files
- `app.py` – Flask application and routes
- `templates/index.html` – Bootstrap form + table
- `templates/update.html` – Update form

## Notes
- The database file `firstapp.db` is created automatically in the `instance/` folder on first run.
- If you change the model, delete the old database file to rebuild it (or use migrations via Flask-Migrate).