# SOFTWARE REQUIREMENT SPECIFICATION (SRS)
## Security Incident Mapping (SIM) Platform

---

## 1. INTRODUCTION

### 1.1 Purpose
The purpose of this document is to provide a detailed Software Requirement Specification (SRS) for the **Security Incident Mapping (SIM)** platform. This system is designed to enable students, staff, and landlords on campus to report security incidents quickly, anonymously, and efficiently. The platform aims to reduce campus crime by increasing reporting rates, improving situational awareness, and providing actionable data to campus security units.

### 1.2 Scope
The SIM platform is a web-based application that allows:
- Students and campus residents to report incidents (theft, assault, rape, murder, etc.)
- Users to view a map of reported incidents (anonymized)
- Users to track the status of their reports using a reference number
- Security personnel to manage and respond to reports
- Administrators to generate analytics and manage users

The system is designed as a Minimum Viable Product (MVP) for the SEN202 Weekend 1 assignment. Future iterations may include mobile apps, SMS integration, and real-time notifications.

### 1.3 Definitions, Acronyms, and Abbreviations

| Term | Definition |
|------|------------|
| **SIM** | Security Incident Mapping – the platform name |
| **Incident** | Any crime or security threat (theft, assault, rape, murder, vandalism, etc.) |
| **Anonymous Report** | A report submitted without any personally identifiable information |
| **Stakeholder** | Any person with an interest in the system (students, staff, landlords, security) |
| **MVP** | Minimum Viable Product – the simplest working version |
| **SRS** | Software Requirement Specification |
| **FR** | Functional Requirement |
| **NFR** | Non-Functional Requirement |
| **Admin** | System administrator with full access rights |
| **Security Unit** | Campus security personnel who manage incident responses |

### 1.4 References
- SEN202 Weekend 1 Assignment Brief (July 2026)
- Ishikawa Problem Analysis Diagram
- Use-Case Diagram
- Google Form Questionnaire Responses

---

## 2. OVERALL DESCRIPTION

### 2.1 Product Perspective
The SIM platform is a standalone web-based system. It operates independently but may integrate with external services in future versions (e.g., Google Maps API, SMS gateways, campus security databases). The current version uses browser localStorage for data persistence, eliminating the need for a backend server during the demonstration phase.

### 2.2 User Characteristics

| User Type | Description | Technical Skill Level |
|-----------|-------------|----------------------|
| **Student** | Primary users; report incidents and view maps | Basic (can use web forms) |
| **Security Unit** | Campus security personnel; manage and respond to reports | Basic to Intermediate |
| **Admin** | System administrators; manage users and generate analytics | Intermediate |
| **Landlord** | Off-campus housing providers; secondary stakeholders | Basic |

### 2.3 Operating Environment
- **Hardware:** Any computer or mobile device with a modern web browser
- **Software:** HTML5-compliant browser (Chrome, Firefox, Safari, Edge)
- **Network:** Internet connection required for initial access (offline capability planned for future)
- **Display:** Responsive design supports screen sizes from 320px to 1920px

### 2.4 Design and Implementation Constraints

| Constraint | Description |
|------------|-------------|
| **Technology** | Must be built with HTML, CSS, and JavaScript only (no backend for MVP) |
| **Budget** | Zero-cost solution using open-source tools |
| **Time** | Complete within assignment deadline (July 10, 2026) |
| **Data Storage** | localStorage for demo; no database required |
| **Browser Support** | Must work on modern browsers (no IE support) |
| **Security** | No sensitive data stored; HTTPS recommended for production |

### 2.5 Assumptions and Dependencies

**Assumptions:**
- Users have basic literacy and can fill out forms
- Users have access to a device with internet connection
- Campus security is willing to use the system
- Reports are submitted in good faith
- The campus has identified security points of contact

**Dependencies:**
- Google Forms for questionnaire data collection
- draw.io for diagram creation
- GitHub for version control and submission
- Leaflet.js (future) for interactive maps

---

## 3. FUNCTIONAL REQUIREMENTS (FR)

### 3.1 User Management

| ID | Requirement | Priority | Actor |
|----|-------------|----------|-------|
| FR1 | System shall allow users to view the platform without login (public view) | High | All |
| FR2 | System shall allow Admin to view all users | Medium | Admin |
| FR3 | System shall allow Admin to add/remove users | Medium | Admin |
| FR4 | System shall allow Admin to assign roles (student, security, admin) | Medium | Admin |

### 3.2 Incident Reporting

| ID | Requirement | Priority | Actor |
|----|-------------|----------|-------|
| FR5 | System shall allow users to submit incident reports | High | Student |
| FR6 | System shall capture crime type (dropdown) | High | Student |
| FR7 | System shall capture location (text input) | High | Student |
| FR8 | System shall capture incident description (textarea) | High | Student |
| FR9 | System shall allow users to submit reports anonymously (checkbox) | High | Student |
| FR10 | System shall automatically generate a unique reference number | High | System |
| FR11 | System shall timestamp each report automatically | High | System |
| FR12 | System shall auto-assign status "Pending" to new reports | Medium | System |

### 3.3 Incident Mapping

| ID | Requirement | Priority | Actor |
|----|-------------|----------|-------|
| FR13 | System shall display reported incidents on a map | High | Student, Security |
| FR14 | System shall show incident locations as markers | Medium | Student, Security |
| FR15 | System shall allow map zoom and pan | Low | Student, Security |
| FR16 | System shall hide exact addresses for anonymous reports | High | System |

### 3.4 Report Tracking

| ID | Requirement | Priority | Actor |
|----|-------------|----------|-------|
| FR17 | System shall allow users to check report status using reference number | Medium | Student |
| FR18 | System shall display report status (Pending, In Progress, Resolved) | Medium | Student, Security |

### 3.5 Report Management (Security)

| ID | Requirement | Priority | Actor |
|----|-------------|----------|-------|
| FR19 | System shall allow Security to view all reports | High | Security |
| FR20 | System shall allow Security to update report status | High | Security |
| FR21 | System shall allow Security to add comments to reports | Medium | Security |
| FR22 | System shall allow Security to filter reports by status or type | Low | Security |

### 3.6 Analytics (Admin)

| ID | Requirement | Priority | Actor |
|----|-------------|----------|-------|
| FR23 | System shall allow Admin to view incident statistics | Medium | Admin |
| FR24 | System shall allow Admin to generate reports by crime type | Low | Admin |
| FR25 | System shall allow Admin to generate reports by location | Low | Admin |
| FR26 | System shall allow Admin to export analytics data | Low | Admin |

### 3.7 System Administration

| ID | Requirement | Priority | Actor |
|----|-------------|----------|-------|
| FR27 | System shall allow Admin to delete inappropriate reports | High | Admin |
| FR28 | System shall allow Admin to manage user roles | Medium | Admin |
| FR29 | System shall allow Admin to view system logs | Low | Admin |
| FR30 | System shall allow Admin to backup data | Low | Admin |

---

## 4. NON-FUNCTIONAL REQUIREMENTS (NFR)

### 4.1 Performance

| ID | Requirement | Metric |
|----|-------------|--------|
| NFR1 | Page load time should be fast | < 3 seconds |
| NFR2 | Form submission should be responsive | < 2 seconds |
| NFR3 | System should support concurrent users | 1000 users |
| NFR4 | Map rendering should be smooth | 60 fps |

### 4.2 Security

| ID | Requirement | Implementation |
|----|-------------|----------------|
| NFR5 | All data transmission must be encrypted | HTTPS (production) |
| NFR6 | Anonymous reports must not store IP addresses | No IP tracking |
| NFR7 | User passwords must be hashed | bcrypt (future) |
| NFR8 | Role-based access control | Admin, Security, Student |
| NFR9 | No sensitive data stored in localStorage | Reports limited to non-PII |

### 4.3 Usability

| ID | Requirement | Implementation |
|----|-------------|----------------|
| NFR10 | Interface must be intuitive and user-friendly | Clear labels, logical flow |
| NFR11 | Platform must be mobile-responsive | Bootstrap or custom CSS media queries |
| NFR12 | Forms should provide validation feedback | Inline validation, error messages |
| NFR13 | Language should be simple and accessible | Primary: English; avoid jargon |
| NFR14 | Accessibility standards | WCAG 2.1 compliant (AA level) |

### 4.4 Availability

| ID | Requirement | Metric |
|----|-------------|--------|
| NFR15 | System should be available when needed | 99.9% uptime |
| NFR16 | Data backups should be performed | Daily backups (future) |
| NFR17 | System should handle errors gracefully | User-friendly error messages |

### 4.5 Maintainability

| ID | Requirement | Implementation |
|----|-------------|----------------|
| NFR18 | Code should be well-documented | Comments in HTML, CSS, JS |
| NFR19 | Code should follow best practices | Clean, modular code |
| NFR20 | Version control should be used | Git with GitHub |

### 4.6 Compliance

| ID | Requirement | Implementation |
|----|-------------|----------------|
| NFR21 | Comply with Nigeria Data Protection Regulation (NDPR) | Privacy policy, data minimization |
| NFR22 | Comply with campus IT policies | Approval from security department |
| NFR23 | Ethical handling of sensitive data | No personal data collected |

---

## 5. EXTERNAL INTERFACE REQUIREMENTS

### 5.1 User Interface

| Aspect | Requirement |
|--------|-------------|
| **Platform** | Web-based (HTML5) |
| **Technology** | HTML, CSS, JavaScript |
| **Framework** | None (vanilla JS for MVP) |
| **Responsive** | Yes (mobile-first design) |
| **Color Scheme** | Red/white theme (alert/security theme) |
| **Typography** | Readable fonts (Arial, Segoe UI, sans-serif) |
| **Icons** | Unicode emojis for visual cues |

### 5.2 Software Interfaces

| Interface | Description |
|-----------|-------------|
| **Browser API** | localStorage (data persistence) |
| **Google Forms** | Requirements gathering (external) |
| **draw.io** | Diagram creation (external) |
| **GitHub** | Version control and hosting |
| **Leaflet.js** | Map library (future integration) |

### 5.3 Hardware Interfaces
- None required – runs on any device with a web browser

### 5.4 Communication Interfaces
- HTTP/HTTPS protocol
- No real-time communication (WebSockets) in MVP

---

## 6. OBJECT LISTING

| Object | Attributes | Relationships |
|--------|------------|---------------|
| **User** | id, username, password (hashed), role, email, phone, createdAt | Has many Reports |
| **Student** | id, userId (FK), studentId, department, yearOfStudy | Extends User |
| **Security** | id, userId (FK), badgeNumber, unit | Extends User |
| **Admin** | id, userId (FK), permissions, lastLogin | Extends User |
| **Report** | id, crimeType, location, description, timestamp, anonymous, status, referenceNumber, userId (nullable) | Belongs to User or Anonymous |
| **IncidentLocation** | reportId, latitude, longitude, address | Belongs to Report |
| **Comment** | id, reportId, userId, content, timestamp | Belongs to Report and User |
| **Analytics** | id, reportType, count, dateRange, generatedBy | Generated by Admin |
| **SystemLog** | id, userId, action, timestamp, ipAddress | Tracks user actions |

---

## 7. REQUIREMENTS GATHERING

### 7.1 Methodology
A questionnaire was distributed via Google Forms to gather requirements from key stakeholders. The form targeted:
- Students (primary users)
- Staff/Faculty
- Landlords/Hostel Owners
- Campus Security Personnel

### 7.2 Google Form
**Link:** [https://forms.gle/YOUR_LINK_HERE](https://forms.gle/YOUR_LINK_HERE)

### 7.3 Key Findings from Questionnaire

| Area | Key Insight |
|------|-------------|
| **Crime Awareness** | X% of respondents have witnessed or experienced campus crime |
| **Reporting Rate** | Only X% reported incidents |
| **Reasons for Not Reporting** | Fear of retaliation, distrust, no easy channel |
| **App Interest** | X% would use an anonymous reporting platform |
| **Preferred Features** | Anonymity, real-time map, quick response |

> *Note: Insert actual percentages from your Google Form responses here*

### 7.4 Ishikawa Analysis Summary

| Category | Root Causes |
|----------|-------------|
| **Management** | Weak security, Underfunding |
| **Technology** | Poor network, No apps, Poor CCTV |
| **Environment** | Bad lighting, Hidden spots |
| **Process** | Untrained guards, Slow reporting, No follow-up |
| **Culture** | "Don't snitch" mentality, Distrust, Fear |

---

## 8. USE-CASE DIAGRAM

![Use-Case Diagram](usecase.png)

**Actors:**
- **Student:** Primary user who reports incidents
- **Security:** Responds to and manages reports
- **Admin:** Oversees system and manages users

**Use Cases:**
1. Report Incident – Student
2. View Map – Student, Security
3. Track Reports – Student
4. Manage Reports – Security
5. View Analytics – Admin
6. Manage Users – Admin

---

## 9. ISHIKAWA DIAGRAM

![Ishikawa Diagram](ishikawa.png)

**Categories & Causes:**
- **Management:** Weak security, underfunded
- **Technology:** Poor network, no apps, poor CCTV
- **Environment:** Bad lighting, hidden spots
- **Process:** Untrained guards, slow reporting, no follow-up
- **Culture:** "Don't snitch" mentality, distrust, fear

---

## 10. APPENDIX

### 10.1 Code Listing
```html
<!-- Full code is in index.html in the repository -->