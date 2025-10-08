# Dare Careers Power BI Learner Performance Dashboard

## Overview  
Dare Careers is a business that provides training in **Power BI** and **AWS Cloud**. To effectively monitor the progress and performance of its students, Dare Careers requires a comprehensive **Power BI dashboard**.  

This dashboard tracks key metrics, including:  
- Daily Zoom attendance records  
- Daily participation  
- Weekly quiz and lab grades  
- Learner status (graduation and certification)  

The dashboard provides actionable insights into learner engagement, progress, and outcomes — helping program managers and trainers to:  
- Track performance trends over time  
- Identify learners at risk of dropping out  
- Measure key performance indicators such as certification and graduation rates  

---

##  Data Model Overview  
The Power BI model integrates multiple data sources representing different aspects of the training program. The main tables include:  

- **Students** – Contains learner information such as student name, track, and ID.  
- **Zoom Attendance** – Records attendance details for each student, including date and duration (used to mark presence or absence).  
- **Participation** – Captures whether students participated in daily sessions.  
- **Labs & Quizzes** – Stores scores for weekly labs and quizzes.  
- **Status of Learner** – Tracks whether a student is certified, graduated, or still in progress.  
- **Date Table** – A master calendar used to enable time intelligence (daily, weekly, and monthly trends).  

Each table is connected using **relationships** to ensure that filters, slicers, and visuals in the report interact correctly.

---

## Power BI Relationships Explained  

The Power BI model uses **1-to-many (1:*)** relationships to connect dimension tables (like *Students* and *Date Table*) with fact tables (like *Zoom Attendance* and *Labs & Quizzes*).  

![Model](<images/Model_view.png>)

Here’s what each relationship means:

###  `Students[Student Name] → Zoom Attendance[Student Name]`
- **Type:** One-to-Many (1:*)  
- **Meaning:** Each student in the *Students* table can appear multiple times in the *Zoom Attendance* table because they attend multiple sessions.  
- **Purpose:** Enables filtering of attendance records by specific student.

---

### `Students[Student Name] → Participation[Student Name]`
- **Type:** One-to-Many (1:*)  
- **Meaning:** Each student can have multiple participation records across different days.  
- **Purpose:** Allows the report to calculate participation rates per student.

---

### `Students[Student Name] → Labs & Quizzes[Student Name]`
- **Type:** One-to-Many (1:*)  
- **Meaning:** A student can have multiple quiz or lab entries across program weeks.  
- **Purpose:** Supports calculation of average scores, lab completion rate, and performance over time.

---

### `Students[Student Name] → Status of Learner[Student Name]`
- **Type:** One-to-One (1:1)  
- **Meaning:** Each student has only one status record (Certified, Not Certified, or In Progress).  
- **Purpose:** Enables filtering visuals to show performance based on learner status.

---

### `DateTable[Date] → Zoom Attendance[Date]`
- **Type:** One-to-Many (1:*)  
- **Meaning:** Each date in the *Date Table* can appear multiple times in *Zoom Attendance* because several students attend on the same date.  
- **Purpose:** Enables trend analysis over time (daily/weekly/monthly attendance trends).

---

### `DateTable[Date] → Participation[Date]`
- **Type:** One-to-Many (1:*)  
- **Meaning:** Each calendar date can correspond to many participation entries (one per student).  
- **Purpose:** Used for time-based participation analysis.

---

### `DateTable[Date] → Labs & Quizzes[Date]`
- **Type:** One-to-Many (1:*)  
- **Meaning:** A single date in the *Date Table* can relate to many quiz or lab entries for different students.  
- **Purpose:** Enables weekly or monthly performance trend reporting.

---





## Dashboard Capabilities
The Power BI dashboard built from this model enables:  
- **Overall Performance Metrics :** Provide a high-level overview of learner performance, summarizing key metrics for program
stakeholders.  

![Overall](<images/Overall Performance Metrics.png>)


- **Detailed Learner Insights:** Provide detailed insights into individual learner progress and engagement for trainers and
program managers.

![Detailed](<images/Detailed Learner Insights.png>)

---

