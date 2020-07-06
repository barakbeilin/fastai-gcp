Share folder from win10 to ubuntu18 machine.
Choose windows shared folder using vmware gui.
Then on the vm enter:
```
sudo apt-get install open-vm-tools open-vm-tools-desktop
sudo  mkdir /mnt/hgfs
sudo vmhgfs-fuse .host:/ /mnt/hgfs/ -o allow_other -o uid=1000
```
Now you have the shaed folder on ```/mnt/hgfs```
