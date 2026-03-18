## Day 42 - Backup and Delete Azure Storage Blob Container

## Task Details:

The Nautilus DevOps team is currently engaged in a cleanup process, focusing on removing unnecessary data and services from their Azure environment. \
As part of the migration process, several resources were created for one-time use only, necessitating a cleanup effort to optimize their Azure environment.

A private blob container named `nautilus-blob-15245` already exists in the southcentralus region under storage account `nautilusst18708`

1) Copy the contents of `nautilus-blob-15245` blob container to the `/opt` directory on the azure-client host (the landing host once you load this lab).

2) Delete the blob container `nautilus-blob-15245` from the storage account.

## Steps:
1. Copy blob contents to `/opt`
```
az storage blob download-batch \
  --account-name nautilusst18708 \
  --source nautilus-blob-15245 \
  --destination /opt/
```
   > You can verify with `ls -l /opt/`

2. Delete the container
```
az storage container delete \
  --name nautilus-blob-15245 \
  --account-name nautilusst18708
```
