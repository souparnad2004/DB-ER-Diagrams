# 🚀 SMART ELEVATOR CONTROL SYSTEM (DB Design)

A scalable database design (ER diagram) for a smart elevator control system supporting multiple buildings, zones, floors, and elevators.

## 🏗️ Features
- Multi-building architecture
- Zone-based elevator grouping
- Floor-to-elevator mapping (M:N)
- Request → Assignment → Ride execution flow
- Ride history & analytics support
- Maintenance tracking ready design

## 🧠 Core Flow
Request → Ride Assignment → Elevator Execution → Ride Logs

## 📦 Entities
- Buildings
- Zones
- Floors
- Elevators
- Elevator_Floors (mapping)
- Requests
- Ride_Assignments
- Ride_Logs