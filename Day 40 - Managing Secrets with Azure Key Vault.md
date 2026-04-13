## Day 40: Managing Secrets with Azure Key Vault

## Task Details:

The Nautilus DevOps team is focusing on improving their data security by using Azure Key Vault. Your task is to create a `Key Vault` with an RSA key and manage the encryption and decryption of a pre-existing sensitive file using this key.
Specific Requirements:

- Create a Key Vault:
    - Name the Key Vault `devops-30993`
    - Create the vault in the `East US` region.
    - Use the `Standard` pricing tier.
    - Set Soft Delete retention to `7 days`
    - Use the `Vault access` policy permission model.
    - Configure an access policy that allows `Get, List, Encrypt, and Decrypt` permissions for the lab identity.

- Create an RSA Key:
    - Create a key named devops-key within the Key Vault.
    - Key type: `RSA`
    - RSA key size: `4096`
    - Leave all other settings as default.
    - Encrypt the Sensitive Data:

- Use the key to encrypt the provided `SensitiveData.txt` file (located in /root/) on the azure-client host.

- Use the `RSA-OAEP` algorithm.

- Base64 encode the plaintext before encryption.

- Save the encrypted version as `EncryptedData.bin` in the `/root/` directory.

> If you encounter a permissions error, retrieve the Service Principal ID using: `az account show --query user.name -o tsv` and grant the required Key Vault permissions.

- Verify Decryption:
    - Decrypt `EncryptedData.bin`
    - Base64 decode the decrypted output.
    - Save the result as `DecryptedData.txt` in  ``/root/
    - Ensure the decrypted file matches the original `SensitiveData.txt`
    - Ensure that the Key Vault and key are correctly configured. The validation script will test your configuration by decrypting the EncryptedData.bin file using the key you created.

## Steps:

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. Search for and select Key Vaults.

    <img width="740" height="304" alt="Screenshot 2026-03-16 210124" src="https://github.com/user-attachments/assets/9938b8b1-f390-43a9-9833-a717d2c38002" />

3. From the Key Vaults dashboard, click on  +create

4. On the Basics tab, configure the following:

    <img width="758" height="660" alt="Screenshot 2026-03-16 223008" src="https://github.com/user-attachments/assets/3bf91a14-8139-434e-9d40-0d57158e37f3" />
    
    <img width="800" height="354" alt="Screenshot 2026-03-16 223016" src="https://github.com/user-attachments/assets/eefbbfd2-64a7-4dfb-880c-dda23f704a8e" />

5. On the Access configuration tab, choose Vault access policy.

    <img width="889" height="789" alt="Screenshot 2026-03-16 223049" src="https://github.com/user-attachments/assets/26f8f986-3be4-4f25-b385-cd6cbf70f723" />

6. Review + Create

7. Once Deployment is complete, go to the key vault resource named `devops-30993`

8. Select Objects > Keys > + Generate/Import

    <img width="664" height="546" alt="Screenshot 2026-03-16 223311" src="https://github.com/user-attachments/assets/98e21fb4-40c8-40e5-966d-a57c3c78cf57" />

9. Enter a Key name, set RSA size to `4096`, then Create.

10. On the Azure CLI, retrieve the Service Principal ID
    ```
    az account show --query user.name -o tsv
    ```

11. Select Access policies, Click on the `+ Create`  and configure the following

    <img width="749" height="393" alt="Screenshot 2026-03-16 223711" src="https://github.com/user-attachments/assets/b0af72aa-e30b-4e7e-91e5-b44fe07659f0" />
    
    <img width="941" height="825" alt="Screenshot 2026-03-16 223727" src="https://github.com/user-attachments/assets/00d04d6c-5549-4548-a69e-645feefc86ce" />
    
    <img width="813" height="664" alt="Screenshot 2026-03-16 223818" src="https://github.com/user-attachments/assets/7c2e9202-5642-4c46-8bce-f53ff4065f80" />

12.  Review + Create

13. On the Azure CLI, convert the `SensitiveData.txt` file to base 64
    ```
    base64 /root/SensitiveData.txt > /root/plaintext.b64
    ```

14. Encrypt the `SensitiveData.txt` file
    ```
    az keyvault key encrypt \
     --vault-name devops-30993 \
     --name devops-key \
     --algorithm RSA-OAEP \
     --value "$(cat /root/plaintext.b64)" \
     --query result \
     -o tsv > /root/EncryptedData.bin
    ```

15. Decrypt the file
    ```
    az keyvault key decrypt \
    --vault-name devops-30993 \
     --name devops-key \
     --algorithm RSA-OAEP \
     --value "$(cat /root/EncryptedData.bin)" \
     --query result \
     -o tsv > /root/decrypted.b64
    ```

16. Convert Back to Original Text and Verify data 
    ```
    base64 --decode /root/decrypted.b64 > /root/DecryptedData.txt
    diff /root/SensitiveData.txt /root/DecryptedData.txt
    ```

