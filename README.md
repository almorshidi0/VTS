## Vision

- For employees who need to manage their own vacation time, sick leave, and personal time off, the Vacation Tracking System (VTS) is a web application that provides an automated rules-based validation and tracking process. Unlike the tedious manual approval, checking and authorization process, VTS reduces the time it takes to manage vacation time request, minimizes non-core management activities, and saves time and money mostly in the HR department.

## Functional Requirements

- Implement a flexible rules-based system for validating and verifying leave time requests
- Provide access to requests for the previous calendar year
- Allow requests to be made up to a year and a half in the future
- Enable manager approval (for immediate subordinates, not needed for high level employees)
- Use e-mail notification to request manager approval and notify employees of request status changes
- Allow managers to directly award personal leave time to an employee (with system-set limits)
- Allow the HR and system administration personnel to override all actions restricted by rules
- Provide an interface for other internal systems to query any given employee's vacation request summary
- Interface with the HR department legacy systems to retrieve required employee information and changes

## Non-Functional Requirements

- The system shall be easy to use, intuitive, and intelligent
- The system shall authenticate all users via the existing intranet portal's single-sign-on mechanisms
- The system shall keep activity logs for all transactions
- The system shall log overrides of all actions restricted by rules performed by HR and system administration personnel.
- The system shall provide a Web service interface to accept queries about employee vacation requests summaries

## Constraints

- The system must use existing hardware and middleware
- The system must be implemented as an extension to the existing intranet portal system
- The system must use the portal's single-sign-on mechanisms for all authentication

## Domain

- Boundaries:
	- Users: Employee, Manager, Clerk, Admin
	- External Systems: Intranet portal's single-sign-on and HR legacy systems.
- Concepts
	- Employee: an employee who requests vacation time
	- Manager: An employee with the authority to approve leave for immediate subordinates
	- Vacation Request: A recorded request for vacation, sick leave, or personal time off
- Scope
	- In Scope (What VTS will do):
	    - Automate rules-based validation for vacation requests.
	    - Send approval requests via email.
	    - Allow HR Clerks to manually override rules and manage records.
	    - Provide an API/Interface for other internal systems to query vacation summaries.
	- Out of Scope (What VTS will NOT do):
	    - Authenticate users natively (relies entirely on the existing Intranet Portal SSO).

## Actors
- Employee: The main user of this system. An employee uses this system to manage his or her vacation time.
- Manager: An employee who has all the abilities and goals of a regular employee, but with the added responsibility of approving vacation requests for immediate subordinates. A manager may award subordinates comp time, subject to certain limits set in the system.
- Clerk: A member of the HR department who has sufficient rights to view employees' personal data and is responsible for ensuring that employees' information in all HR systems is up to date and correct. An Clerk can add or remove nearly any record in the system. In the real world, Clerks may or may not be employees; however, if they are employees, they use two separate login IDs to manage these two different roles.
- System Admin: A role responsible for the smooth running of the system's technical resources (e.g., Web server, database) and for collecting and archiving all log files.

## System Use Case Diagram

[](Use Case Diagram.png)

## The Manage Time Use Case

- Entity Relationships Diagram
[ER Diagram](ER Diagram.png)
- Relational Date Model
[Relational Data Model](Relational Data Model.png)
- Sequence Diagrams
	- Main Flow
	[Main Flow Sequence Diagram](Main Flow Sequence Diagram.png)
	- Alternate Flow: Withdraw Request
	[Withdraw Alternate Flow Sequence Digram](Withdraw Alternate Flow Sequence Digram.png)
	- Alternate Flow: Cancel Approved Request
	[Cancel Alternate Flow Sequence Diagram](Cancel Alternate Flow Sequence Diagram.png)
	- Alternate Flow: Edit Pending Request
	[Edit Alternate Flow Sequence Diagram](Edit Alternate Flow Sequence Diagram.png)
- Flow Charts
	- Main Flow
	[Main Flow Chart](Main Flow Chart.png)
	- Alternate Flow: Withdraw Request
	[Withdraw Alternate Flow Chart](Withdraw Alternate Flow Chart.png)
	- Alternate Flow: Cancel Approved Request
	[Cancel Alternate Flow Chart](Cancel Alternate Flow Chart.png)
	- Alternate Flow: Edit Pending Request
	[Edit Alternate Flow Chart](Edit Alternate Flow Chart.png)
- Pseudocode
```

```
