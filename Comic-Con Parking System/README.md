# 🎭 Comic-Con Parking System

## 📌 Overview
Database design (ERD) for managing parking at a Comic-Con event.  
Handles vehicle entry, spot allocation, ticket generation, and payments across zones and levels.

---

## 🧠 Parking Structure
- **Zone** → Area (A, B, VIP)
- **Level** → Floor inside zone
- **Spot** → Individual parking space

**Spot Format:**  
```
<Zone>-<Level>-<Spot>
Example: A-L1-01
```

---

## 🗂️ Main Tables
- **owners** → vehicle owners  
- **vehicles** → vehicle details  
- **vehicle_categories** → bike, car, SUV, EV  
- **parking_zones** → parking areas  
- **parking_levels** → floors in zones  
- **parking_spots** → individual spots  
- **reserved_parking_categories** → VIP, staff, exhibitors, EV  
- **parking_sessions** → entry & exit tracking  
- **tickets** → generated parking tickets  
- **payments** → payment records  

---

## ⚡ Key Features
- Multi-zone & multi-level parking  
- Reserved category support  
- Ticket generation system  
- Payment tracking  
- Reusable spots & multiple visits  

---

## 🔄 Availability Logic
- **Occupied** → session with `exited_at IS NULL`  
- **Available** → no active session
  
---

## 🚀 Summary
A normalized and scalable parking system designed for real-world event management.
