# SQL_project

# 🎓 Student Management System (SQLite + DB Browser)

A beginner-friendly database project built with **SQLite**, designed and tested using **DB Browser for SQLite**.  
This project manages **Students, Courses, and Enrollments** with realistic queries and reporting views.  

---

## 📂 Project Files
- `student_mgmt.sqlite` → Complete database file (can be opened directly in DB Browser for SQLite).  
- `schema.sql` → Table creation scripts (Students, Courses, Enrollments + views).  
- `data.sql` → Sample data inserts for testing.  
- `queries.sql` → Useful practice queries (joins, grouping, aggregates, reports).  
- `README.md` → Documentation (this file).  

---

## 🗂️ Database Schema

**Tables:**
- `Students(student_id, name, age, department)`  
- `Courses(course_id, course_code, course_name, credits, department)`  
- `Enrollments(enrollment_id, student_id → Students, course_id → Courses, semester, grade, enrollment_date)`  

**Views:**
- `v_student_courses` → Lists student-course-grade details.  
- `v_student_gpa` → Calculates GPA per student (based on A=10, B=8, C=6, D=4, F=0).  

---

## 📝 Sample Queries

### 1. List all students
```sql
SELECT * FROM Students;
```

### 2. Courses taken by Kavya
```
SELECT s.name, c.course_name, e.grade
FROM Students s
JOIN Enrollments e ON s.student_id = e.student_id
JOIN Courses c ON e.course_id = c.course_id
WHERE s.name = 'Kavya';
```

### 3. Students per department
```
SELECT department, COUNT(*) AS total_students
FROM Students
GROUP BY department;
```

### 4. GPA per student (using view)
```
SELECT * FROM v_student_gpa ORDER BY gpa DESC;
```

### 5. Top 5 courses by enrollment
```
SELECT c.course_code, c.course_name, COUNT(*) AS enroll_count
FROM Enrollments e
JOIN Courses c ON c.course_id = e.course_id
GROUP BY c.course_id
ORDER BY enroll_count DESC
LIMIT 5;
```
## Output:
### Database Schema / Structure
<img width="1919" height="969" alt="Screenshot 2025-08-24 004458" src="https://github.com/user-attachments/assets/264c91b1-4bcf-4fd1-996e-19e5cf46be88" />

### Tables with Data
<img width="306" height="846" alt="Screenshot 2025-08-24 004826" src="https://github.com/user-attachments/assets/13eb9731-2d7c-4fea-a6cf-c63fca86ebfa" />
<img width="578" height="340" alt="Screenshot 2025-08-24 004805" src="https://github.com/user-attachments/assets/f686af4e-4153-486b-a547-f7b45bdd8877" />
<img width="551" height="465" alt="Screenshot 2025-08-24 004838" src="https://github.com/user-attachments/assets/edcefa9b-fb82-4c62-913e-8ebf07a3bdf2" />

### SQL Queries in Action
<img width="1179" height="967" alt="Screenshot 2025-08-24 004721" src="https://github.com/user-attachments/assets/f8762fee-c699-4593-bd8d-b73bbec31a52" />
<img width="1333" height="950" alt="Screenshot 2025-08-24 004748" src="https://github.com/user-attachments/assets/6978adbe-7efb-4cb5-ae2f-c4ddd3746710" />


## Result

This project is part of my learning journey into Databases & SQL for roles like Data Analyst and QA Engineer.








