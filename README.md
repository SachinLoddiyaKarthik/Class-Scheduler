# 📅 Class Scheduling Optimization System

![Python](https://img.shields.io/badge/Python-3.9-blue?logo=python)
![Google OR-Tools](https://img.shields.io/badge/Google_OR--Tools-Optimization-brightgreen)
![PyQt](https://img.shields.io/badge/PyQt-GUI-orange?logo=qt)
![Constraint Programming](https://img.shields.io/badge/Constraint_Programming-MIP-ff69b4)
![CSV](https://img.shields.io/badge/CSV-Data_Input-yellow)
![PDF](https://img.shields.io/badge/PDF-Export_Supported-lightgrey)

A robust, constraint-based course scheduling system built for the WMU Statistics Department that balances faculty preferences, program constraints, and academic policies using Mixed Integer Programming and a drag-and-drop interactive UI.

---

## 📌 Project Overview

Manual scheduling of classes is time-consuming and prone to conflicts. This system offers a **fully automated class scheduling solution** that:

- Uses **Mixed Integer Programming (MIP)** via **Google OR-Tools**
- Optimizes based on **hard** (e.g., instructor availability, no overlaps) and **soft** constraints (e.g., preferences, breaks)
- Features a **PyQt-based UI** with drag-and-drop editing and real-time conflict validation
- Supports structured data input/output in CSV, Excel, and PDF formats

---

## 🎯 Key Objectives

| Objective | Impact |
|----------|--------|
| Automate class scheduling | Reduce manual effort for department chairs |
| Respect preferences | Improve faculty satisfaction |
| Avoid conflicts | Eliminate scheduling overlaps |
| Export schedules | Support PDF/Excel sharing and reporting |
| Support manual overrides | Enable admins to adjust using UI |

---

## 🛠️ Technology Stack

### ⚙️ Backend Optimization
- **Google OR-Tools** – Constraint programming (CP-SAT solver)
- **Python** – Core implementation
- **Pandas** – Data transformation and preprocessing
- **CSV** – Input format for course, instructor, timeslot, and preferences

### 🖥️ Frontend UI
- **PyQt5** – GUI framework
- **QThread** – For background threading (no UI freeze)
- **DragDropTable** – Custom table widget with drag-and-drop
- **pdfplumber** – For parsing uploaded PDFs

### 📦 System Architecture
- Three-tier architecture: **Presentation**, **Business Logic**, **Data Layer**
- Signal-slot model for **event-driven** updates
- Uses **asynchronous threads** for backend processing

---

## 📐 Mathematical Formulation

The scheduling problem is modeled as a **Constraint Satisfaction Problem (CSP)**:

### ✏️ Decision Variable
```python
Xc,t,d,f = 1 if course `c` is scheduled at time slot `t`, day `d`, with faculty `f`
````

### ✅ Hard Constraints

* No instructor/TA overlap
* Consistent time slots across days
* Required courses in a specialization cannot overlap
* TA-led courses only for introductory sections

### ⚠️ Soft Constraints (penalty-based)

* Faculty time-of-day preferences (morning/afternoon/evening)
* Minimum break duration between courses
* Elective vs required overlap minimization
* External department conflicts (e.g., CS or Math)

---

## 🧪 Sample Input Data

| File                         | Description                                           |
| ---------------------------- | ----------------------------------------------------- |
| `fallcourses.csv`            | Faculty-led courses with timings and preferences      |
| `intro.csv`                  | Introductory courses assigned to TAs                  |
| `timeslot.csv`               | All valid time slot templates                         |
| `programs_dimension.csv`     | Specialization mapping: required, electives, external |
| `external.csv`               | External course times (CS, Math)                      |
| `instructor_preferences.csv` | Instructor teaching preferences and break times       |

---

## 🖼️ UI Features

### 🔄 Real-Time Drag and Drop

* Rearrange schedules directly on the GUI
* Conflicts highlighted instantly

### 🧾 PDF Upload

* Use `pdfplumber` to parse and import existing schedules

### 📥 Schedule Export

* Final schedule exportable as CSV, PDF, or Excel

### 🔍 Conflict Reports

* Detailed conflict insights for required vs elective overlap
* Instructor/TA scheduling violations

---

## 📊 Output Example

```plaintext
Course Code  | Time Slot | Day       | Instructor
-------------|-----------|-----------|------------
STAT 5680    | T27       | Tue/Thu   | D. Ngo
STAT 4640    | T32       | Mon/Wed   | Y. Zhang
STAT 6620    | T31       | Tue/Thu   | J. Naranjo
```

All constraints were satisfied in the sample output.

---

## ⚙️ Performance Optimization

| Technique         | Implementation              | Result                  |
| ----------------- | --------------------------- | ----------------------- |
| Symmetry Breaking | Course ordering constraints | 22% faster solve times  |
| Lazy Constraints  | Added on-demand             | 35% memory reduction    |
| Parallel Solving  | OR-Tools CP-SAT (8 cores)   | 3.1× faster performance |

---

## 🌱 Future Enhancements

* 📊 **Faculty Load Balancing** – Even teaching distribution
* ⏳ **Dynamic Re-optimization** – Mid-semester adjustment handling
* 🌐 **Web Interface (Flask)** – Accessible scheduling portal
* 🤖 **ML-based Conflict Prediction** – Learn from past trends
* 🏫 **Multi-Department Support** – Cross-campus scheduling logic

---

## 🤝 Contributing

We welcome improvements and collaborations!

1. Fork the repository
2. Create a branch (`git checkout -b feature/scheduler-enhancement`)
3. Commit your changes (`git commit -m "Added new scheduling constraint"`)
4. Push the branch (`git push origin feature/scheduler-enhancement`)
5. Open a Pull Request 🚀

---

## 📬 Contact

**Sachin Loddiya Karthik**
[GitHub](https://github.com/SachinLoddiyaKarthik)
[LinkedIn](https://www.linkedin.com/in/sachin-lk/)

---

**Repository Link**:
👉 [https://github.com/SachinLoddiyaKarthik/class-scheduler-optimizer](https://github.com/SachinLoddiyaKarthik/class-scheduler-optimizer)

