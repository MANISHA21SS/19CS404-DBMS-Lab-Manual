# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:

<img width="992" height="640" alt="Screenshot 2025-09-23 191451" src="https://github.com/user-attachments/assets/d6803128-4626-45f9-ad5c-ec54c1a65fd4" />


### Entities and Attributes

<img width="912" height="552" alt="Screenshot 2025-09-23 191756" src="https://github.com/user-attachments/assets/69ba6409-5a27-4351-8946-33dde6bc2eb7" />


### Relationships and Constraints

<img width="913" height="549" alt="Screenshot 2025-09-23 191810" src="https://github.com/user-attachments/assets/728dcfea-90ca-486b-9a69-d960e9114b40" />


### Assumptions

A member must enroll in at least one program.

A program must be led by at least one trainer.

Payments are tied to members and programs (not to trainers directly).

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
  
<img width="803" height="642" alt="Screenshot 2025-09-23 192200" src="https://github.com/user-attachments/assets/c9e4355c-f3f5-470e-9379-5cb815a36104" />

### Entities and Attributes

<img width="924" height="411" alt="Screenshot 2025-09-23 192220" src="https://github.com/user-attachments/assets/665e76c8-5eef-4216-9a15-5ba95b5b6c66" />


### Relationships and Constraints

<img width="924" height="424" alt="Screenshot 2025-09-23 192237" src="https://github.com/user-attachments/assets/124508a1-79b6-4850-881a-aeed9dbb98c3" />


### Assumptions

A member must exist before borrowing books or registering for events.

A book may or may not be borrowed; not all books will always have loans.

Fines are only generated if a book is returned late.

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
 
<img width="763" height="786" alt="Screenshot 2025-09-23 192323" src="https://github.com/user-attachments/assets/c2e519d0-3ea9-4cc7-96d4-6f491fcc6101" />


### Entities and Attributes

<img width="909" height="332" alt="Screenshot 2025-09-23 192335" src="https://github.com/user-attachments/assets/f239fb79-5de0-4536-8268-1f9d4b216a7c" />
<img width="918" height="125" alt="Screenshot 2025-09-23 192349" src="https://github.com/user-attachments/assets/4e22300c-0908-4e39-8aa3-a7c5a0c7ba98" />


### Relationships and Constraints

<img width="923" height="536" alt="Screenshot 2025-09-23 192403" src="https://github.com/user-attachments/assets/e23b42c5-5262-47aa-bcfe-7b7ff0c6879c" />


### Assumptions

A customer may exist without making a reservation or placing an order.

A reservation must be tied to both a customer and a restaurant.

Every order must belong to a customer and a restaurant.

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
