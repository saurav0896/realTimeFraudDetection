# Real-Time Fraud Detection, Auto Incident Creation & Remediation
This is a complete solution on Real Time Fraud Detection , Analysis , Auto Incident Creation &amp; Remediation on any e-commerce portal developed on top of Microsoft Azure Tech Stack. Checks every event on portal and then analysis whether it is fraudulent or not 

## Solution Architecture
![](Images/RFTAAR.jpg)

## Tech Stack Used
1. Azure Event Hub
2. Azure Stream Analytics
3. Azure Functions
4. Azure Data Storage
5. Power BI
6. Service Now
7. Ansible

## Working (Data Flow)
1. User based events gets captured from e-commerce protal to Azure Event Hub
2. Azure Event Hub streamline those data to Azure Stream Analytics where every data is anaylized
3. After Processing Azure Stream Analytics pass those fraudulent data to Azure Functions and Azure Power BI (can also add storage if needed)
4. Azure Function Capture those data and create a service incident in Service Now with Fraud details and assign it to IT Security Group for further action
5. Azure Function also add fraud data to a temporary block list created in Service Now , which can be used for further references
6. Azure PowerBI capture the output of Azure Stream Analytics and then show the fraud data in a Real Time Dashboard in form of Charts and tables
7. Web Portal constantly check the block list in Service Now to check the user is fraudulent or not

## Solution Benefit
1. Cloud based solution thus can be easily scale up and down
2. Created after observing current IT Service Managment Methodology and thus can be integrated with any bussiness usecase across any  bussiness tower
3. Kept Current IT Process Automation and zero effort deployment in mind.
4. Reduces Man Power to handle the request as detection and remediation both are automation 
