# School Management Portal

A full-stack web application designed to manage common academic and administrative activities in an educational institution from a single platform.

The portal brings student management, attendance, project allocation, online fee payments, authentication, and dashboard analytics together in one system. It is built with a role-based approach so that Admins, Teachers, and Students can access the features relevant to them.

## Table of Contents

* [Overview](#overview)
* [Key Features](#key-features)
* [How the Application Works](#how-the-application-works)
* [Application Flow](#application-flow)
* [User Roles](#user-roles)
* [Modules](#modules)
* [Technology Stack](#technology-stack)
* [System Architecture](#system-architecture)
* [Data Flow](#data-flow)
* [Project Structure](#project-structure)
* [Authentication and Security](#authentication-and-security)
* [Payment Flow](#payment-flow)
* [Installation and Setup](#installation-and-setup)
* [Environment Variables](#environment-variables)
* [Running the Project](#running-the-project)
* [Testing](#testing)
* [Project Results](#project-results)
* [Use Cases](#use-cases)
* [Future Enhancements](#future-enhancements)
* [Conclusion](#conclusion)

---

## Overview

Managing students, attendance, projects, and payments manually can become difficult as the number of students and academic activities increases. Data can be scattered across different files, attendance records can take time to maintain, and tracking payments or project allocations becomes harder to manage.

The School Management Portal provides a centralized web-based solution for these tasks.

The application allows authorized users to log in and perform operations based on their role. Admins can manage student information and monitor the overall system, Teachers can manage attendance and academic activities, and Students can view their information, assigned projects, and payment-related details.

The project is designed with a responsive interface and a separate frontend and backend so that the application can be maintained and extended as new requirements are added.

---

## Key Features

* Role-based access for Admin, Teacher, and Student
* Secure login using JWT authentication
* Student management with add, edit, delete, and search/filter operations
* Daily attendance management
* Attendance summaries and reporting
* Project allocation to students or teams
* Project progress tracking
* Online fee payments using Razorpay
* Payment transaction record storage
* Dashboard with student, attendance, payment, and project information
* Charts and analytics using Chart.js
* Responsive user interface
* MongoDB-based data storage
* REST API based communication between frontend and backend

---

## How the Application Works

The application follows a simple client-server flow.

1. A user opens the portal and reaches the login page.
2. The user enters their email and password.
3. The backend verifies the login details.
4. After successful authentication, a JWT token is generated.
5. The user is redirected to the dashboard according to their role.
6. The frontend communicates with the backend through API requests.
7. The backend validates the request and performs the required operation.
8. MongoDB is used to store and retrieve application data.
9. The backend sends the result back to the frontend.
10. The frontend updates the interface and displays the latest information.

For example, when a teacher marks a student as present, the attendance information is sent from the React application to the Node.js API. The backend processes the request and stores the attendance record in MongoDB. The updated attendance information can then be displayed on the dashboard.

---

## Application Flow

```text
                         SCHOOL MANAGEMENT PORTAL
                                  |
                                  v
                           Login / Authentication
                                  |
                                  v
                         JWT Token Verification
                                  |
                                  v
                            Role Identification
                                  |
             +--------------------+--------------------+
             |                    |                    |
             v                    v                    v
           Admin               Teacher              Student
             |                    |                    |
             v                    v                    v
      Student Management    Attendance           Project View
      System Management     Project Activity     Payment
      Dashboard             Dashboard            Dashboard
             |                    |                    |
             +--------------------+--------------------+
                                  |
                                  v
                            Backend REST API
                                  |
                                  v
                              MongoDB
                                  |
                                  +------> Razorpay
```

### Student Management Flow

```text
Admin
  |
  v
Student Form
  |
  v
React Frontend
  |
  v
REST API
  |
  v
Node.js Backend
  |
  v
MongoDB
  |
  v
Updated Student List
```

### Attendance Flow

```text
Teacher
  |
  v
Attendance Page
  |
  v
Select Present / Absent
  |
  v
React Frontend
  |
  v
Attendance API
  |
  v
Node.js Backend
  |
  v
MongoDB
  |
  v
Attendance Summary
```

### Payment Flow

```text
Student
  |
  v
Fee Payment
  |
  v
Razorpay Checkout
  |
  v
Payment Verification
  |
  v
Backend API
  |
  v
MongoDB
  |
  v
Payment Status / Transaction Record
```

---

## User Roles

### Admin

The Admin has access to the main management features of the portal.

Typical responsibilities include:

* Managing student records
* Adding, editing, and deleting student information
* Viewing system-level dashboards
* Monitoring attendance information
* Managing project allocations
* Viewing payment information
* Managing application-level data

### Teacher

Teachers are mainly responsible for academic activities.

Typical responsibilities include:

* Viewing assigned students
* Marking daily attendance
* Checking attendance summaries
* Managing or viewing project-related activities
* Monitoring student progress

### Student

Students can access information related to their own academic activities.

Typical features include:

* Viewing personal information
* Viewing attendance information
* Checking assigned projects
* Viewing project status
* Making online fee payments
* Viewing payment status and transaction information

Access to each feature is controlled by the user's role.

---

## Modules

### 1. Student Management

The Student Management module maintains student information in one place.

Features include:

* Add new students
* Edit student information
* Delete student records
* View the complete student list
* Filter students by batch, team, or program
* Store student information in MongoDB

This makes it easier for administrators to maintain student records without depending on separate files or manual registers.

### 2. Attendance Management

The Attendance module is used to record and monitor daily attendance.

Features include:

* Mark students as Present or Absent
* Automatically record the attendance date and time
* Store attendance records in MongoDB
* View attendance summaries
* Generate or export attendance data
* Track attendance percentage

The module provides teachers with a faster way to maintain attendance and gives administrators a clear view of attendance records.

### 3. Project Allocation

The Project Allocation module helps assign projects to individual students or teams.

Features include:

* Assign a project to a student
* Assign a project to a team
* Select students based on their team
* Store project allocation information
* Track project progress

This keeps project-related information organized and makes it easier to monitor assigned work.

### 4. Payment Management

The Payment module handles online fee payments through Razorpay.

Features include:

* Start an online payment
* Use Razorpay checkout
* Process payment information securely
* Verify payment status through the backend
* Store transaction information in MongoDB
* Display payment status to the user

The payment flow separates the payment provider from the application's own database so that transaction records can be maintained for future reference.

### 5. Dashboard and Analytics

The dashboard provides a quick overview of important information.

It can display:

* Total number of students
* Attendance percentage
* Payment status
* Project distribution
* Academic statistics
* Graphs and visual reports

Chart.js is used to represent relevant information in a more readable format.

### 6. Authentication and Authorization

The authentication module controls access to the application.

Features include:

* Email and password login
* JWT-based authentication
* Role-based authorization
* Protected application routes
* Separate access for Admin, Teacher, and Student

Users are only allowed to access the operations permitted for their role.

---

## Technology Stack

### Frontend Technologies

| Technology    | Purpose                              |
| ------------- | ------------------------------------ |
| React.js      | Building the user interface          |
| Tailwind CSS  | Responsive and utility-based styling |
| Framer Motion | UI animations and page transitions   |
| Chart.js      | Dashboard charts and analytics       |

### Backend Technologies

| Technology | Purpose                                         |
| ---------- | ----------------------------------------------- |
| Node.js    | Running the backend server                      |
| Express.js | Building REST APIs and handling server requests |
| JWT        | Authentication and authorization                |
| Mongoose   | Working with MongoDB from the Node.js backend   |

### Database and Services

| Technology | Purpose                  |
| ---------- | ------------------------ |
| MongoDB    | Storing application data |
| Razorpay   | Online fee payment       |

---

## System Architecture

The application follows a client-server architecture.

```text
+----------------------+
|      User / Client   |
+----------+-----------+
           |
           v
+----------------------+
|    React Frontend    |
| Tailwind / UI / JWT  |
+----------+-----------+
           |
           | HTTP / REST API
           v
+----------------------+
|   Node.js Backend    |
| API / Auth / Logic   |
+----------+-----------+
           |
           v
+----------------------+
|       MongoDB        |
|   Application Data   |
+----------------------+

           |
           v
+----------------------+
|      Razorpay        |
|   Payment Gateway    |
+----------------------+
```

### Request Flow

```text
User Action
    ↓
React Component
    ↓
API Request
    ↓
Node.js / Express Backend
    ↓
Authentication / Authorization
    ↓
Business Logic
    ↓
MongoDB or Razorpay
    ↓
API Response
    ↓
React UI Update
```

---

## Data Flow

### Level 0 DFD

```text
User
  |
  v
School Management Portal
  |
  v
Dashboard / Services
```

### Level 1 DFD

```text
Admin
  |
  +----> Student Management ----> MongoDB
  |
  +----> Dashboard -------------> MongoDB

Teacher
  |
  +----> Attendance ------------> MongoDB
  |
  +----> Project Activity ------> MongoDB

Student
  |
  +----> Project View ----------> MongoDB
  |
  +----> Payment ---------------> Razorpay
                                      |
                                      v
                                   MongoDB
```

---

## Project Structure

A typical project structure can be organized as follows:

```text
school-management-portal/
│
├── frontend/
│   ├── public/
│   └── src/
│       ├── components/
│       ├── pages/
│       ├── layouts/
│       ├── services/
│       ├── context/
│       ├── hooks/
│       ├── assets/
│       └── App.jsx
│
├── backend/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── services/
│   ├── config/
│   ├── utils/
│   └── server.js
│
├── .gitignore
├── README.md
└── package.json
```

The exact folder names can be adjusted according to the implementation, but keeping frontend components, backend routes, models, middleware, and configuration separated makes the project easier to maintain.

---

## Authentication and Security

Authentication is handled using JSON Web Tokens (JWT).

The basic authentication flow is:

```text
Login Request
     |
     v
Backend Checks Credentials
     |
     v
Credentials Valid?
   /       \
 No         Yes
 |           |
 v           v
Error     Generate JWT
             |
             v
       Authenticated User
             |
             v
      Access Protected APIs
```

The backend checks the user's identity before allowing access to protected operations. Role-based authorization is then used to determine whether the user is allowed to perform a particular action.

Sensitive configuration values such as database credentials, JWT secrets, and payment gateway keys should be stored in environment variables rather than directly inside the source code.

---

## Payment Flow

The application uses Razorpay for online fee payments.

```text
Student
   |
   v
Select Fee / Payment
   |
   v
Create Payment Request
   |
   v
Razorpay Checkout
   |
   v
Payment Completed
   |
   v
Backend Verification
   |
   v
Save Transaction Details
   |
   v
Update Payment Status
```

The application maintains the relevant payment information in MongoDB so that the payment history can be displayed later.

---

## Installation and Setup

### Prerequisites

Make sure the following are installed on your system:

* Node.js
* npm
* MongoDB or a MongoDB Atlas database
* Git
* A code editor such as VS Code

### Clone the Repository

```bash
git clone <your-repository-url>
cd school-management-portal
```

### Install Frontend Dependencies

```bash
cd frontend
npm install
```

### Install Backend Dependencies

Open another terminal and run:

```bash
cd backend
npm install
```

---

## Environment Variables

Create a `.env` file inside the backend directory.

Example:

```env
PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret

RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_key_secret
```

Do not commit the `.env` file to GitHub.

Add it to `.gitignore`:

```gitignore
node_modules/
.env
```

Use the variable names required by the actual backend implementation if they differ from the example above.

---

## Running the Project

Start the backend:

```bash
cd backend
npm run dev
```

Start the frontend in another terminal:

```bash
cd frontend
npm run dev
```

The frontend will then connect to the backend API according to the API configuration used in the project.

If the project uses different npm scripts, run the scripts defined in the respective `package.json` files.

---

## Testing

The main modules can be tested using the following scenarios.

| Test Case          | Input                       | Expected Result                                            |
| ------------------ | --------------------------- | ---------------------------------------------------------- |
| Successful Login   | Valid email and password    | User is authenticated and redirected to the dashboard      |
| Invalid Login      | Incorrect password          | Login error is displayed                                   |
| Add Student        | Valid student information   | Student is saved and appears in the list                   |
| Edit Student       | Updated student information | Existing student record is updated                         |
| Delete Student     | Existing student record     | Student is removed from the list                           |
| Mark Attendance    | Present/Absent selection    | Attendance is stored successfully                          |
| Project Allocation | Student/team and project    | Project is assigned successfully                           |
| Payment            | Valid payment request       | Razorpay checkout is opened and payment status is recorded |

API endpoints can also be tested independently using tools such as Postman.

---

## Project Results

After testing the main modules, the application provides a working flow for:

* Managing student information
* Recording attendance
* Allocating projects
* Viewing academic and administrative information
* Processing online payments
* Authenticating users with JWT
* Restricting access based on user roles
* Displaying dashboard statistics
* Working across responsive screen sizes

The separation of frontend, backend, database, and external payment services also provides a foundation for adding more modules in the future.

---

## Use Cases

The portal can be adapted for different types of educational organizations, including:

* Schools
* Colleges
* Coaching institutes
* Skill development centers
* Training programs

The same architecture can be extended with additional roles and modules depending on the institution's requirements.

---

## Future Enhancements

The project can be extended with several additional features:

* Parent portal
* Automated fee reminders
* SMS and email notifications
* Face recognition based attendance
* AI-based performance and learning suggestions
* Teacher performance analytics
* More detailed academic reports
* Advanced notification and communication system

These features can be added without changing the overall client-server architecture of the application.

---

## Conclusion

The School Management Portal provides a centralized way to manage important academic and administrative activities through a single web application.

React is used to build the frontend, while Node.js and Express.js provide the backend APIs and MongoDB stores the application data. JWT handles authentication and role-based access, while Razorpay provides the online payment functionality.

The main focus of the project is to reduce repetitive manual work, keep information organized, and provide different users with the tools they need from one platform.

The modular structure also makes the application easier to maintain and gives it room for future improvements as the requirements of an institution grow.
