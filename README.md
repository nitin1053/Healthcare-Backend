# Healthcare Backend System

A Django-based healthcare backend system that manages patients, doctors, and their relationships.

## Features

- User authentication with JWT
- Patient management
- Doctor management
- Patient-Doctor mapping
- RESTful API endpoints
- PostgreSQL database

## Setup Instructions

1. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Create a `.env` file in the root directory with the following variables:
```
DEBUG=True
SECRET_KEY=your-secret-key
DB_NAME=healthcare_db
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_HOST=localhost
DB_PORT=5432
```

4. Run migrations:
```bash
python manage.py migrate
```

5. Create a superuser:
```bash
python manage.py createsuperuser
```

6. Run the development server:
```bash
python manage.py runserver
```

## API Endpoints

### Authentication
- POST /api/auth/register/ - Register a new user
- POST /api/auth/login/ - Login and get JWT token

### Patients
- POST /api/patients/ - Add a new patient
- GET /api/patients/ - List all patients
- GET /api/patients/<id>/ - Get patient details
- PUT /api/patients/<id>/ - Update patient
- DELETE /api/patients/<id>/ - Delete patient

### Doctors
- POST /api/doctors/ - Add a new doctor
- GET /api/doctors/ - List all doctors
- GET /api/doctors/<id>/ - Get doctor details
- PUT /api/doctors/<id>/ - Update doctor
- DELETE /api/doctors/<id>/ - Delete doctor

### Patient-Doctor Mapping
- POST /api/mappings/ - Assign doctor to patient
- GET /api/mappings/ - List all mappings
- GET /api/mappings/<patient_id>/ - Get doctors for patient
- DELETE /api/mappings/<id>/ - Remove doctor from patient 