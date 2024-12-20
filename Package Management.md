- clone the paru git repo from the AUR, build it and delete the cloned directory
```
git clone https://aur.archlinux.org/paru.git
cd paru makepkg -si
cd ~
rm -rf paru
```

- edit the pacman.conf file, uncomment Color ParallelDownloads and the multilib repo and add ILoveCandy
```
sudo nvim /etc/pacman.conf


# Misc options
#UseSyslog
Color
#NoProgressBar
CheckSpace
#VerbosePkgLists
ParallelDownloads = 5
DownloadUser = alpm
#DisableSandbox
ILoveCandy

...

[multilib]
Include = /etc/pacman.d/mirrorlist
```

- install reflector and edit its config file to change the latest filter to age, as well as changing the sort from age to rate. Also uncomment the country option and change it to GB
``` 
paru -S reflector
sudo nvim /etc/xdg/reflector/reflector.conf

... 
-- protocol https
-- country GB
-- age 6
-- sort rate
```

 - enable the reflector service to update the mirrors on boot
```
sudo systemctl enable reflector.service
```

- install pacman-contrib and enable the paccache timer to clean the pacman cache weekly. this will remove cached versions except for the most recent 3
```
paru -S pacman-contrib
sudo systemctl enable paccache.timer
```
