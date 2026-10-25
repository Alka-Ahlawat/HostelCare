# HostelCare — Hostel Complaint & Maintenance Management Portal

A Flask web application prototype for student complaint registration, warden/admin management, maintenance staff updates, complaint status tracking, photo attachments, feedback, and analytics.

## 1. Requirements
- Python 3.10 or newer
- VS Code (recommended)
- A modern browser (Chrome/Edge)

SQLite is used by default, so no separate database server is needed. The database file `hostel_portal.db` is created automatically.

## 2. Run in VS Code (Windows)
1. Extract the ZIP file to a folder.
2. Open VS Code → **File → Open Folder** → select `hostel_complaint_portal`.
3. Open **Terminal → New Terminal**.
4. Create a virtual environment:
   ```powershell
   py -m venv .venv
   ```
5. Activate it:
   ```powershell
   .\.venv\Scripts\Activate.ps1
   ```
   If PowerShell blocks activation, use Command Prompt terminal and run:
   ```bat
   .venv\Scripts\activate.bat
   ```
6. Install packages:
   ```powershell
   python -m pip install -r requirements.txt
   ```
7. Start the app:
   ```powershell
   python app.py
   ```
8. Open the local address printed in the terminal, usually `http://127.0.0.1:5000`.

Stop the server with **Ctrl+C** in the terminal.

## 3. Demo accounts
These accounts are created automatically on the first run of a fresh database.

| Role | Email | Password |
|---|---|---|
| Student | `student@hostel.test` | `Student123!` |
| Admin/Warden | `admin@hostel.test` | `Admin123!` |
| Maintenance staff | `staff@hostel.test` | `Staff123!` |

You can also register a new student account from the sign-up page. Demo accounts are for local presentation only.

## 4. Features implemented
- Student registration and login with hashed passwords
- Role-based access for students, admin/warden, and maintenance staff
- Complaint form with category, location, priority, description, and optional photo upload
- Complaint list and detailed status history
- Admin staff assignment and priority/status management
- Staff progress updates and resolution
- Student feedback (1–5 rating) after resolution; feedback closes the complaint
- Analytics: total, pending, resolved, resolution rate, category frequency, average resolution time, repeated locations
- Responsive design for desktop and mobile browser
- SQLite relational database

## 5. Complaint lifecycle
Submitted → Under Review → Assigned → In Progress → Resolved → Closed

The admin can assign a complaint and update its status. Assigned maintenance staff can update work to **In Progress** or **Resolved**. Students can rate the service after resolution, which closes the complaint.

## 6. Test checklist
1. Log in as student and submit a complaint.
2. Log in as admin and open the complaint.
3. Assign the maintenance staff account and set status to Assigned.
4. Log in as staff and update status to In Progress, then Resolved.
5. Log in as student, open the complaint, submit a rating and feedback.
6. Log in as admin and review analytics and complaint history.
7. Try an unsupported photo format or incomplete form to verify validation.

## 7. Project scope / limitations
- This is an academic prototype. It does not send real email/SMS notifications.
- AI-based classification is a future enhancement; categories are selected by the student.
- The analytics are calculated from the prototype's database records.
- Photo upload is restricted by file extension and size for a classroom demo; production deployments need stronger file validation and malware scanning.
- For deployment, set a strong random `SECRET_KEY`, turn off Flask debug mode, use HTTPS, configure backups, and consider migrating to MySQL.

## 8. Suggested future enhancements
- Email/SMS notifications
- AI-based complaint category prediction
- MySQL deployment
- Android/iOS application
- Exportable analytics reports
- More advanced duplicate-complaint detection
