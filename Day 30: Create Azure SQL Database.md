## Day 30: Create Azure SQL Database

#### Task Details:
The Nautilus Devops team is strategizing the migration of a portion of their infrastructure to Azure. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition
Recently, they started working on creating and configuring some database instances on Azure.
For this task, create one `publicly` accessible Azure SQL Database instance along with the following details:

1) The name of the Azure SQL Database must be `devops-sqldb`

2) The server name must be `devops-server-19529` under `centralus`

3) The compute + storage configuration should be Basic (For less demanding workloads).

4) The backup storage redundancy should be Locally-redundant backup storage.

5) Set the login admin username to `devops-admin` and set an appropriate password.

6) Set the database size to 2 GiB.

7) Keep the rest of the configurations as `default` Finally, make sure the database is in the `Ready` state before submitting this task.

#### STEPS
1. Sign in to the [Azure Portal](https://portal.azure.com/)
2. On the Azure dashboard, select SQL Databases and select Create

<img width="958" height="341" alt="Screenshot 2026-03-02 195004" src="https://github.com/user-attachments/assets/e0c548c7-bf2c-425a-bedc-231b5c64c5b7" />

3. On the Basics tab, in the Database name field, enter `devops-sqldb`

<img width="869" height="505" alt="Screenshot 2026-03-jni201400" src="https://github.com/user-attachments/assets/88ec95df-918c-43eb-88d4-d1545522d629" />

4. On the Basics tab, under Server, select Create new and configure the server with the following settings:
```
Server name: devops-server-19529
Location: (US) Central US
Authentication method: Use SQL authentication
Server admin login: devops-admin
Password: Enter and confirm a strong password
```
<img width="960" height="864" alt="Screenshot 2026-03-02 201324" src="https://github.com/user-attachments/assets/31a1713e-2c77-4ea0-9aa6-fe833539f5b9" />

5. On the Basics tab, under Compute + storage, select Configure database, choose the Basic tier

<img width="718" height="76" alt="Screenshot 2026-03-02 203639" src="https://github.com/user-attachments/assets/0b5a23d8-0ad4-44c2-9344-7860bbb8be34" />

6. On the Basics tab, set Backup storage redundancy to Locally-redundant backup storage
<img width="957" height="698" alt="Screenshot 2026-03-02 201425" src="https://github.com/user-attachments/assets/af09c1f6-9839-4fc2-8519-267df57bb8c7" />

7. Review + Create





