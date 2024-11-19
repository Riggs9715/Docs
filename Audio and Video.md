paru -S mesa lib32-mesa vulkan-intel lib32-vulkan-intel 
paru -S pipewire lib32-pipewire wireplumber
paru -S --asdeps pipewire-audio pipewire-alsa pipewire-pulse pipewire-jack lib32-pipewire-jack
systemctl enable --user pipewire
systemctl enable --user wireplumber
systemctl enable --user pipewire-pulse
paru -S blueman
sudo systemctl enable --now bluetooth
paru -S pavucontrol
