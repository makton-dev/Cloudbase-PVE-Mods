# CloudBase working configs
Instead of getting a username as password from the clouddrive, we have the default "administrator" getting it's password updated to what is in the XML. This is only to get the VM up. Once the VM is up and connected to a saltstack master server, the "highstate" will be applied and Salt will uninstall Cloudbase, and clean the folders.

Otherwise, this configuration seems to work really well with Proxmox-VE

# BaseConfigDriveService.py
This python was modified to disconned the configdrive from the OS, but I think it's causing issues with the Unattended process so I would not recommend using it at this time.