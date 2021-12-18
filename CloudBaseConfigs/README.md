# CloudBase working configs
Instead of getting a username as password from the clouddrive, we have the default "administrator" getting it's password updated to what is in the XML. This is only to get the VM up. Once the VM is up and connected to a saltstack master server, the "highstate" will be applied and Salt will uninstall Cloudbase, and clean the folders.

Otherwise, this configuration seems to work really well with Proxmox-VE

# BaseConfigDriveService.py
This python was modified to disconned the configdrive from the OS, but I think it's causing issues with the Unattended process so I would not recommend using it at this time.

UPDATE 12/17/2021: Moved the volumeExtend plugin from unattended to regular cloudbase-init. Also a bit of cleanup. The BaseConfigDriveService.py that is on this repo is not being used ATM as I want to see the configdrive for tuning of the metadata. Also, changed my user on unattended.xml to match what I'm really doing. Since TF/Salt will be making the password changes and disabling the administrator, this just insures the administrator is accessable to the 2 managers.

Also, Added SetUserPublicSSHKeysPlugin to the cloudbase-init. This goes with the "cloudinit.pm" within this repo and the SSH metadata was added at that code. there is an issue on the cloudbase-init side for the ssh keys -> https://github.com/cloudbase/cloudbase-init/issues/85