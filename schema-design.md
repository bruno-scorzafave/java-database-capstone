# Database Design

## MySQL Database Design

### Table: patients
- id : INT, Primary Key, Auto Increment
- name: varchar(100), Not Null
- email: varchar(150), Not Null, Unique
- phone_number: varchar(20)

### Table: doctors
- id : INT, Primary Key, Auto Increment
- name: varchar(100), Not Null
- email: varchar(150), Not Null, Unique
- phone_number: varchar(20)

### Table: admin
- id : INT, Primary Key, Auto Increment
- name: varchar(100), Not Null
- email: varchar(150), Not Null, Unique

### Table: appointments
- id: INT, Primary Key, Auto Increment
- doctor_id: INT, Foreign Key → doctors(id), On Cascade Delete
- patient_id: INT, Foreign Key → patients(id), On Cascade Delete
- appointment_time: DATETIME, Not Null
- status: INT (0 = Scheduled, 1 = Completed, 2 = Cancelled)

## MongoDB Collection Design

### Collection: prescriptions
```json
{
  "_id": "ObjectId('64abc123456')",
  "patientName": "John Smith",
  "appointmentId": 51,
  "medication": "Paracetamol",
  "dosage": "500mg",
  "doctorNotes": "Take 1 tablet every 6 hours.",
  "refillCount": 2,
  "pharmacy": {
    "name": "Walgreens SF",
    "location": "Market Street"
  }
}
```

### Collection: feedback
```json
{
  "_id": "ObjectId('444ajsdn56789')",
  "appointmentId": 12,
  "stars": 5,
  "comments": "Great consult!"
}
```

### Collection: logs
```json
{
  "_id": "ObjectId('13jnj4n5n67')",
  "type": "Error",
  "message": "Error trying to create an appointment",
  "doctorId": 12,
  "patientId": 12,
  "datetime": "2026-07-04T20:04:00.000Z"
}
```