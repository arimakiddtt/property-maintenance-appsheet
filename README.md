🏢 Property Maintenance App (Google AppSheet)
This repository demonstrates the backend design and configuration strategy behind a low-code Property Maintenance application built using Google AppSheet and Google Sheets. The app supports maintenance tracking, vendor management, asset logging, and job diaries—designed for property departments or facilities teams.

⚠️ Access to Live App
The live demo app is not publicly accessible to avoid misuse and unauthorized cloning.
Serious inquiries only — please contact me via LinkedIn and include your email address if you'd like access.

🚀 Purpose
This project showcases my ability to:
Design relational datastores in Google Sheets
Develop functional low-code applications
Implement flexible RBAC security models
Leave scalable hooks for future features
Rather than providing a plug-and-play app, this repo aims to demonstrate my approach to data modeling, permissions, and architecture that can scale with any property team or organization.

🗂️ Google Sheets Datastore Structure
The app is powered by a series of interlinked Google Sheets, each functioning like a table in a traditional relational database. Foreign key relationships are handled using common column names (e.g., Job-ID, Location-ID).

🧱 Core Tables:
🔧 Jobs
Tracks job details, scheduling, costs, vendors, and PO dependencies.

📆 Job Diary
Logs ongoing work activity per job, allowing for multi-day or multi-vendor workflows.

🛠️ Maintenance
Defines categories such as Preventative, Emergency, Warranty, etc. for reporting and trend tracking.

🗺️ Location
Catalogs all geographic locations or work zones for maintenance activities.

💼 Assets
Logs company assets tied to jobs. Useful for tracking recurring maintenance or failure rates.

🧑‍🔧 Vendors
Stores contact details for contractors or service providers.

📢 Report Issue (Planned / Open for Implementation)
Supports crowd-sourced issue reporting with image uploads and location tagging. Sheet is modeled but frontend is left for the implementer.

🛡️ RBAC (Open Design Template)
Provides a scaffold for Role-Based Access Control via expressions or sheet rules, adaptable to the admin's needs.

🔐 Role-Based Access Control (RBAC)
While RBAC is not hardcoded, it is intentionally left open for extension via:

Expression-based UI rules:
OR(([Logged By]=USEREMAIL()), (USEREMAIL() = "<adminEmail>"))

Table-level access control using:
SWITCH(USEREMAIL(), 
    "<adminEmail>", "ALL_CHANGES",
    "<readonlyEmail>", "READ_ONLY")

Sheet-based lookup permissions:
SWITCH(
  LOOKUP(USEREMAIL(), "RBAC", "Email", "Score"), 
  0, "ALL_CHANGES", 
  1, "ALL_CHANGES", 
  2, "ADDS_AND_UPDATES", 
  "READ_ONLY")
  
Admins and developers are free to design their preferred enforcement logic.

🖼️ Screenshots & Media
Coming soon.

Visual walkthroughs, UI screenshots, and demo videos will be added to this repo shortly.

💡 Implementation Notes
Media upload paths (e.g., PO documents or reported issues) are not hardcoded; implementers can configure their preferred Drive folders.

Several features like Issue Reporting and RBAC logic are not fully implemented on purpose — providing room for growth and adaptation.

The structure here is meant to showcase thought leadership in app design, not to be copy-pasted into production.

🧠 Why This Project?
I built this to demonstrate:
My real-world experience with Google AppSheet and relational design
How low-code platforms can be extended with thoughtful architecture
That I can deliver practical, scalable solutions without unnecessary complexity
