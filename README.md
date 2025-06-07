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

### Authentication APIs

#### 1. Register a new user
- **POST** `/api/users/`
- **Body:**
  ```json
  {
    "name": "John Doe",
    "email": "john@example.com",
    "password": "yourpassword"
  }
  ```

#### 2. Login (JWT Token)
- **POST** `/api/auth/login/`
- **Body:**
  ```json
  {
    "email": "john@example.com",
    "password": "yourpassword"
  }
  ```

### Patient Management APIs

#### 3. Add a new patient
- **POST** `/api/patients/`
- **Body:**
  ```json
  {
    "first_name": "Alice",
    "last_name": "Smith",
    "date_of_birth": "1990-01-01",
    "gender": "F",
    "address": "123 Main St",
    "phone_number": "1234567890",
    "medical_history": "None"
  }
  ```

#### 4. Get all patients (created by authenticated user)
- **GET** `/api/patients/`

#### 5. Get details of a specific patient
- **GET** `/api/patients/<id>/`

### Doctor Management APIs

#### 6. Add a new doctor
- **POST** `/api/doctors/`
- **Body:**
  ```json
  {
    "first_name": "Drake",
    "last_name": "Ramoray",
    "specialization": "CARD",
    "license_number": "LIC123456",
    "phone_number": "9876543210",
    "email": "drake@example.com"
  }
  ```

#### 7. Get all doctors (created by authenticated user)
- **GET** `/api/doctors/`

#### 8. Get details of a specific doctor
- **GET** `/api/doctors/<id>/`

### Patient-Doctor Mapping APIs

#### 9. Assign a doctor to a patient
- **POST** `/api/mappings/`
- **Body:**
  ```json
  {
    "patient": 1,
    "doctor": 2,
    "notes": "Primary cardiologist"
  }
  ```

#### 10. Get all patient-doctor mappings
- **GET** `/api/mappings/`

#### 11. Get all doctors assigned to a specific patient
- **GET** `/api/mappings/patient_doctors/?patient_id=<patient_id>`

**Note:**  
- All endpoints except registration and login require JWT authentication (add `Authorization: Bearer <your_token>` header).
- Replace `<id>` and `<patient_id>` with actual IDs from your database. 