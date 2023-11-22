# Export nfs directory 

1. On server you would like to export directory 
-``sudo dnf install nfs-utils`` 
-``systemctl enable --now nfs-server.service`` 
-``mkdir /driectory-exported``
-``ip a`` 
-``echo "/directory-exported *(rw,sync,no_root_squash)" >> /etc/exports``
-``systemctl restart nfs-server.service`` 
-``showmount -e`` #to verify


2. On server you would like to mount exported directory 
-``mkdir /directory-mounted`` 
-``echo "<ip_of_server_with_export>:/directory-exported  /directory-mounted nfs defaults 0 0" >> /etc/fstab``
-``mount -a`` 
-``ls -l /directory-mounted`` #to verify 

# Create AutoFS

1. On first server create export directory

-``sudo dnf install nfs-utils``
-``systemctl enable --now nfs-server.service``
-``mkdir /driectory-exported``
-``ip a``
-``echo "/directory-exported *(rw,sync,no_root_squash)" >> /etc/exports``
-``systemctl restart nfs-server.service``
-``showmount -e`` #to verify


2. On second server 

-``echo "exports /etc/auto.nfs" >> /etc/auto.master`` 
-``echo "test -fstype=nfs,rw,soft,intr  <ip_from_exported_server>:/<name_of_exported_share>" >> /etc/auto.nfs``
-``sudo systemctl restart autofs.service``
-``cd /exports/test ; ls -l``
