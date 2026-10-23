## Vision

- For employees who need to manage their own vacation time, sick leave, and personal time off, the Vacation Tracking System (VTS) is a web application that provides automated, rules-based validation and tracking of leave requests. Unlike the tedious manual approval, checking, and authorization process, VTS reduces the time required to manage leave requests, minimizes non-core management activities, and saves time and money, primarily in the HR department.

## Functional Requirements

- Implement a flexible rules-based system for validating and verifying leave time requests
- Provide access to requests for the previous calendar year
- Allow requests to be made up to a year and a half in the future
- Enable manager approval (for immediate subordinates, not needed for high level employees)
- Use e-mail notification to request manager approval and notify employees of request status changes
- Allow managers to directly award personal leave time to an employee (with system-set limits)
- Allow the HR department to override all actions restricted by rules
- Provide an interface for other internal systems to query any given employee's vacation request summary
- Interface with the HR department legacy systems to retrieve required employee information and changes

## Non-Functional Requirements

- The system shall be easy to use, intuitive, and intelligent
- The system shall authenticate all users via the existing intranet portal's single-sign-on mechanisms
- The system shall keep activity logs for all transactions
- The system shall log all transactions, including overrides of rule-restricted actions

## Constraints

- The system must use existing hardware and middleware
- The system must be implemented as an extension to the existing intranet portal system
- The system must use the portal's single-sign-on mechanisms for all authentication

## Problem Domain

- Boundaries: The system manages employee vacation time, sick leave, and personal time off. It automates request validation according to the organization's rules, handles optional manager approval, and notifies employees of request status changes. HR clerks maintain employee records, leave allowances, categories, and rules. The system extends the existing intranet and interfaces with legacy HR systems.

- Domain Concepts: Employee, Manager, HR Clerk, System Administrator, Leave Request, Leave Category, Leave Balance, Leave Allowance, Leave Rules, Approval Status, and Activity Log.

- Scope of the System: Employees can view, create, and cancel leave requests. Managers can approve or reject requests and award additional leave within defined limits. HR clerks can maintain employee records and leave rules and override rule-based rejections. System administrators manage system logs and backups. The system validates requests automatically, sends email notifications, and maintains transaction logs.

## Actors
- Employee: The main user of this system. An employee uses this system to manage his or her vacation time.
- Manager: An employee who has all the abilities and goals of a regular employee, but with the added responsibility of approving vacation requests for immediate subordinates. A manager may award subordinates comp time, subject to certain limits set in the system.
- HR Clerk: A member of the HR department who has sufficient rights to view employees' personal data and override all actions restricted by rules. In the real world, Clerks may or may not be employees; however, if they are employees, they use two separate login IDs to manage these two different roles.
- System Admin: A role responsible for the smooth running of the system's technical resources (e.g., Web server, database) and for collecting and archiving all log files.

## System Use Case Diagram

![Use Case Diagram](Use%20Case%20Diagram.png)

## The Manage Time Use Case

- Entity Relationships Diagram
![ER Diagram](ER%20Diagram.png)
- Relational Date Model
![Relational Data Model](Relational%20Data%20Model.png)
- Sequence Diagrams
	- Main Flow
	![Main Flow Sequence Diagram](Main%20Flow%20Sequence%20Diagram.png)
- Flow Charts
	- Main Flow
	![Main Flow Chart](Main%20Flow%20Chart.png)
- Pseudocode
```
navigateToVTS() {
	lookUpRequestsAndBalances();
	displayRequestsAndBalances();
	if(isManager) {
		lookUpPendingRequests();
		displayPendingRequests();
	}
	if(userWantstoMakeRequest) {
		// Common flow for employees and managers
		while(!requestDetailsAreCompleteAndValid) {
			if(newRequest) {
				promptForCategory();
				promptForRequestDetails();
				requestDetailsAreCompleteAndValid = true;
			} else {
				displayEditableViewHighlightingErrors();
				if(userCansels) {
					break;
				}
			}
		}
		if(requestDetailsAreCompleteAndValid) {
			if(requestRequiresApproval) {
				recordInDbAsPending();
				sendEmailToManager()
			} else {
				recordInDbAsApproved();
			}
		}
		returnToHomePage();
	}
	if(isManager && managerSelectsARequestToApprove) {
		displayRequestDetails();
		if(approved) {
			changeRecordStateToApproved();
		} else {
			promptForExplanation();
			changeRecordStateToRejected();
		}
		sendEmailToEmployee();
		returnToHomePage();
	}
}
```
