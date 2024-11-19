- edit the mkinitcpio conf file to add the resume hook then rebuild. This hook must be somewhere **after** the udev hook in the list.
```
sudo nvim /etc/mkinitcpio.conf
```

```
HOOKS=(base udev autodetect microcode modconf kms keyboard keymap consolefont block filesystems resume fsck)
```

```
sudo mkinitcpio -P
```

- edit grub config, adding resume=UUID=_UUID-of-swap=partition_ to the kernel parameters and regenerate the config
```
sudo nvim /etc/default/grub
```

```
GRUB_CMDLIN_LINUX_DEFAULT="loglevel3 quiet splash resume=UUID=fa46-462f-88f3-899061e948a2"
```

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```