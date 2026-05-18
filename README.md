# End-to-End Hiring & Contracting Automation
<img width="2172" height="724" alt="ChatGPT Image Apr 30, 2026, 02_29_38 PM" src="https://github.com/user-attachments/assets/419794f7-1394-4405-93f9-90666385e458" />


# 1. Introduction
## 1.1 Team Bois de la Batie

| Name  | Role | Email Address |
| ------------- | ------------- | ------------- |
| Joël Grolimund  | BPMN Expert | joel.grolimund@students.fhnw.ch |
| Samed Öztürk  | IT Specialist  | samed.oeztuerk@students.fhnw.ch |
| Sara Afzalinia  | HR Expert  | sara.afzalinia@students.fhnw.ch |
| Thea Amoy  | HR Expert  | theayzabelle.amoy@students.fhnw.ch |

## 1.2 Supervisors

| Name  | Email Address |
| ------------- | ------------- |
| Andreas Martin  |  andreas.martin@fhnw.ch |
| Charuta Pande  |  charuta.pande@fhnw.ch |
| Devid Montecchiari  |  devid.montecchiari@fhnw.ch |

## 1.3 Abstract & Project Overview
Obtaining an apprenticeship is generally considered moderately challenging, as the process combines elements of a job search with certain academic requirements. While there are many apprenticeship positions available in Switzerland, competition can be strong in more popular fields such as business or healthcare, making it harder for some applicants to secure a place. Students are typically required to submit a CV, a motivation letter, and school reports, and to pass interviews in which their attitude and suitability are evaluated. 

Our role in Human Resources is to support the company in managing this process by efficiently handling applications and making the experience as flexible and user-friendly as possible.

In this project, we focus on improving the hiring and contracting process. This includes mapping the journey from the moment a candidate is selected through their signing of the contract to the successful filling of the position. The current process requires extensive verification to ensure compliance with federal and cantonal regulations, as well as applicable collective labor agreements (Gesamtarbeitsverträge), resulting in a significant administrative workload for employees.

## 1.4 Use Case & Scope

The case focuses on the end-to-end hiring and contract management process for apprentices, from candidate selection to contract signing and onboarding preparation. The process involves multiple stakeholders, including HR, hiring managers, candidates, and, where applicable, legal guardians. It requires strict compliance with federal and cantonal regulations, as well as applicable collective labor agreements (Gesamtarbeitsverträge).

Currently, the process is characterized by:

- Multiple manual document exchanges
- Repeated compliance and document verification steps
- Iterative feedback loops between stakeholders
- Manual contract creation and validation

The objective of this initiative is to analyze, standardize, and automate the process to improve efficiency, ensure compliance, and enhance the overall experience for both HR and the candidates.

Out of scope are activities related to candidate sourcing (including job postings and candidate outreach), interviews and evaluations, and post-onboarding processes. Payroll management and any changes to legal or regulatory frameworks are also excluded.

## 1.5 Stakeholders

The process involves three key stakeholders. The HR of the Company drives the overall hiring process from start to finish. The Apprentice and their guardian participate by filling out forms, reviewing documents, and signing them. The guardian is only involved when the apprentice is under 18 years old, for which they would need to co-sign the employee  contract. 

# 2. AS IS

<img width="10104" height="2940" alt="Hiring_Apprentice_AS-IS" src="https://github.com/user-attachments/assets/bded92cd-71d8-46da-b0c2-6c32f42ea789" />


## 2.1 Limitations in the AS-IS process
The AS-IS process for hiring apprentices in Switzerland is built around paper forms, manual data entry, and sequential coordination across multiple parties. Every step depends on a single HR contact chasing documents, re-entering contract details by hand, and personally triggering each follow-up action in turn. The result is a process that is slow to complete, sensitive to errors, and difficult to scale — particularly when a guardian signature or a late correction throws the whole sequence off course.

### a. Paper-based intake
The process starts with physical or email-attached documents that must be manually sent, completed, and returned, introducing delays before HR can even begin.
### b. Manual contract creation
Every hire requires HR to look up and re-enter occupation codes, salary bands, and duration from the cantonal VET template, with no reuse of prior data or smart defaults.
### c. Late error detection
Contract mistakes only surface during the review stage, well into the process, triggering a correction feedback loop that sends work back to HR and restarts the clock.
### d. Fragmented multi-party coordination
The candidate, guardian (for minors), and HR each operate in separate lanes with no shared digital workspace, meaning every cross-party step relies on manual communication and follow-up.
### e. Disconnected close-out tasks 
Once the contract is signed, HR must manually trigger each wrap-up action in sequence: saving to the system, creating a new entry, removing the job posting, and informing the school — none of which are linked or automated.

# 3. TO BE

<img width="9420" height="1815" alt="Hiring_Apprentice_TO-BE" src="https://github.com/user-attachments/assets/f7b5cacd-40b4-41f8-9000-d8bfaef2adad" />


## 3.1 Process Optimizations

### 3.1.1 Standard Fill out Form

A standardized input form was set up to ensure consistent data collection, making it easier to automatically populate the apprenticeship contract template.

### 3.1.2 Systematic Corrections

Corrections have traditionally been a significant time drain for HR users, involving back-and-forth emails and calls, as well as manual updates to both the contract and the database. To address this pain point, we implemented a systematic correction process.

There are two points in the process where corrections can be made. First, once the candidate submits their form, the HR user can review and adjust any information directly in Camunda before proceeding. Second, when the candidate (and their guardian, if applicable) receives the contract for signing, they can flag any errors by clicking a dedicated correction link in the email. They simply describe the issue, and the HR user — who has full visibility over all requested changes — can then update the data in Camunda, regenerate the contract, and have the changes automatically reflected in Supabase.

This approach reduces unnecessary back-and-forth between parties, ensures that all changes are documented, and keeps the overall process moving efficiently.

<br> <ins> Camunda Task Modeler </ins> : Pre-Contract Generation (First Instance of Corrections)

<br> <img width="1271" height="658" alt="Screenshot 2026-05-14 at 18 07 04" src="https://github.com/user-attachments/assets/bebe391a-f77e-4ffc-9356-90aecc90e32c" />

<br> <ins> Fill out Form </ins> : Correction Request (Second Instance of Corrections)

<br> <img width="629" height="474" alt="Screenshot 2026-05-14 at 18 36 07" src="https://github.com/user-attachments/assets/67f70c0b-2318-4fae-9796-4a22cbf87e76" />

<br> <ins> Make Scenario </ins> : Fillout Correction Form

<br> <img width="504" height="263" alt="Screenshot 2026-05-14 at 22 28 27" src="https://github.com/user-attachments/assets/1842d027-34a3-47f3-9b48-a409b3062873" />

## 3.2 Automations

### 3.2.1 Automation of email sending to candidate and guardian

Once the candidate accepts the offer, the process of obtaining their personal information (and their guardian's) begins. This action is triggered in Camunda when the HR user confirms the candidate's acceptance of the offer.

<br> <ins> Camunda Task Modeler </ins> : HR user Confirmation of Offer Acceptance

<img width="693" height="232" alt="Screenshot 2026-05-14 at 17 47 15" src="https://github.com/user-attachments/assets/f2b5942b-91ed-4102-9b88-5c7e730223ea" />

<br> <ins> Make Scenario </ins> : Email send form to Apprentice

<img width="603" height="260" alt="Screenshot 2026-05-14 at 17 10 49" src="https://github.com/user-attachments/assets/0b8242e0-958f-48f0-97f5-7818937681b4" />

The candidate and their guardian receive an email prompting them to complete an employee form. This includes information that will eventually be used to finalize the contract.

<br> <ins> Email received by the candidate

<img width="392" height="340" alt="Screenshot 2026-05-14 at 18 05 32" src="https://github.com/user-attachments/assets/4418df57-fe4e-4d01-836c-cf0545cd76b2" />

<br> <ins> Make Scenario </ins> : Online Form with Apprentice Data

<img width="1177" height="244" alt="Screenshot 2026-05-14 at 17 09 53" src="https://github.com/user-attachments/assets/69b248d0-b72d-4cf8-a52c-6b2148eccc50" />

Once the form has been filled out, the answers are downloaded and uploaded to the database "Supabase". A variable "is_adult" is consequently created to calculate the candidates' age. The process defines two validations: one in the frontend and another in the backend. This is because the front end does not account for leap years in its calculations, while the backend makes up for it. 

In Supabase, there are two tables: one for candidates and another for guardians, linked via the Student_ID field. Once the rows are created, Camunda will receive a notification that this part of the process is done. 

### 3.2.2 DMN table automation

<img width="1456" height="358" alt="Screenshot 2026-05-14 at 17 31 20" src="https://github.com/user-attachments/assets/6c5c0911-4d50-4890-b2a2-31f828362583" />

This is the Decision Key Points Apprenticeship DMN table. It defines salary and holiday entitlements by job type, using a "First" hit policy.
The introduction of such a process reduces the time employees need to map the different values each time a contract is created. Another benefit is that this table can be easily revised should new information or regulations be introduced. 

Once the information is extracted, the HR user can verify all required information instantly. It is essential that a user task be put in place in this part of the process to ensure that the information to be input into the contract is correct and done to the best of the user's knowledge. The HR user needs to tick the box "Contract Approved" in Camunda to proceed. 

<br> <ins> Camunda Task Modeler </ins>: HR User Confirmation of Contract

<img width="1271" height="658" alt="Screenshot 2026-05-14 at 18 07 04" src="https://github.com/user-attachments/assets/197c881e-e48f-445d-a8ce-69226579cf42" />

### 3.2.3. Population of the Apprentice Contract template form

<br> <ins> Make Scenario </ins> : PDF Generation and Send email

<br> <img width="1051" height="285" alt="Screenshot 2026-05-14 at 18 18 19" src="https://github.com/user-attachments/assets/65520257-3e99-40b2-9fe4-58bc224ad585" />

The information received from the candidate, as well as the results of the DMN table, will be integrated in the Apprentice Contract template form using the integration PDF.co.

### 3.2.4. Set up automatic sending to guardians for candidates under 18

Once the HR user confirms the data has been received in Camunda, the Apprentice contract will be generated in PDF format and uploaded to Supabase. In the latter part of the scenario, a router has been put in place to determine whether the contract should be sent only to the candidate or to the candidate and their respective guardian. It uses the aforementioned variable "is_adult," created earlier in the process.

### 3.2.5. Automated Update of Database in case of corrections

In case of corrections, the HR user can implement them in Camunda directly. Those changes will then be reflected in Supabase via this trigger:

<br> <ins> Make Scenario </ins> : Supabase Update
<img width="1075" height="282" alt="Screenshot 2026-05-14 at 18 11 59" src="https://github.com/user-attachments/assets/0973285e-e823-4cae-8766-d7884bd2b1ab" />

The HR user will be able to view the corrections to be made in Camunda Task Modeler under the field "Candidate Feedback Request". They can then implement those changes and go along the process of confirming, generating the contract, and sending it to the candidate (and their guardian, if applicable) for signature.

### 3.2.6. Automatic upload of the contract once approved

If the candidate signs the contract, they will need to click the first link in the e-mail they receive. They will be sent to another form where they can upload the document.

<br> <ins> Fill out form </ins> : Signed Apprenticeship Contract Upload
<br> <img width="562" height="575" alt="Screenshot 2026-05-14 at 22 48 25" src="https://github.com/user-attachments/assets/34eea6be-1d1f-46dc-8032-e014399370a8" />

<br> <ins> Make Scenario </ins> : Google Slides and AI Stuff (Part 1)
<br> <img width="563" height="192" alt="Screenshot 2026-05-14 at 22 51 13" src="https://github.com/user-attachments/assets/e822d7b6-44a3-4822-8b46-8e6d0e8ed438" />

Once the candidate uploads the document and sends it, another scenario is triggered in which the HTTP will download said document and upload it to Supabase. 

### 3.2.7. Generation of AI profile (for the internal ads)
<br> <ins> Make Scenario </ins>: Google Slides and AI Stuff (Part 2)
SCREENSHOT MAKE 1 (from 2nd supabase until upload in supabase)

After the signed contract is uploaded, the system automatically generates an AI-based profile for internal advertisements. Using the candidate’s submitted data, ChatGPT creates personalized content such as a welcome text, fun fact, and image prompt. Make takes the image promt and the profile picture from Supabase to create an edited fun profile picture. Taking the text and the picture a Google slide is being created and stored for later use.
SCREENSHOT WELCOME SLIDE 2

### 3.2.8. Informing the school and notify HR to remove job posting
<br> <ins> Make Scenario </ins>: Google Slides and AI Stuff (Part 3)
ADD PICTURE OF MAKE 4
Once the contracting process is finished, the system automatically sends a notification email to the corresponding school. The email contains essential information such as the student’s name and apprenticeship period.
ADD PICTURE OF MAIL
Directly after that the system automatically sends a notification to the HR department, informing them that the position has been filled. This allows HR to remove or deactivate the related job posting and keep recruitment platforms up to date.
ADD PICTURE OF MAIL 

## 3.3 Technologies 

| Tool  | Purpose |
| ------------- | ------------- |
| Camunda  |  Orchestrator of tasks. |
| Make  |  Scenario-making tool.  |
| Supabase  |  Database. |
| POST  |  XXX |
| Fill out form  |  Form. |


## 4. Final State

### 4.1 Conclusion

This project successfully demonstrated how the apprentice hiring and contracting process can be optimized through workflow automation and process standardization. By integrating Camunda, Make, Supabase, and AI-supported functionalities, several manual and repetitive tasks were automated, including data collection, contract generation, correction handling, stakeholder notifications, and onboarding preparation. The redesigned TO-BE process reduces administrative workload, minimizes errors, improves transparency between stakeholders, and creates a more efficient and user-friendly experience for both HR employees and candidates. Additionally, the implementation of validation mechanisms and centralized data management ensures greater consistency and compliance throughout the process.

### 4.2 Recommendations

For future improvements, the process could be further enhanced by integrating digital signature solutions to eliminate the need for manual contract uploads and speed up approvals. Additional security measures, such as encrypted document sharing and role-based access management, should also be considered to strengthen data protection and compliance. Furthermore, the AI-generated onboarding profiles and internal advertisement materials could be expanded with customizable templates and branding options. Finally, implementing analytics and monitoring dashboards would allow HR departments to track process performance, identify bottlenecks, and continuously optimize the workflow over time.
