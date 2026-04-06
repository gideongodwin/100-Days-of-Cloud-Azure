## Day 25 - Expanding and Managing Disk Storage

## Task Details:
The Nautilus DevOps team needs to expand the storage capacity of an existing virtual machine and add an additional `data disk` to support increased workloads.
This task requires resizing the existing VM disk and mounting a new data disk to the VM. As a member of the team, perform the following steps:

1) Expand the existing VM `nautilus-vm` disk from `32GiB` to `64GiB`

2) Also create a new standard HDD data disk named `nautilus-disk` of `64Gi` and mount the disk to VM `nautilus-vm` at location `/mnt/nautilus-disk`

## STEPS

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. From the Azure portal dashboard

3. Select the existing vm `nautilus-vm`

   <img width="679" height="354" alt="Screenshot 2026-02-20 093622" src="https://github.com/user-attachments/assets/96858428-cc73-4568-ae0a-10d225c9dc39" />

4. Select Stop, and confirm the action

5. Wait until the VM status changes to Stopped (deallocated)

   <img width="679" height="395" alt="Screenshot 2026-02-20 093650" src="https://github.com/user-attachments/assets/e64cf20f-37c0-408d-9bcb-ecc0fea27838" />

6. On the `nautilus-vm` page, under Settings, click on Disks.

   <img width="679" height="394" alt="Screenshot 2026-02-20 093935" src="https://github.com/user-attachments/assets/796aa091-bbcc-4f57-a84a-41cf8d252c95" />

7. Expand the existing VM `nautilus-vm` disk from `32GiB` to `64GiB`

   <img width="682" height="599" alt="Screenshot 2026-02-20 093959" src="https://github.com/user-attachments/assets/6380bd4e-153b-4350-84ff-91a5c0715f16" />

8. Under the Data disks section, click Create and attach a new disk

   <img width="675" height="177" alt="Screenshot 2026-02-20 094400" src="https://github.com/user-attachments/assets/7889e13c-a8f6-4cd7-bcf2-6e74a512020d" />

   <img width="693" height="64" alt="Screenshot 2026-02-20 095241" src="https://github.com/user-attachments/assets/2e833015-4169-401d-af20-642bf13ebbeb" />

9. Start the vm, and confirm it's running.

   <img width="676" height="328" alt="Screenshot 2026-02-20 095405" src="https://github.com/user-attachments/assets/e364e561-d308-439b-907a-f174acff2b7d" />

10. On the azure client, connect to the vm
   ```
   ssh azureuser@<vm-public-ip>
   ```

11. List Block Devices
   ```
   lsblk
   ```

12. Create a filesystem on the Disk
   ```
   sudo mkfs.xfs /dev/sda
   ```

13. Creates a directory that will be used to access the disk
   ```
   sudo mkdir /mnt/nautilus-disk
   ```

14. Attach the formatted disk to the directory
   ```
   sudo mount /dev/sda /mnt/nautilus-disk
   ```

15. Verify changes
   ```
   lsblk
   ```
