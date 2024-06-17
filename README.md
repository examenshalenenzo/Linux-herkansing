# Linux-herkansing

# Open konsole and become root
su
# Enter the root password when prompted

# Navigate to /home directory
cd /home

# Create directories Administratie and Verkoop
mkdir "Mapnaam1"
mkdir "Mapnaam2"

# Create groups administratie and verkoop         LET OP: Mapnamen met hoofdletter groepnamen zonder
groupadd "groepnaam1"
groupadd "groepnaam2"

# Change the group ownership of the directories
chgrp "groepnaam1" "Mapnaam1"
chgrp "groepnaam2" "Mapnaam2"

# Set the appropriate permissions for the directories
chmod 070 "Mapnaam1"
chmod 070 "Mapnaam1

# Add users cora and jan
useradd "User1"
passwd "wachtwoord1"
# Enter the password twice (e.g., Welkom01)

smbpasswd -a "User1"
# Enter the Samba password twice (e.g., Welkom01)

useradd "User2
passwd "wachtwoord2"
# Enter the password twice (e.g., Welkom01)

smbpasswd -a "User2"
# Enter the Samba password twice (e.g., Welkom01)

# Add users to their respective groups
usermod -aG "groepnaam1" "User1"
usermod -aG "groepnaam2" "User2"

# Start the Samba service
systemctl start smb.service

# Stop the firewall service
systemctl stop firewalld.service

# Edit the Samba configuration file
vi /etc/samba/smb.conf

# Add the following lines to the smb.conf file:
# Press 'i' to enter insert mode in vi editor
[Mapnaam1]
    path = /home/Mapnaam1
    writeable = yes

[Mapnaam2]
    path = /home/Mapnaam1
    writeable = yes

# Save and exit the vi editor
# Press ESC, then type :wq! and press Enter

# Restart the Samba service
systemctl restart smb.service
