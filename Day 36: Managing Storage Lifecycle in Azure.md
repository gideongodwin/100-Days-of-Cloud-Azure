## Day 36: Managing Storage Lifecycle in Azure

#### Task Details:
The Nautilus DevOps team needs to optimize data retention costs by automating the deletion of old blobs. They plan to implement Blob Lifecycle Management for a specific container in Azure Storage.

Task:
1) Create a Storage Account:

Name the storage account `devopsstor713`
Set the region to East US.
Use Locally-redundant storage (LRS) as the redundancy option.
2) Create a Blob Container:

Name the container `devops-container713`

3) Upload a File to the Container:

Upload the file named `tempfile.txt` to the container. The file is present under `/root` of the client host.
4) Configure Blob Lifecycle Management:

Apply a Lifecycle Management rule named `devops-del-rule` to the container `devops-container713` to delete blobs after `7` days of last modification.
5) Validation: Verify that the Lifecycle Management rule named `devops-del-rule` is correctly applied

#### STEPS:
1. Create a Storage Account:
    ```
    az storage account create \
        --name devopsstor713 \
        --resource-group kml_rg_main-635fac10477b4d90 \
        --location eastus \
        --sku Standard_LRS \
        --kind StorageV2
    ```
2. Create the Blob container named `devops-container713`
   ```
   az storage container create \
    --account-name devopsstor713 \
    --name devops-container713
   ```
3. Upload `tempfile.txt` from `/root`
   ```
   az storage blob upload \
    --account-name devopsstor713 \
    --container-name devops-container713 \
    --name tempfile.txt \
    --file /root/tempfile.txt
   ```
4. Create a lifecycle management policy to delete blobs older than 7 days
   ```
   cat > lifecycle-policy.json <<EOF
{
  "rules": [
    {
      "name": "devops-del-rule",
      "enabled": true,
      "type": "Lifecycle",
      "definition": {
        "filters": {
          "blobTypes": ["blockBlob"],
          "prefixMatch": ["devops-container713/"]
        },
        "actions": {
          "baseBlob": {
            "delete": {
              "daysAfterModificationGreaterThan": 7
            }
          }
        }
      }
    }
  ]
}
EOF ```

5. Apply the lifecycle policy to the storage account:
   ```
   az storage account management-policy create \
    --account-name devopsstor713 \
    --policy @lifecycle-policy.json \
    --resource-group kml_rg_main-635fac10477b4d90
   ```
6. Validate the Lifecycle Management Rule
   ```
   az storage account management-policy show \
    --account-name devopsstor713 \
    --resource-group kml_rg_main-635fac10477b4d90
   ```
