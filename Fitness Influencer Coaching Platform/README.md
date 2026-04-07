# Fitness Influencer Coaching Platform - Database Schema

## Overview
This repository contains the **database ER diagram** for a Fitness Influencer Coaching Platform.  
This is an online coaching ecosystem where one or more trainers/influencers manage multiple clients and provide structured online fitness support.

---

## Tables

### Users
Stores all users (clients and trainers).  
- **Columns:** `id`, `name`, `email`, `password`, `phone`, `role`, `dob`  
- **Role:** `"client"` or `"trainer"`

### Clients
Additional info for users with role `client`.  
- FK: `user_id → users.id`

### Trainers
Additional info for users with role `trainer`.  
- FK: `user_id → users.id`  
- Columns: `experience`, `years`

### Programs
Fitness programs or coaching plans.  
- Columns: `id`, `name`, `description`, `duration_days`, `price`, `available_seats`

### Program_Trainers
Bridge table for **programs with multiple trainers**.  
- FK: `program_id → programs.id`  
- FK: `trainer_id → trainers.id`

### Subscriptions
Tracks **client enrollment in programs** over a time period.  
- FK: `client_id → clients.id`  
- FK: `program_id → programs.id`  
- Columns: `valid_from`, `valid_until`, `status`, `created_at`, `updated_at`

### Payments
Tracks payments for subscriptions.  
- FK: `client_id → clients.id`  
- FK: `subscription_id → subscriptions.id`  
- Columns: `amount`, `payment_date`, `transaction_id`

### Sessions
Tracks scheduled sessions or consultations for programs.  
- FK: `program_id → programs.id`  
- FK: `trainer_id → trainers.id`  
- Columns: `session_type`, `scheduled_at`, `duration`, `status`, `link`, `notes`

### Session_Attendance
Tracks which clients attended which sessions.  
- FK: `session_id → sessions.id`  
- FK: `client_id → clients.id`  
- Columns: `status`, `joined_at`

### Progress
Tracks client progress per program.  
- FK: `client_id → clients.id`  
- FK: `program_id → programs.id`  
- Columns: `checkin_date`, `trainer_notes`, `created_at`, `updated_at`

### Progress_Entries
Stores structured metrics for each progress entry (weight, body measurements, etc.).  
- FK: `progress_id → progress.id`  
- Columns: `metric`, `value`

---

## Relationships / Cardinality

- **Users → Clients / Trainers** → 1:1  
- **Programs ↔ Program_Trainers** → M:N  
- **Clients ↔ Subscriptions ↔ Programs** → M:N  
- **Subscriptions → Payments** → 1:N  
- **Sessions → Session_Attendance → Clients** → M:N  
- **Progress → Progress_Entries** → 1:N  

---

## Notes
- This schema supports **multiple trainers per program**, **attendance tracking**, and **detailed client progress tracking**.  
- All foreign keys are properly defined to ensure **referential integrity**.  
