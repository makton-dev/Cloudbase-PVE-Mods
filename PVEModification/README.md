# Proxmox Cloudinit.pm
This was the file that modified to have DNS working with cloudbase-init on my Proxmox VE server farm. I took the nameservers and added them to a "default" variable which I apply to the first ethernet adapter (ETH0) when the network config is generated. This is only applied when the OS is windows as well, so linux will react no different.

UPDATE 12/17/2022: Added the VM name as the hostname in the configdrive metadata as hostname doesn't get changed without it. thanks to the Proxmox forum members for direction (https://forum.proxmox.com/threads/windows-cloud-init-working.83511/).

Have also added any SSH Public Keys to the metadata file as welll, but there is an issue on the cloudbase-init. Opened a case on it here -> https://github.com/cloudbase/cloudbase-init/issues/85