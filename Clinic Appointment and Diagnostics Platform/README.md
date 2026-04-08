# Clinic Appointment and Diagnostics Platform - Database Design

## Overview
This is an ER diagram design for a **clinic management system**. It manages:

- Users (Doctors and Patients)
- Appointments and Consultations
- Diagnostic Tests and Reports
- Payments

Patients can book appointments, visit doctors, get prescribed tests, and receive reports. Doctors manage consultations, specialties, and follow-ups.

---

## Tables and Relationships

### Users
- Stores general information for all users.
- Attributes: `id`, `name`, `email`, `phone`, `dob`, `role`, `address`, `created_at`, `updated_at`.

### Doctors
- Links to a user and stores doctor-specific info.
- `user_id` → `users.id`
- Many-to-many with specialties via `doctor_specialty`.

### Specialties & Doctor_Specialty
- `specialties`: list of medical specialties.
- `doctor_specialty`: join table (composite PK: doctor_id + specialty_id).

### Patients & Doctor_Patient
- `patients`: links to a user, stores patient-specific info (`gender`, `blood_group`).
- `doctor_patient`: optional join table for patient–doctor mapping.

### Appointments
- Scheduled bookings between patients and doctors.
- Attributes: `doctor_id`, `patient_id`, `scheduled_at`, `status`, `reason`.
- Links: `appointments.doctor_id` → `doctors.id`, `appointments.patient_id` → `patients.id`.

### Consultations
- Represents actual visits.
- Attributes: `appointment_id` (optional), `doctor_id`, `patient_id`, `diagnosis`, `consultation_date`.
- Links: `doctor_id` → `doctors.id`, `patient_id` → `patients.id`, `appointment_id` → `appointments.id`.

### Diagnostics & Reports
- `diagnostics`: tests prescribed during a consultation.
- `reports`: results of tests linked to consultations and patients.

### Payments
- Tracks billing for consultations (and optionally tests).
- Attributes: `consultation_id`, `patient_id`, `amount`, `payment_method`, `status`, `payment_date`.

---

## Notes
- Many-to-many relationships handled with join tables.
- Consultations are distinct from appointments.
- Diagnostics and reports are linked to consultations.
- Payments are linked to consultations.

---

## Submission
- ER diagram included as image/PDF.
