# Team-Foxtrot

##### Sharmila Selvanayakam, Swathi Ravula, Tanja Plagemann

## Lab order automation  

#### Description 

Our virtual lab MiSwaTa is highly automated from prescription to invoice.  


Doctors can order a lab prescription for a patient via a Google form. They have to enter their individual requestor code, the patient data, the invoice type and select the requested analysis.  

The doctor doesn’t need to provide their email address and name explicitly, since this master data is already saved in the system (another Google sheet, identified via the requestor code).  

There are two possible scenarios as to where the invoice for this service is sent. It can either be sent to the health insurance of the patient or the patient themselves. 

If the invoice needs to be sent directly to the patient, the patient’s email has to be provided. Otherwise the order is rejected and a cancellation is sent to the doctor via their email address. 
The master data for the registered health insurances is saved in an additional Google sheet and identified via the insurance company name. 

If at any time the doctor would like to check the status of the order, they can use our chatbot application. To identify the order in our system, the doctor is asked to supply the patient’s first name, last name and date of birth. 


#### Business Process Flow: 

The lab administrator starts the Camunda Instance. The process flow will automatically check the Google Sheet “LabOrder” for any open order. Then the order status is updated to “received” and the lab technician can add the lab results via Camunda. Afterwards the results are checked in a DMN table and annotated with “OK” or “notOK” depending on the normal range for the specific tests (like Cholesterol). The status is changed to “analysis completed” and the summary of the results are reported via email to the doctor. Depending on the type of the invoice (health insurance or patient) the bill is created and sent to the corresponding email address. The status of the order is changed to “in billing”. After a final manual check of the payments, the process is completed and the order goes to status “completed”. 


#### Authors and acknowledgment 

Thank you to the DigiBP lecturers for the hands-on lectures and especially Charuta for her help with our project.  

#### Resources

[Prescription Order Form](https://docs.google.com/forms/d/e/1FAIpQLSfQs8cGd2bKQF_u6yinasf9VX3rH8FfdpuefcL9ssI7bTVTCA/viewform?usp=sf_link)

[Form Admin mode](https://docs.google.com/forms/d/1IB_glcX78C7KSul5MwQc4F-CVKiN6Pmy_nnucZAWbok/edit)

[Lab Order Queue](https://docs.google.com/spreadsheets/d/1jH9_oCoUMZemPrcxkbj0RxjJfH4lyrs9BMG9oCypBBw/edit?usp=sharing)

[Status Check Chatbot](https://dialogflow.cloud.google.com/#/agent/statuscheck-9psw/editIntent/e7da8001-5019-4a76-969e-83c3cf0bf38a/)

[Camunda herokuapp](https://digibp.herokuapp.com/camunda/app/tasklist/default/#/?searchQuery=%5B%5D&filter=4802bb7f-f9ef-11ea-a35f-9a370aa1b3d1&sorting=%5B%7B%22sortBy%22:%22created%22,%22sortOrder%22:%22desc%22%7D%5D)
