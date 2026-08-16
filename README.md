# BPMN Process Modeling Assignment(ALL BPMN files are inside bpmn folder and the screenshots are in readme and in images folder)
## Scenario 1: Employee Leave Approval
![Scenario 1 - Employee Leave Approval](images/leave-approval.png)

### Process Description
An employee applies for leave through the HR system. The system first checks whether the employee has enough leave balance before routing the request to a manager for a decision.

### Flow Logic
1. **Start Event** – "Employee Submits Leave Request" triggers the process.
2. **Task** – "Check Leave Balance": the HR system verifies available balance.
3. **Exclusive Gateway** – "Sufficient Balance?"
   - **No** → **Task** "Send Insufficient Balance Notification" → **End Event** "Insufficient Balance".
   - **Yes** → **Task** "Send Request to Manager for Approval".
4. **Exclusive Gateway** – "Manager Approves?"
   - **Approved** → **Task** "Update Employee Leave Balance" → **Task** "Send Approval Notification" → **End Event** "Leave Approved".
   - **Rejected** → **Task** "Send Rejection Notification" → **End Event** "Leave Rejected".


## Scenario 2: Online Purchase Order Processing
![Scenario 2 - Online Purchase](images/purchase-order.png)

### Process Description
A customer places an online order. The system checks stock availability and processes payment before confirming and shipping the order.

### Flow Logic
1. **Start Event** – "Customer Places Order".
2. **Task** – "Check Product Availability".
3. **Exclusive Gateway** – "Product Available?"
   - **No** → **Task** "Notify Customer - Out of Stock" → **End Event** "Out of Stock" (process ends here).
   - **Yes** → **Task** "Process Payment".
4. **Exclusive Gateway** – "Payment Successful?"
   - **No** → **Task** "Notify Customer - Payment Failed" → **End Event** "Payment Failed" (process ends here).
   - **Yes** → **Task** "Confirm Order" → **Task** "Prepare Product for Shipment" → **Task** "Ship Order" → **Task** "Send Shipping Confirmation" → **End Event** "Order Completed".


## Scenario 3: IT Service Request
![Scenario 3 - IT Service Request](images/it-service-request.png)

### Process Description
An employee reports an IT problem. The help desk registers and triages it by severity, assigns it to the right technician tier, and routes it internally or externally depending on whether it can be resolved in-house.

### Flow Logic
1. **Start Event** – "Employee Reports IT Problem".
2. **Task** – "Submit IT Support Request".
3. **Task** – "Register Request" (help desk logs the ticket).
4. **Task** – "Check Severity of the Problem".
5. **Exclusive Gateway** – "Severity Level?"
   - **Low Severity** → **Task** "Assign to Support Technician".
   - **High Severity** → **Task** "Assign to Senior Technician".
   - Both paths **converge** at a merging Exclusive Gateway before continuing (a technician has now been assigned, regardless of tier).
6. **Task** – "Investigate the Problem".
7. **Exclusive Gateway** – "Resolvable Internally?"
   - **Yes** → **Task** "Fix the Problem".
   - **No** → **Task** "Escalate to External Service Provider".
   - Both paths **converge** again at a second merging Exclusive Gateway (resolution has been reached either way).
8. **Task** – "Update Request Status".
9. **Task** – "Send Resolution Notification to Employee".
10. **End Event** – "Request Resolved".
