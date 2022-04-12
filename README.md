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
These are the subflows called in the main flow.

### Peoplesoft Registration Subflow
The Peoplesoft Registration Subflow can be found [here](https://us.flow.microsoft.com/manage/environments/Default-4b2a4b19-d135-420e-8bb2-b1cd238998cc/flows/274a752a-1e2c-4ee1-816e-fd17c66e802e/details). 

It checks if a given input is present in the Peoplesoft registration SharePoint table - if they are not in the
table, it will automatically add them. The flow then checks if the input is registered in Peoplesoft. 

If they are not, the flow will send them a request to register with an Outlook approval that they approve when
they complete registration. If they are already registered, it will email them requesting a proof of payment.  