# End-to-End Hiring & Contracting Automation

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
Obtaining an apprenticeship is generally considered moderately challenging, as the process combines elements of a job search with certain academic requirements. While there are many apprenticeship positions available in Switzerland, competition can be strong in more popular fields such as business or healthcare, making it harder for some applicants to secure a place. Students are typically required to submit a CV, a motivation letter, and school reports, and need to pass interviews where their attitude and suitability are evaluated. 

Our role as Human Resources is to support the company in managing this process by handling applications efficiently and making the experience as flexible and user-friendly as possible.

In this project, we focus on the improvement of the hiring and contracting process. This includes mapping the journey from the moment a candidate is selected, to their signing of the contract, up to the successful filling of the position. The current process requires extensive verification to ensure compliance with federal and cantonal regulations, as well as applicable collective labor agreements (Gesamtarbeitsverträge), resulting in a significant administrative workload for employees.

## 1.4 Use Case & Scope

The case focuses on the end-to-end hiring and contract management process for apprentices, from candidate selection to contract signing and onboarding preparation. The process involves multiple stakeholders, including HR, hiring managers, candidates, and, where applicable, legal guardians. It requires strict compliance with federal and cantonal regulations, as well as applicable collective labour agreements (Gesamtarbeitsverträge).

Currently, the process is characterized by:

- Multiple manual document exchanges
- Repeated compliance and document verification steps
- Iterative feedback loops between stakeholders
- Manual contract creation and validation

The objective of this initiative is to analyze, standardize, and automate the process to improve efficiency, ensure compliance, and enhance the overall experience for both HR and the candidates.

Out of scope are activities related to candidate sourcing (including job postings and candidate outreach), interviews and evaluations, and post-onboarding processes. Payroll management and any changes to legal or regulatory frameworks are also excluded.

# 2. AS IS
<img width="9234" height="2640" alt="Hiring_Apprentice_AS-IS" src="Hiring_Apprentice_AS-IS.png" />

## 2.1 Stakeholders

XXX

## 2.2 Limitations in the AS-IS process
The AS-IS process for hiring apprentices in Switzerland is built around paper forms, manual data entry, and sequential coordination across multiple parties. Every step depends on a single HR contact chasing documents, re-entering contract details by hand, and personally triggering each follow-up action in turn. The result is a process that is slow to complete, sensitive to errors, and difficult to scale — particularly when a guardian signature or a late correction throws the whole sequence off course.

### 1. Paper-based intake
The process starts with physical or email-attached documents that must be manually sent, completed, and returned, introducing delays before HR can even begin.
### 2. Manual contract creation
Every hire requires HR to look up and re-enter occupation codes, salary bands, and duration from the cantonal VET template, with no reuse of prior data or smart defaults.
### 3. Late error detection
Contract mistakes only surface during the review stage, well into the process, triggering a correction feedback loop that sends work back to HR and restarts the clock.
### 4. Fragmented multi-party coordination
The candidate, guardian (for minors), and HR each operate in separate lanes with no shared digital workspace, meaning every cross-party step relies on manual communication and follow-up.
### 5. Disconnected close-out tasks 
Once the contract is signed, HR must manually trigger each wrap-up action in sequence: saving to the system, creating a new entry, removing the job posting, and informing the school — none of which are linked or automated.

# 3. TO BE

<img width="7980" height="2595" alt="Bild" src="https://github.com/user-attachments/assets/e2f3c814-7a68-4367-8a89-71d53ce95df6" />

## 3.1 Process Optimization

- Set up of Google forms to have standardized input 

## 3.2 Automation

- DMN table automation for salary calculation
- Population of the template contract from information received from candidate and the salary from DMN
- Set up of automatic sending to guardians for candidates under 18
- Automatic upload of contract once approved
- Generation of AI profile (for the internal ads)
- Informing the school
- Notification of HR to remove job posting

## 3.3 Technologies 

a. Camunda 
XXX

b. Make
XXX

c. Supabase
XXX


## 4. Final State

### 4.1 Conclusion

### 4.2 Recommendations

XXX
