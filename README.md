# Medical_Diagnosis_Center-ServiceNow-
A ServiceNow-based Diagnostic Test Center Portal built with Service Portal to simplify diagnostic test discovery, appointment booking, slot management, payments, reporting, notifications, and role-based healthcare administration.
Diagnostic Test Center Portal


Access my demo link:
https://drive.google.com/file/d/1nZYS3ciW2QUOlqmOfZrqKZxr4HoCUzlB/view?usp=sharing


The Diagnostic Test Center Portal is a custom application built on the ServiceNow platform using Service Portal. It helps patients find diagnostic tests, book appointments, arrange sample collection, complete payments, and track their medical reports in one place.

🚀 Features
Browse available diagnostic tests and packages
Book appointments for preferred dates and time slots
Request home sample collection
Check slot availability in real time
Calculate prices and discounts automatically
Confirm payments through a defined workflow
Cancel or reschedule appointments
Send automated email notifications
Upload and track medical reports
Send appointment reminders
Update appointment statuses through scheduled jobs
Control access based on user roles and ACLs
Assign and manage lab technicians
Manage tests, pricing, slots, and workflows through an admin interface
🛠️ Technologies Used
ServiceNow
Service Portal
Flow Designer
Business Rules
Client Scripts
UI Policies
ACLs
Scheduled Jobs
Notifications
Custom Tables and Forms
Glide Scripting
👥 User Roles
Patient

Patients can:

Browse diagnostic tests and packages
Book appointments
Choose available time slots
Confirm payments
Cancel or reschedule appointments
Track appointment and report statuses
Lab Technician

Lab technicians can:

View their assigned appointments
Manage sample collection
Update test processing statuses
Upload completed diagnostic reports
Administrator

Administrators can:

Manage the diagnostic test catalog
Set prices and discounts
Create and manage appointment slots
Assign technicians
Configure workflows
Manage diagnostic records and system settings
🔄 Appointment Lifecycle

Requested → Scheduled → Sample Collected → Processing → Report Ready → Completed

The system can also identify missed appointments and update their status automatically through scheduled background jobs.

⚙️ Automation

Flow Designer manages key processes such as booking validation, payment confirmation, administrative approvals, appointment updates, and notifications.

Scheduled Jobs handle background tasks, including appointment status updates and missed-appointment processing.

Business Rules and Client Scripts support record validation, automatic updates, and dynamic behavior throughout the portal.

🔐 Security

Role-based Access Control Lists (ACLs) restrict access to records and actions based on each user's role. This helps ensure that patients, technicians, and administrators can only view or modify the information relevant to them.

🎯 Objective

The goal of this project is to provide a centralized diagnostic test management platform that makes appointment scheduling easier, reduces manual administrative work, prevents slot overbooking, and gives patients a clear way to track their appointments and medical reports.

📌 Project Highlights
Complete diagnostic appointment management
Workflow-based test and appointment processing
Real-time slot availability checks
Automatic billing and discount calculation
Automated email notifications and reminders
Secure role-based access
Centralized administration
Automatic appointment lifecycle tracking
👨‍💻 Platform

ServiceNow Application Development with Service Portal
