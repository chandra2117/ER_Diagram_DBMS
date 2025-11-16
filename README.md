# ER Diagram Workshop
## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

# Scenario A: City Fitness Club Management
#### Business Context:
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

#### Requirements:

  - Members register with name, membership type, and start date.
  - Each member can join multiple programs (Yoga, Zumba, Weight Training).
  - Trainers assigned to programs; a program may have multiple trainers.
  - Members may book personal training sessions with trainers.
  - Attendance recorded for each session.
  - Payments tracked for memberships and sessions.
### ER Diagram:

<img width="732" height="805" alt="image" src="https://github.com/user-attachments/assets/00f7be05-84f9-4d6e-8a1f-4302c5294767" />

## Entities and Attributes
<table>
  <tr>
    <th>Entity</th>
    <th>Attributes(PK, FK)</th>
    <th>Notes</th>
  </tr>
  <tr>
    <td>Member</td>
    <td>MemberID,Membership</td>
    <td>Store member details</td>
  </tr>
  <tr>
    <td>Trainer</td>
    <td>TrainerID,Name,Email,PhoneNumber</td>
    <td>Store Trainer details</td>
  </tr>
  <tr>
    <td>Program</td>
    <td>ProgramID,Cost</td>
    <td>Programs like Zumbz/yoga</td>
  </tr>
  <tr>
    <td>Session</td>
    <td>SessionID,SessionDate</td>
    <td>Tracks attendance</td>
  </tr>
  <tr>
    <td>Payment</td>
    <td>PaymentID,Amount</td>
    <td>Tracks payments by members</td>
  </tr>             
</table>

## Relationships and Constraints
<table>
  <tr>
    <th>Relationship</th>
    <th>Cardinality</th>
    <th>Participation</th>
    <th>Notes</th>
  </tr>
  <tr>
    <td>Member-Program</td>
    <td>M:N</td>
    <td>Optional(Member),Mandatory(Enrollment)</td>
    <td>Member may or may not join programs</td>
  </tr>
  <tr>
    <td>Trainer-Program</td>
    <td>M:N</td>
    <td>Optional(Trainer),Mandatory(Assignment)</td>
    <td>Trainer may or may not run Programs</td>
  </tr>
  <tr>
    <td>Member–Trainer</td>
    <td>1:N</td>
    <td>Mandatory (Session), Optional (Member/Trainer)</td>
    <td>Session must have a member & trainer</td>
  </tr>
</table>

## Assumptions
  - Program = recurring class; Session = specific instance.
  - Payments cover both memberships and sessions.
  - A Session links one Member and one Trainer.

# Scenario B: City Library Event & Book Lending System
#### Business Context:
The Central Library wants to manage book lending and cultural events.

#### Requirements:
  - Members borrow books, with loan and return dates tracked.
  - Each book has title, author, and category.
  - Library organizes events; members can register.
  - Each event has one or more speakers/authors.
  - Rooms are booked for events and study.
  - Overdue fines apply for late returns.
    
## ER Diagram:

<img width="647" height="763" alt="image" src="https://github.com/user-attachments/assets/96e450a1-9210-4cda-aa04-6f42ce76b1c4" />

## Entities and Attributes
<table>
  <tr>
    <th>Entity</th>
    <th>Attributes(PK, FK)</th>
    <th>Notes</th>
  </tr>
  <tr>
    <td>Member</td>
    <td>MemberID (PK), Name, Address, Phone, Email</td>
    <td>Library members</td>
  </tr>
  <tr>
    <td>Book</td>
    <td>BookID (PK), Title, Author, Category, ISBN, PubYear</td>
    <td>Books in collection</td>
  </tr>
  <tr>
    <td>Loan</td>
    <td>LoanID (PK), LoanDate, DueDate, ReturnDate, FineAmount, MemberID (FK), BookID (FK)</td>
    <td>Tracks book borrowing</td>
  </tr>
  <tr>
    <td>Speaker</td>
    <td>SpeakerID (PK), Name, Bio, ContactInfo</td>
    <td>Event speakers/authors</td>
  </tr>
  <tr>
    <td>Booking</td>
    <td>BookingID (PK), BookingDate, StartTime, EndTime, RoomID (FK), MemberID (FK)</td>
    <td>Study room reservations</td>
  </tr>             
</table>

## Relationships and Constraints
<table>
  <tr>
    <th>Relationship</th>
    <th>Cardinality</th>
    <th>Participation</th>
    <th>Notes</th>
  </tr>
  <tr>
    <td>Member–Book</td>
    <td>M:N</td>
    <td>Mandatory for Loan, Optional for Member/Book</td>
    <td>Members borrow books</td>
  </tr>
  <tr>
    <td>Member–Event</td>
    <td>M:N</td>
    <td>Mandatory for Registration, Optional for Member/Event</td>
    <td>Members register for events</td>
  </tr>
  <tr>
    <td>Event–Speaker</td>
    <td>M:N</td>
    <td>Mandatory for EventSpeaker, Optional for Event/Speaker</td>
    <td>Events may have multiple speakers</td>
  </tr>
  <tr>
    <td>Event–Room</td>
    <td>1:N</td>
    <td>Mandatory for Event, Optional for Room</td>
    <td>Each event in one room</td>
  </tr>
  <tr>
    <td>Room–Booking</td>
    <td>1:N</td>
    <td>Mandatory for Booking, Optional for Room</td>
    <td>Rooms booked for study by members</td>
  </tr>
</table>
	
## Assumptions
  - Overdue fines are stored per Loan record.
  - BookCopy not modeled
  - Rooms serve both events and study bookings.
    
# Scenario C: Restaurant Table Reservation & Ordering
#### Business Context:
A popular restaurant wants to manage reservations, orders, and billing.

#### Requirements:

Customers can reserve tables or walk in.
Each reservation includes date, time, and number of guests.
Customers place food orders linked to reservations.
Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).
Bills generated per reservation, including food and service charges.
Waiters assigned to serve reservations.
## ER Diagram:

<img width="598" height="744" alt="image" src="https://github.com/user-attachments/assets/986b56ea-3e24-467d-a6ef-e61f2059079d" />

### Entities and Attributes
<table>
  <tr>
    <th>Entity</th>
    <th>Attributes (PK, FK)</th>
    <th>Notes</th>
  </tr>
  <tr>
    <td>Customer</td>
    <td>CustomerID (PK), Name, Email, Phone</td>
    <td>Stores customer info</td>
  </tr>
  <tr>
    <td>Waiter</td>
    <td>WaiterID (PK), Name, Shift, ContactInfo</td>
    <td>Waiter details</td>
  </tr>
  <tr>
    <td>Table</td>
    <td>TableID (PK), TableNumber, Capacity, Location</td>
    <td>Restaurant tables</td>
  </tr>
  <tr>
    <td>Reservation</td>
    <td>ReservationID (PK), ReservationDate, ReservationTime, NoOfGuests, Status, CustomerID (FK), TableID (FK)</td>
    <td>Table bookings</td>
  </tr>
  <tr>
    <td>Order</td>
    <td>OrderID (PK), OrderDate, OrderTime, Status, ReservationID (FK)</td>
    <td>Orders linked to reservations</td>
  </tr>
  <tr>
    <td>Dish</td>
    <td>DishID (PK), DishName, Description, Price, CategoryID (FK)</td>
    <td>Menu items</td>
  </tr>
  <tr>
    <td>Bill</td>
    <td>BillID (PK), BillDate, TotalAmount, ServiceCharge, Tax, Status, ReservationID (FK)</td>
    <td>Final bill per reservation</td>
  </tr>
  <tr>
    <td>Assignment</td>
    <td>AssignmentID (PK), WaiterID (FK), ReservationID (FK)</td>
    <td>Resolves Waiter–Reservation</td>
  </tr>
</table>

### Relationships and Constraints
<table>
  <tr>
    <th>Relationship</th>
    <th>Cardinality</th>
    <th>Participation</th>
    <th>Notes</th>
  </tr>
  <tr>
    <td>Customer–Reservation</td>
    <td>1:N</td>
    <td>Mandatory for Reservation, Optional for Customer</td>
    <td>One customer can have many reservations</td>
  </tr>
  <tr>
    <td>Reservation–Table</td>
    <td>1:N</td>
    <td>Mandatory for Reservation, Optional for Table</td>
    <td>Each reservation is for one table</td>
  </tr>
  <tr>
    <td>Order–Dish</td>
    <td>M:N</td>
    <td>Mandatory for Order_Item, Optional for Order/Dish</td>
    <td>An order can include many dishes</td>
  </tr>
  <tr>
    <td>Reservation–Bill</td>
    <td>1:1</td>
    <td>Mandatory for Bill, Optional for Reservation</td>
    <td>One bill per reservation</td>
  </tr>
  <tr>
    <td>Waiter–Reservation</td>
    <td>M:N</td>
    <td>Mandatory for Assignment, Optional for Waiter/Reservation</td>
    <td>Multiple waiters can serve a reservation</td>
  </tr>
</table>


## Assumptions
  - Walk-in customers are still recorded
  - One bill per reservation
  - Split payments not modeled; could extend with a Payment entity.
## Instructions for Students
  - Complete all three scenarios (A, B, C).
  - Identify entities, relationships, and attributes for each.
  - Draw ER diagrams using draw.io / diagrams.net or hand-drawn & scanned.
  - Fill in all tables and assumptions for each scenario.
  - Export the completed Markdown (with diagrams) as a single PDF
