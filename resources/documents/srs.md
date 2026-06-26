# Software Requirement Specification (SRS)

## Functional Requirements
1. Users must be able to register using OAuth (Google/GitHub).
2. Admins can view the system analytics dashboard.

## Non-Functional Requirements
* **Security:** All passwords must be hashed using bcrypt before saving.
* **Performance:** API response time must be under 300ms.