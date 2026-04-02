# Agile Planning Document
## RPL (Recognition of Prior Learning) Application System

**Author:** Boniface Kabaso
**Date:** March 2026
**Assignment:** Assignment 6 — Agile User Stories, Backlog, and Sprint Planning

---

## Table of Contents

1. [User Stories](#1-user-stories)
2. [Product Backlog](#2-product-backlog)
3. [Sprint Plan — Sprint 1](#3-sprint-plan--sprint-1)
4. [Traceability Matrix](#4-traceability-matrix)

---

## 1. User Stories

User stories are written in the format: *"As a [role], I want [action] so that [benefit]."*
All stories follow the **INVEST** criteria: Independent, Negotiable, Valuable, Estimable, Small, Testable.

---

### Functional User Stories (from Assignment 4 Requirements)

| Story ID | User Story | Acceptance Criteria | Priority | Linked Requirement | Linked Use Case |
|----------|-----------|---------------------|----------|--------------------|-----------------|
| **US-001** | As a **student**, I want to register an account using my institutional email so that I can access the RPL system securely. | Account created after email verification. Password must meet complexity rules. Confirmation email received within 2 minutes. Login works after verification. | High | FR-01 | UC1 |
| **US-002** | As a **student**, I want to submit an RPL application online so that I no longer need to complete and submit paper forms. | Form captures all required fields. Supporting documents can be uploaded (PDF, DOCX, JPG, PNG ≤10MB). Unique reference number generated on submission. Confirmation email sent within 2 minutes. | High | FR-02 | UC2 |
| **US-003** | As a **student**, I want the system to prevent me from submitting a duplicate application for the same module so that I do not accidentally apply twice. | System checks for active application on module selection. Duplicate detected → submission blocked with clear error message and link to existing application. Rejected applicants can reapply after the configured waiting period. | High | FR-03 | UC14 |
| **US-004** | As a **student**, I want to track the status of my RPL application in real time so that I always know where my application stands without having to contact the office. | Dashboard displays all submitted applications and their current status. Status updates within 60 seconds of assessor action. Status history timeline is visible. In-app and email notifications sent on every status change. | High | FR-04 | UC4 |
| **US-005** | As an **academic assessor**, I want to view and review assigned RPL applications so that I can evaluate student evidence and make informed decisions efficiently. | Assessor queue shows all assigned applications ordered by submission date. Each application shows student details, prior learning description, and all uploaded documents. Assessor can add notes and select Approve, Reject, or Request Additional Information. Decision is timestamped and linked to assessor account. | High | FR-05 | UC6 |
| **US-006** | As an **academic assessor**, I want to request additional information from a student during review so that I can make a fully informed assessment decision. | Assessor can enter a specific request. Application status changes to "Additional Information Required". Student notified via email and in-app notification with request details and deadline. Student can upload response documents without resubmitting. | High | FR-06 | UC7 |
| **US-007** | As a **registrar**, I want to generate reports on RPL application statistics so that I can monitor outcomes and compliance with institutional policies. | Reports include: total applications, approval/rejection rates, average processing time, applications per programme. Reports exportable as CSV and PDF. Data reflects current database state. Report generates within 5 seconds. | Medium | FR-09 | — |
| **US-008** | As a **registrar**, I want a complete audit log of all actions taken on applications so that I can ensure accountability and meet compliance requirements. | Every action (submission, status change, decision, login) is logged with user ID and timestamp. Logs are read-only — no editing or deletion permitted. Logs retained for minimum 5 years. Accessible to Registrar, IT Admin, and DPO only. | High | FR-10 | — |
| **US-009** | As an **IT administrator**, I want to manage user roles and permissions so that each user only accesses features relevant to their role. | IT Admin can create, edit, and deactivate user accounts. Roles: Student, Assessor, Registrar, Institution Admin, IT Admin, Helpdesk. Unauthorised access attempts blocked and logged. Role changes take effect immediately. | High | FR-11 | UC9 |
| **US-010** | As a **helpdesk staff member**, I want to look up a student's application status so that I can answer student queries without needing to contact the Registrar. | Helpdesk can search by student ID or email. Application status and history are displayed. Helpdesk has read-only access — no edit, approve, or reject actions available. Search results load within 2 seconds. | Medium | FR-12 | UC13 |
| **US-011** | As an **institution administrator**, I want to configure available modules and academic periods for RPL so that the system reflects our current institutional offerings. | Admin can add, edit, and deactivate modules and qualifications. Admin can set academic periods and application deadlines. Changes take effect immediately without a system restart. All configuration changes are logged. | Medium | FR-07 | UC10 |
| **US-012** | As a **student**, I want to receive automated email notifications when my application status changes so that I am always informed without having to log in constantly. | Email sent within 2 minutes of any status change. Email contains: application reference number, new status, and relevant details. All sent notifications are logged. | Medium | FR-08 | UC5 |

---

### Non-Functional User Stories

| Story ID | User Story | Acceptance Criteria | Priority | Linked Requirement |
|----------|-----------|---------------------|----------|--------------------|
| **US-013** | As a **system administrator**, I want all user data encrypted with AES-256 at rest so that security compliance with POPIA and GDPR is maintained. | All data in the database is encrypted at rest using AES-256. Verified through security audit and penetration testing. No plaintext personal data stored. | High | NFR-SEC01 |
| **US-014** | As a **student**, I want the application pages to load within 2 seconds so that I can complete my application without frustrating delays. | All dashboard and form pages load in ≤2 seconds under normal load (≤500 concurrent users). Verified through load testing. | High | NFR-P01 |
| **US-015** | As an **IT administrator**, I want the system to support 1,000 concurrent users during peak periods so that the system remains available and performant at the start of every semester. | Load test with 1,000 concurrent users shows response times ≤2 seconds and error rate <1%. No crashes or timeouts during 10-minute sustained load test. | High | NFR-S01 |
| **US-016** | As a **student with a disability**, I want the system interface to comply with WCAG 2.1 Level AA accessibility standards so that I can use the system independently and without barriers. | Interface passes WCAG 2.1 Level AA audit. Screen reader compatible. All form fields have labels. Colour contrast meets minimum ratios. | Medium | NFR-U01 |

---

## 2. Product Backlog

Stories are prioritised using **MoSCoW** methodology. Effort is estimated using the **Fibonacci sequence** (1, 2, 3, 5, 8, 13) in story points.

| Story ID | User Story (Summary) | MoSCoW Priority | Story Points | Dependencies | Justification |
|----------|----------------------|-----------------|--------------|--------------|---------------|
| **US-001** | Student registration and login | Must-have | 3 | None | All other features require authenticated access. Core foundation of the system. |
| **US-009** | IT Admin manages user roles (RBAC) | Must-have | 5 | US-001 | Role-based access is a security requirement and must be in place before any role-specific features are built. |
| **US-002** | Student submits RPL application | Must-have | 5 | US-001 | Core value proposition of the system — the primary reason the system is being built. |
| **US-003** | Duplicate application prevention | Must-have | 3 | US-002 | Directly addresses a key stakeholder pain point. Must be built alongside submission to avoid data integrity issues. |
| **US-004** | Student tracks application status | Must-have | 3 | US-002 | Students need visibility into their application. Directly reduces helpdesk load and improves student satisfaction. |
| **US-005** | Assessor reviews assigned applications | Must-have | 5 | US-002, US-009 | Without assessor review, no applications can be processed. Core workflow step. |
| **US-006** | Assessor requests additional information | Must-have | 3 | US-005 | Essential part of the assessment process. Assessors frequently need more evidence before deciding. |
| **US-013** | AES-256 encryption at rest | Must-have | 5 | US-001 | Legal compliance (POPIA/GDPR) is non-negotiable. Must be in place before any personal data is stored. |
| **US-015** | System supports 1,000 concurrent users | Must-have | 8 | US-001, US-002 | Peak semester loads must be planned for from the start to avoid architectural rework later. |
| **US-008** | Registrar views audit logs | Should-have | 3 | US-005 | Important for compliance and accountability, but the system can function temporarily without the full audit UI. |
| **US-012** | Automated email notifications | Should-have | 3 | US-002, US-004 | Improves student experience significantly. Should be included early but not a blocker for MVP core flow. |
| **US-014** | Pages load within 2 seconds | Should-have | 5 | US-001, US-002 | Performance is critical for adoption, but can be optimised iteratively after functional MVP is working. |
| **US-011** | Admin configures modules and periods | Should-have | 3 | US-009 | Needed before go-live but can initially be seeded via backend/database for MVP testing. |
| **US-010** | Helpdesk views application status | Could-have | 2 | US-004, US-009 | Useful for helpdesk efficiency but students can self-serve via the tracking dashboard in the interim. |
| **US-007** | Registrar generates reports | Could-have | 5 | US-005, US-008 | Valuable for institutional oversight but not required for the core student-facing MVP. |
| **US-016** | WCAG 2.1 AA accessibility compliance | Could-have | 5 | US-002, US-004 | Important for inclusivity and should be addressed early, but full compliance audit can follow after functional MVP. |

---

### Backlog Prioritisation Justification

**Must-have stories** form the core RPL application lifecycle: a student can register, submit an application, the system prevents duplicates, the student can track status, and an assessor can review and request information. These align directly with the primary stakeholder success metrics from Assignment 4 — eliminating paper forms, preventing duplicates, and enabling real-time tracking. Security (US-013) and scalability (US-015) are also Must-have because legal compliance and system availability are non-negotiable from day one.

**Should-have stories** enhance the experience significantly — notifications, audit logs, performance optimisation, and admin configuration — but the system can demonstrate core value without them in the first sprint.

**Could-have stories** add operational efficiency (helpdesk view, reporting) and quality polish (accessibility) that are genuinely important but can be deferred to later sprints without blocking the MVP.

---

## 3. Sprint Plan — Sprint 1

### Sprint Goal
> *"Deliver a working MVP of the RPL application system where a student can register, log in, submit an RPL application with document uploads, and see their application on a dashboard — with duplicate prevention enforced and role-based access in place."*

**Sprint Duration:** 2 weeks (14 days)
**Sprint Number:** 1
**Team:** Boniface Kabaso (Solo developer / full-stack)

### Selected User Stories for Sprint 1

| Story ID | Summary | Story Points | Rationale for Inclusion |
|----------|---------|--------------|--------------------------|
| US-001 | Student registration and login | 3 | Authentication is the entry point for all other features |
| US-009 | IT Admin manages user roles (RBAC) | 5 | Must be built alongside auth to enforce access from the start |
| US-002 | Student submits RPL application | 5 | Core feature — the MVP cannot exist without it |
| US-003 | Duplicate application prevention | 3 | Inseparable from submission; must be built together |
| US-004 | Student tracks application status | 3 | Completes the basic student journey for MVP |

**Total Story Points:** 19

---

### Sprint Backlog

| Task ID | Task Description | Story ID | Assigned To | Estimated Hours | Status |
|---------|-----------------|----------|-------------|-----------------|--------|
| T-001 | Set up project repository, folder structure, and CI/CD pipeline | US-001 | Boniface | 4 | To Do |
| T-002 | Design and implement database schema (Users, Roles, Applications, Documents) | US-001, US-009 | Boniface | 6 | To Do |
| T-003 | Build user registration API endpoint with email validation and password hashing | US-001 | Boniface | 5 | To Do |
| T-004 | Implement email verification flow (token generation, verification endpoint) | US-001 | Boniface | 4 | To Do |
| T-005 | Build login API endpoint with JWT authentication and session management | US-001 | Boniface | 4 | To Do |
| T-006 | Design and implement Role-Based Access Control (RBAC) middleware | US-009 | Boniface | 6 | To Do |
| T-007 | Create role management UI for IT Admin (create, edit, deactivate users) | US-009 | Boniface | 5 | To Do |
| T-008 | Design RPL application form UI (fields, layout, validation) | US-002 | Boniface | 5 | To Do |
| T-009 | Build application submission API endpoint (save form data to database) | US-002 | Boniface | 5 | To Do |
| T-010 | Implement document upload functionality (file validation, secure storage) | US-002 | Boniface | 6 | To Do |
| T-011 | Generate unique application reference number on submission | US-002 | Boniface | 2 | To Do |
| T-012 | Implement duplicate application check logic (query by student ID + module) | US-003 | Boniface | 4 | To Do |
| T-013 | Build frontend duplicate warning message and link to existing application | US-003 | Boniface | 2 | To Do |
| T-014 | Design and build student dashboard (list of submitted applications + statuses) | US-004 | Boniface | 5 | To Do |
| T-015 | Build application detail view (status history timeline, current status display) | US-004 | Boniface | 4 | To Do |
| T-016 | Write unit tests for registration, login, submission, and duplicate check | US-001–US-004 | Boniface | 6 | To Do |
| T-017 | Deploy MVP to staging environment and perform smoke testing | All | Boniface | 4 | To Do |

**Total Estimated Hours: 77 hours**

---

### Definition of Done (Sprint 1)

A user story is considered **Done** when:
- All acceptance criteria are met and verified.
- Unit tests pass with ≥80% code coverage for the feature.
- Code is reviewed (self-review for solo project) and merged to the main branch.
- Feature is deployed to the staging environment and manually smoke-tested.
- GitHub Issue for the story is closed and linked to the relevant commit.

---

## 4. Traceability Matrix

| Story ID | User Story Summary | Assignment 4 Requirement | Assignment 5 Use Case | MoSCoW | Sprint 1 |
|----------|-------------------|--------------------------|-----------------------|--------|----------|
| US-001 | Student registration/login | FR-01 | UC1 | Must-have | ✅ Included |
| US-002 | Submit RPL application | FR-02 | UC2, UC3 | Must-have | ✅ Included |
| US-003 | Duplicate prevention | FR-03 | UC14 | Must-have | ✅ Included |
| US-004 | Track application status | FR-04 | UC4 | Must-have | ✅ Included |
| US-005 | Assessor reviews applications | FR-05 | UC6 | Must-have | ⏳ Sprint 2 |
| US-006 | Request additional information | FR-06 | UC7 | Must-have | ⏳ Sprint 2 |
| US-007 | Registrar generates reports | FR-09 | — | Could-have | ⏳ Sprint 3 |
| US-008 | Audit logs | FR-10 | — | Should-have | ⏳ Sprint 2 |
| US-009 | RBAC / User role management | FR-11 | UC9 | Must-have | ✅ Included |
| US-010 | Helpdesk status view | FR-12 | UC13 | Could-have | ⏳ Sprint 3 |
| US-011 | Admin configures modules | FR-07 | UC10 | Should-have | ⏳ Sprint 2 |
| US-012 | Automated email notifications | FR-08 | UC5 | Should-have | ⏳ Sprint 2 |
| US-013 | AES-256 encryption at rest | NFR-SEC01 | — | Must-have | ✅ Included (via T-002) |
| US-014 | Pages load ≤2 seconds | NFR-P01 | — | Should-have | ⏳ Sprint 2 |
| US-015 | 1,000 concurrent users | NFR-S01 | — | Must-have | ⏳ Sprint 2 |
| US-016 | WCAG 2.1 AA accessibility | NFR-U01 | — | Could-have | ⏳ Sprint 3 |

---

*Document prepared for Assignment 6 — RPL Application System*
*Author: Boniface Kabaso | March 2026*
