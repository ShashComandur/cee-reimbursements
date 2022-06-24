# CEE Reimbursements
This repository is intended to house documentation for the reimbursement automation process for the 
Civil and Environmental Engineering Department at UofSC.

### Author
Shash Comandur  
comandus@email.sc.edu  
shashcomandur.com

# About
The automation of the reimbursement process is implemented using Microsoft Power Automate. The current
flow chart that describes the process of the Power Automate flow can be found [here](cee-reimb-flowchart-v2.pdf). 
The main flow uses multiple subflows to break up the process. Documentation of the subflows can be found below.

## Subflows
These are the subflows called in the main flow. Provided below is an overview of what each subflow in the solution package
does.

### Main Test - 06/13/2022 (Driver)
This subflow is an updated version of the main flow. When a new form response is recorded, meaning a new request for a
reimbursement, this flow automatically sends out an approval request to confirm or reject the reimbursement itself.
When the approval is approved, it begins the rest of process by calling the subflow "Main Test - 06/02/2022".
When the approval is rejected, it sends out an email notifying the appropriate parties about the rejection.

### Main Test - 06/02/2022
This subflow is main process. It calls the rest of the appropriate subflows using the conditional logic displayed in the flowchart 
in the correct order.

### Check if entry exists in Peoplesoft Table
This subflow takes in the input of an email and returns true or false depending on whether that email is present in the Peoplesoft
SharePoint table.

### Check Peoplesoft validation
This subflow takes in the input of an email, assuming it is present in the Peoplesoft table, and returns true or false depending
on whether the "Validated" field is checked or not for that person. Note that this subflow is only called after the previous
subflow returns true, meaning that it is only run on emails that exist in the table - the case in which the input does not exist
cannot happen.

### Email request proof of payment
This subflow takes in the input of an email, and sends the proof of payment request email template to it.

### Get first and last name
This subflow takes in the input of an email, and returns the first and last names of the person associated with that email.

### Get Student USCID
This subflow takes in the input of a student's email, and returns the USCID associated with it.

### Get Supervisor USCID
This subflow takes in the input of a supervisor's email, and returns the USCID associated with it.

### Send registration request by email, start approval
This subflow is activated in the case which a user is not validated in Peoplesoft. It takes in the email of that person and does two
things: it sends them an email asking them follow the appropriate instructions to become validated in Peoplesoft, and it starts an
approval for them, which they are instructed to approve after completing the registration. 

This choice is intentional, as it allows the approval is what allows the process to continue automatically after the user fully finishes registration. 