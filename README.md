# Cloudbase-PVE-Mods
Modified Files for CloudBase-init and Proxmox PVE in support of Terraform/SaltStack automation

## Purpose
This was created for me to keep notes of the custom pieces for automating Windows server builds from Proxmox using Terraform/Saltstack. This repo was made public as nothing in it is sensitive and seems to solves issues others have seen.

## Idea
For this build, was not worried about passing a password through the clouddrive as the admin password would be changed by Salt during the configuration process. So, having a "generic" admin password no just fine in this case. Thus, the admin password is in the cloudinit-unattended XML, which removes the need to mess with PVE at this time, though I might wrap around and open that option later on.

The main issue is the DNS. Seems Proxmox cloudinit.pm likes to keep the DNS servers on the loopback interface, which cloudbase will not use in this way. Instead I take the dns servers from the loopback interface and add them to the first ethernet adapter (eth0) as well. This solves the DNS issues for the Windows VM on Prox.

Lastly, the clouddrive stays as a CDrom. I have the code to "disconnect" the CD but the drive remains which is of no help. Since there is no sensitive data in the clouddrive (it's in the XML), don't really care if the clouddrive is seen at this point. Will be looking at a way to remove that device a bit later down the line.
