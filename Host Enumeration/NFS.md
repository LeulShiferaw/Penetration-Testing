- Network file share - same as SMB although different protocol
- `cat exports` use this command to see the config of the nfs system
- Dangerous setting: rw, insecure, nohide, no_root_squash
- Use `sudo nmap 10.129.14.128 -p111,2049 -sV -sC` to scan the ports for nfs
- use `--script nfs*` to get more information
- use `showmount -e IP_ADDRESS` to see a list of the mounts
- use `sudo mount -t nfs IP_ADDRESS:/ ./mount_folder_name/ -o nolock` to mount on your system
- `sudo umount ./mount_folder_name` to unmount