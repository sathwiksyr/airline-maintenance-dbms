# ✈️ Airline Maintenance and Safety Audit System

![MySQL](https://img.shields.io/badge/Database-MySQL-blue)
![SQL](https://img.shields.io/badge/Language-SQL-orange)
![Data Engineering](https://img.shields.io/badge/Focus-Data%20Engineering-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

A **relational database system designed to manage aircraft maintenance operations, inspections, safety audits, and regulatory compliance tracking for airlines.**

The project demonstrates how **structured databases can support safety-critical aviation workflows** by organizing operational data and enabling efficient queries for maintenance tracking and compliance monitoring.

---

# 🚨 Real World Problem

Airlines operate large fleets of aircraft that require **continuous maintenance, safety inspections, and regulatory audits**.

Managing these operations without a structured system can cause:

• Difficulty tracking maintenance history
• Poor visibility of inspection results
• Inefficient audit monitoring
• Compliance risks with aviation regulations
• Data inconsistency across multiple departments

Airlines need a **centralized database system** that ensures **accurate record keeping and traceability of maintenance and safety operations**.

---

# 💡 Solution

This project implements a **relational database architecture** that organizes aircraft maintenance and audit operations into structured tables.

The system enables:

✔ Centralized aircraft information storage
✔ Maintenance activity tracking
✔ Inspection result management
✔ Audit and regulatory compliance monitoring
✔ Automated compliance updates using SQL triggers
✔ Analytical queries for operational insights

This structure ensures **data integrity, traceability, and efficient retrieval of operational records**.

---

# 🏗 System Architecture

```text
Aircraft
   │
   ├── MaintenanceLog ─── Technician
   │
   ├── Inspection ─────── Inspector
   │
   └── AuditAircraft ──── Audit ─── Auditor
                              │
                              └── ComplianceHistory
```

This architecture models the **workflow of aircraft maintenance, inspections, and audits** within airline operations.

---

# 🗂 Database Tables

| Table             | Purpose                                             |
| ----------------- | --------------------------------------------------- |
| Aircraft          | Stores aircraft details and airline ownership       |
| Technician        | Maintenance personnel records                       |
| MaintenanceLog    | Tracks maintenance activities performed on aircraft |
| Inspector         | Inspection staff responsible for safety checks      |
| Inspection        | Records inspection results                          |
| Auditor           | Regulatory auditors                                 |
| Audit             | Audit events and compliance status                  |
| AuditAircraft     | Mapping between audits and aircraft                 |
| ComplianceHistory | Historical compliance records                       |

Total tables implemented: **9**

---

# ⚙️ Key SQL Features

## Database Schema Design

Implemented relational schema using **primary keys, foreign keys, and constraints** to maintain data integrity.

```sql
CREATE TABLE Aircraft (
AircraftID INT PRIMARY KEY,
Model VARCHAR(100),
RegistrationNumber VARCHAR(20) UNIQUE,
ManufactureDate DATE,
AirlineName VARCHAR(100)
);
```

---

## Data Operations

The database includes **30 sample records per table**, simulating realistic airline operations including:

• Aircraft models from Boeing and Airbus
• Multiple technicians and inspectors
• Maintenance operations and inspection results
• Compliance records for regulatory audits

---

## Analytical SQL Queries

The system supports queries for operational insights such as:

• Aircraft belonging to specific airlines
• Maintenance activity summaries
• Inspection statistics per aircraft
• Identification of aircraft with failed inspections

Example:

```sql
SELECT a.AircraftID, a.Model, COUNT(i.InspectionID) AS InspectionCount
FROM Aircraft a
LEFT JOIN Inspection i
ON a.AircraftID = i.AircraftID
GROUP BY a.AircraftID, a.Model;
```

---

## Trigger Automation

A trigger automatically updates **audit compliance status** whenever a compliance record is inserted.

```sql
CREATE TRIGGER UpdateAuditComplianceStatus
AFTER INSERT ON ComplianceHistory
FOR EACH ROW
BEGIN
-- compliance update logic
END;
```

---

## Stored Procedure

Stored procedure used to retrieve **maintenance logs for a specific aircraft**.

```sql
CALL GetMaintenanceLogsForAircraft(1);
```

---

# 📊 Example Insights

Using SQL queries, the database can answer questions such as:

• Which aircraft failed inspections
• How many inspections each aircraft has undergone
• Maintenance activity history for specific aircraft
• Compliance status of audits

These insights help **improve operational transparency and safety monitoring**.

---

# 📂 Project Structure

```
airline-maintenance-dbms
│
├── airline_maintenance_full_database.sql
├── project_report.pdf
├── README.md
└── ER_Diagram.png
```

---

# 🚀 How to Run the Database

1. Open **MySQL Workbench**
2. Import the SQL file

```
airline_maintenance_full_database.sql
```

3. Execute the script

The script will automatically create:

• All database tables
• Sample dataset
• SQL trigger
• Stored procedure

---

# 📈 Future Improvements

Potential improvements include:

• Web interface for database interaction
• Real-time maintenance dashboards
• Integration with airline operational systems
• Performance optimization using advanced indexing

---

# 👨‍💻 Author

**Sathwik S.Y.R**
Computer Science & Data Engineering
