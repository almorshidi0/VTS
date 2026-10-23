## Requests UI

![UI](UI.png)

## What if we need to have in the future another status like HR_Pending, HR_Approval with minimum change?

In the new data model, request state is modeled as a separate table to facilitate extension.

- Entity Relationships Diagram
![ER Diagram](ER%20Diagram.png)
- Relational Data Model
![Relational Data Model](Relational%20Data%20Model.png)

## Request State Machine

![Request State Machine](Request%20State%20Machine.png)

## Request Sequence Diagram

![Request Sequence Diagram](Request%20Sequence%20Diagram.png)

## Alternate Flow: Withdraw Request

- Flowchart
![Withdraw Alternate Flow Chart](Withdraw%20Alternate%20Flow%20Chart.png)
- Sequence Diagram
![Withdraw Alternate Flow Sequence Diagram](Withdraw%20Alternate%20Flow%20Sequence%20Digram.png)
- Pseudocode
```
navigateToVTS() {
	lookUpRequestsAndBalances();
	displayRequestsAndBalances();
	// Employee selects a pending request to withdraw
	if(EmployeeWantstoWithdrawRequest) {
		promptForConfirmation();
		if(confirmed) {
			updateInDbAsWithdrawn();
			removeFromManagerView();
			sendEmailToManager();
		}
		returnToHomePage();
	}
}
```

## Alternate Flow: Cancel Approved Request

- Flowchart
![Cancel Alternate Flow Chart](Cancel%20Alternate%20Flow%20Chart.png)
- Sequence Diagram
![Cancel Alternate Flow Sequence Diagram](Cancel%20Alternate%20Flow%20Sequence%20Diagram.png)
- Pseudocode
```
navigateToVTS() {
	lookUpRequestsAndBalances();
	displayRequestsAndBalances();
	// Employee selects an approved request to cancel
	if(EmployeeWantstoCancelRequest) {
		if(cancellable) {
			promptForConfirmation();
			if(!futureRequest) {
				promptForExplanation();
			}
			if(confirmed) {
				updateInDbAsCanceled();
				returnBalances();
				removeFromManagerView();
				sendEmailToManager();
			}
		} else {
			alertUnCancellable();
		}
		returnToHomePage();
	}
}
```

## Alternate Flow: Edit Pending Request

- Flowchart
![Edit Alternate Flow Chart](Edit%20Alternate%20Flow%20Chart.png)
- Sequence Diagram

![Edit Alternate Flow Sequence Diagram](Edit%20Alternate%20Flow%20Sequence%20Diagram.png)
- Pseudocode
```
navigateToVTS() {
	lookUpRequestsAndBalances();
	displayRequestsAndBalances();
	// Employee selects a pending request to edit or withdraw
	if(EmployeeWantsToWithdrawRequest) {
		promptForConfirmation();
		if(confirmed) {
			updateInDbAsWithdrawn();
			removeFromManagerView();
			sendEmailToManager();
		}
		returnToHomePage();
	} else if(EmployeeWantsToEditRequest) {
		while(!newDetailsAreCompleteAndValid) {
			displayEditableView();
			if(cancelled) {
				break;
			} else if(isValidChange) {
				updateDetailsInDB();
				newDetailsAreCompleteAndValid = true;
			}
		}
		returnToHomePage();
	}
}
```
