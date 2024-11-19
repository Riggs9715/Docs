paru -S snapper snapper-rollback snap-pac-grub
sudo nvim /etc/snapper-rollback.conf
mountpoint to /.btrfsroot
sudo umount /.snapshots
sudo rmdir /.snapshots
sudo snapper -c root create-config /
sudo mount -a
sudo nvim /etc/snapper/configs/root
add riggs to ALLOWED_USERS
set timeline limits 
5 hour
7 day 
4 week
sudo systemctl enable snapper-timeline.timer
sudo systemctl enable snapper-cleanup.timer