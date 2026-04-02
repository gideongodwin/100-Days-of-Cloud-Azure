## Day 19: Convert Public Azure Blob Container to Private

## Task Details:

The Nautilus DevOps team has been using Azure Blob Storage to manage their data. Recently, they realized that one of their containers, currently public, needs to be restricted for internal use only. Your task is to convert a public Azure Blob container to private.

## Steps:

Two blob containers named `nautilus-container-23484` and `nautilus-priv-861` are available in the `eastus` region within the storage account `nautilusst16449`.
The `nautilus-container-23484` is currently public, and `nautilus-priv-861` is private.

- Convert the blob container `nautilus-container-23484` from public to private while leaving `nautilus-priv-861` unchanged.

- Make sure the access level for `nautilus-container-23484` is set to `private` with no public access

## Steps:

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. From the Azure portal dashboard, Select Storage Accounts

3. On the Storage accounts page, select `nautilusst16449` from the list

   <img width="676" height="318" alt="548107396-dfb8d23e-5371-434b-8c53-4c62cf588ba7" src="https://github.com/user-attachments/assets/df092894-be7f-4400-bea9-6d1cd0ef05cd" />

4. In the storage account menu, under Data storage, select Containers

<img width="650" height="437" alt="548112660-3663c54b-c0cd-4344-80b4-79f47fee8223" src="https://github.com/user-attachments/assets/2e126177-1e4f-4695-a3be-49cef572bb81" />

5. Select `nautilus-container-23484` from the list of containers, and then select Change access level

<img width="934" height="426" alt="548127270-50d3e039-a684-44c3-adfb-1a5b7330365b" src="https://github.com/user-attachments/assets/492b5600-54ca-4368-b06e-b644d047f5bd" />

6. In the Change access level pane, set Public access level to Private (no anonymous access).

7. Select OK to save the changes.

<img width="682" height="489" alt="Screenshot 2026-02-11 083438" src="https://github.com/user-attachments/assets/7acaf152-d130-4435-b3fe-7ae39d55293f" />




 
