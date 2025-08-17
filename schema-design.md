## MySQL Database Design

### Table: patients
- id: INT, Primary Key, Auto Increment
- first_name: VARCHAR(50), Not Null
- last_name: VARCHAR(50), Not Null
- dob: DATE, Not Null
- email: VARCHAR(100), Unique
- phone: VARCHAR(20)

### Table: doctors
- id: INT, Primary Key, Auto Increment
- first_name: VARCHAR(50), Not Null
- last_name: VARCHAR(50), Not Null
- specialty: VARCHAR(100), Not Null
- email: VARCHAR(100), Unique

### Table: appointments
- id: INT, Primary Key, Auto Increment
- doctor_id: INT, Foreign Key → doctors(id)
- patient_id: INT, Foreign Key → patients(id)
- appointment_time: DATETIME, Not Null
- status: INT, Default 0 (0 = Scheduled, 1 = Completed, 2 = Cancelled)

### Table: admin
- id: INT, Primary Key, Auto Increment
- first_name: VARCHAR(50), Not Null
- last_name: VARCHAR(50), Not Null
- email: VARCHAR(100), Unique

### Table: payments
- id: INT, Primary Key, Auto Increment
- appointment_id: INT, Foreign Key → appointments(id)
- amount: DECIMAL(10, 2), Not Null
- payment_date: DATETIME, Not Null
- payment_method: VARCHAR(50)

### Table: clinic_locations
- id: INT, Primary Key, Auto Increment
- name: VARCHAR(100), Not Null
- address: VARCHAR(255), Not Null
- phone: VARCHAR(20)


## MongoDB Collection Design

### Collection: prescriptions

```json

{
  "_id": ObjectId("66c071a938c7f2a1b9c7b134"),
  "patientId": 1001,
  "doctorId": 205,
  "prescriptionDate": ISODate("2025-08-18T09:30:00Z"),
  "medication": {
    "name": "Amoxicillin",
    "strength": "500 mg",
    "form": "capsule"
  },
  "dosage": {
    "amount": "1",
    "unit": "capsule",
    "frequency": "three times a day",
    "duration": "10 days"
  },
  "instructions": "Take with food.",
  "status": "active",
  "history": [
    {
      "timestamp": ISODate("2025-08-18T09:30:00Z"),
      "action": "prescribed",
      "notes": "Initial prescription."
    },
    {
      "timestamp": ISODate("2025-08-20T14:00:00Z"),
      "action": "refill_requested",
      "notes": "Patient requested a refill."
    }
  ],
  "tags": [
    "antibiotic",
    "infection",
    "oral"
  ],
  "metadata": {
    "lastUpdated": ISODate("2025-08-20T14:00:00Z"),
    "sourceSystem": "EHR"
  }
}

```

### Collection: feedback

```json

{
  "_id": ObjectId("66c071a938c7f2a1b9c7b135"),
  "userId": 503,
  "submittedAt": ISODate("2025-08-18T10:15:00Z"),
  "type": "feature_request",
  "status": "pending",
  "title": "Add a dark mode theme",
  "content": "A dark mode theme would be great for late-night usage. It would reduce eye strain and look more modern.",
  "metadata": {
    "device": "desktop",
    "browser": "Chrome 127.0",
    "os": "Windows 11"
  },
  "tags": [
    "ui/ux",
    "accessibility",
    "theme"
  ],
  "attachments": [
    {
      "fileName": "dark-mode-mockup.png",
      "fileUrl": "https://cdn.example.com/feedback_attachments/mockup_123.png",
      "fileType": "image/png"
    }
  ],
  "replies": [
    {
      "replyId": 1,
      "replier": "admin@example.com",
      "replyText": "Thank you for the suggestion! We have added this to our feature roadmap.",
      "repliedAt": ISODate("2025-08-19T11:00:00Z")
    }
  ]
}

```