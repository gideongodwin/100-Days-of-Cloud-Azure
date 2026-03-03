## Day 31: Deploying and Managing a Web Application

#### Task Details:
The Nautilus DevOps team is tasked with deploying a Python-based web application on Azure. You need to create a web app using the following specifications:

1) The Web App name should be `devops-webapp`
2) It should be created in the `West US` region under the default resource group.
3) The publish option should be set to `Code`
4) The Runtime Stack should be `Python` with `Linux` as the operating system.
5) Create a new App Service Plan named `devops-learn-python` with the SKU `Basic B1`
6) Application Insights should be `disabled`
7) Add tags:
   `Name: WebAppLearning` \
   `Environment: Dev` 

#### STEPS:

1. Sign in to the [Azure Portal](https://portal.azure.com/)
2. Search for App Service Plan in the Azure portal’s global search bar, then select it from the results.

<img width="582" height="183" alt="Screenshot 2026-03-03 093318" src="https://github.com/user-attachments/assets/176af66d-3bdc-4d10-9a73-dd521d60b020" />
3. Click on Create
4. On the Basics tab, enter the following:
   - Name: `devops-learn-python`
   - OS: `Linux`
   - Region: `West US`

<img width="621" height="367" alt="Screenshot 2026-03-03 093438" src="https://github.com/user-attachments/assets/8dcb749f-6ba7-4df6-9dba-192dc5a4d1da" />

5. On the Tags tab, add the following:
   - Name: `WebAppLearning`
   - Environment: `Dev`
<img width="576" height="212" alt="Screenshot 2026-03-03 093511" src="https://github.com/user-attachments/assets/425043e1-d0b5-4cfc-a983-1f283fda72b1" />

6. Then Review + Create

7. Search for App Services in the Azure portal’s global search bar, then select it from the results.

<img width="576" height="208" alt="Screenshot 2026-03-03 093646" src="https://github.com/user-attachments/assets/f8536e38-f7e9-4e49-a6ce-c4a22e3e5555" />

8. Click on Create Web App

<img width="550" height="240" alt="Screenshot 2026-03-03 093656" src="https://github.com/user-attachments/assets/310b8485-1bd4-4123-a774-a25f77f8184e" />

9. On the Basics tab, enter the name of the web app: 
10. Ensure the Publish is set to `code`
<img width="580" height="431" alt="Screenshot 2026-03-03 093745" src="https://github.com/user-attachments/assets/864be9d8-3812-4dd4-8e68-ad7835fbc91c" />

11. Set the Runtime Stack to `Python`

<img width="593" height="296" alt="Screenshot 2026-03-03 093818" src="https://github.com/user-attachments/assets/ab95aa62-5f3b-4056-adc3-07a78efd73cf" />

12. On the Monitor + Secure tab, ensure Application Insights is disabled

<img width="588" height="242" alt="Screenshot 2026-03-03 093852" src="https://github.com/user-attachments/assets/16aa5e26-b207-47d3-96d1-cf1082b657b8" />

13. On the Tags tab, add the following:
   - Name: `WebAppLearning`
   - Environment: `Dev`

<img width="562" height="232" alt="Screenshot 2026-03-03 093912" src="https://github.com/user-attachments/assets/6e6cea45-fa8e-4626-9fbf-7ac760198422" />

14. Then Review + Create







