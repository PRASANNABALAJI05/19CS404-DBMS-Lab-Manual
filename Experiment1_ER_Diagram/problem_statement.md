#  ER Diagram Workshop – Submission

##  Objective
To understand and apply **Entity-Relationship (ER) modeling** concepts by creating ER diagrams for real-world applications.

##  Purpose
This workshop provides hands-on experience in designing ER diagrams that represent **database structure**, including:
- Entities
- Relationships
- Attributes
- Constraints  

---

##  Scenario A: City Fitness Club Management

###  Business Context
FlexiFit Gym wants a database to manage its **members, trainers, and fitness programs**.

###  Requirements
- Members register with **name, membership type, and start date**.  
- Each member can join **multiple programs** (Yoga, Zumba, Weight Training).  
- Trainers are **assigned to programs**; a program may have multiple trainers.  
- Members may **book personal training sessions** with trainers.  
- **Attendance** recorded for each session.  
- **Payments** tracked for memberships and sessions.  

###  ER Diagram
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/dd0dea62-afe0-4f27-8544-dbd46a672b4b" />

### Entities and Attributes
| Entity   | Attributes (PK, FK) | Notes |
|----------|----------------------|-------|
| Member   | MemberID (PK), Name, MembershipType, StartDate | Registers for programs |
| Program  | ProgramID (PK), Name, Type | Yoga, Zumba, etc. |
| Trainer  | TrainerID (PK), Name, Specialization | Assigned to programs |
| Session  | SessionID (PK), Date, Time, MemberID (FK), TrainerID (FK) | Personal training |
| Payment  | PaymentID (PK), Amount, Date, MemberID (FK), Type | Membership/session |

###  Relationships and Constraints
| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Member–Program | M:N | Total | A member can join many programs |
| Program–Trainer | M:N | Partial | Trainers assigned to programs |
| Member–Trainer (Personal Session) | M:N | Partial | Booked sessions |
| Session–Attendance | 1:N | Total | Tracks presence |
| Member–Payment | 1:N | Total | Payments for membership & sessions |

###  Assumptions
- Each session involves **one member and one trainer**.  
- Membership type determines validity period (not modeled in ER).  
- Payments linked either to membership or personal training.  

---

##  Scenario B: City Library Event & Book Lending System

###  Business Context
The Central Library wants to manage **book lending and cultural events**.

###  Requirements
- Members borrow books, with **loan and return dates tracked**.  
- Each book has **title, author, and category**.  
- Library organizes **events**; members can register.  
- Each event has **one or more speakers/authors**.  
- **Rooms** are booked for events and study.  
- **Overdue fines** apply for late returns.  

### 🖼 ER Diagram
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/6b44d1a3-1c39-43e8-a9d4-9c9331fe910e" />


###  Entities and Attributes
| Entity   | Attributes (PK, FK) | Notes |
|----------|----------------------|-------|
| Member   | MemberID (PK), Name, Contact | Registers & borrows books |
| Book     | BookID (PK), Title, Author, Category | Lending unit |
| Loan     | LoanID (PK), LoanDate, ReturnDate, MemberID (FK), BookID (FK) | Tracks borrow |
| Event    | EventID (PK), Name, Date | Library event |
| Speaker  | SpeakerID (PK), Name, Expertise | Linked to events |
| Room     | RoomID (PK), RoomNo, Capacity | Used for events/study |
| Fine     | FineID (PK), Amount, LoanID (FK) | Late returns |

###  Relationships and Constraints
| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Member–Loan | 1:N | Total | Each loan belongs to a member |
| Book–Loan | 1:N | Total | Each loan involves one book |
| Event–Member | M:N | Partial | Members register for events |
| Event–Speaker | M:N | Total | Multiple speakers per event |
| Event–Room | 1:1 | Total | Each event held in a room |
| Loan–Fine | 1:1 | Partial | Fine only if overdue |

###  Assumptions
- A book can only be borrowed by **one member at a time**.  
- Event rooms cannot host **multiple events simultaneously**.  
- Fines calculated externally (not within ER).  

---

##  Scenario C: Restaurant Table Reservation & Ordering

###  Business Context
A popular restaurant wants to manage **reservations, orders, and billing**.

###  Requirements
- Customers can **reserve tables** or walk in.  
- Each reservation includes **date, time, number of guests**.  
- Customers place **food orders linked to reservations**.  
- Each order contains **multiple dishes**; dishes belong to **categories** (starter, main, dessert).  
- **Bills** generated per reservation, including food and service charges.  
- **Waiters** assigned to serve reservations.  

###  ER Diagram
![WhatsApp Image 2025-08-29 at 14 35 17_70104f15](https://github.com/user-attachments/assets/a20b22a6-154f-4287-be24-9239a5bfd22e)

###  Entities and Attributes
| Entity    | Attributes (PK, FK) | Notes |
|-----------|----------------------|-------|
| Customer  | CustomerID (PK), Name, Contact | Makes reservations |
| Reservation | ReservationID (PK), Date, Time, Guests, CustomerID (FK), TableID (FK) | Booking info |
| Table     | TableID (PK), Capacity, Location | Dining tables |
| Order     | OrderID (PK), ReservationID (FK), Time | Linked to reservations |
| Dish      | DishID (PK), Name, Category, Price | Ordered item |
| OrderDetail | OrderID (FK), DishID (FK), Quantity | Resolves M:N |
| Bill      | BillID (PK), ReservationID (FK), Amount, ServiceCharge | Final payment |
| Waiter    | WaiterID (PK), Name | Assigned to reservations |

###  Relationships and Constraints
| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Customer–Reservation | 1:N | Partial | A customer can have multiple reservations |
| Reservation–Table | 1:1 | Total | One reservation per table |
| Reservation–Order | 1:N | Total | Orders linked to reservation |
| Order–Dish | M:N | Total | Resolved using OrderDetail |
| Reservation–Bill | 1:1 | Total | One bill per reservation |
| Reservation–Waiter | 1:1 | Partial | Assigned waiter |

###  Assumptions
- Each reservation **occupies one table** only.  
- Bills always generated **per reservation**.  
- Service charges fixed percentage (not modeled).  

---
### ER DIAGRAM SUBMISSION
- Name: PRASANNA BALAJI B
- Reg no: 212223060203
---
##  Instructions for Students
1. Complete **all three scenarios (A, B, C)**.  
2. Identify **entities, relationships, and attributes** for each scenario.  
3. Draw ER diagrams using **draw.io / diagrams.net** (or hand-drawn & scanned).  
4. Fill in **Entities, Relationships, Assumptions** tables.  
5. Export the completed Markdown (with diagrams) as a **single PDF**.  

---

👨‍💻 *End of Submission Template*
