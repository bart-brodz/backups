# backing up all photos 

This guide describes ho to perform a backup of all photos from:
- 'FOTO' directory of 'TOSHIBA 4TB' drive
- 'Photos' directory from Nextcloud

THIS IS A MANUAL PROCESS!

It should be executed periodically to keep the latest backup.

## Sources

This guide is based on the following documents:
- https://guides6475.rssing.com/chan-77553602/article11.html
- https://docs.hetzner.com/storage/storage-box/backup-space-ssh-keys/
- https://docs.hetzner.com/storage/storage-box/access/access-ssh-rsync-borg/

## Backup destination

- Hetzner Storage Box: `BX11` (1TB, 4,92E/mo) 
- location: `DE`
- box name:` storage-box-foto`
- server: `u525993.your-storagebox.de`
- username: `u525993`
- port: `23`

## SSH access to Storage Box

- machine: mint-desktop
- ssh keys:
    - location: `/home/bartb/.ssh/hetzner-storage-box`
        - `storage-box`
        - `storage-box.pub`

Test the connection:
```bash
ssh -i /home/bartb/.ssh/hetzner-storage-box/storage-box -p 23 u525993@u525993.your-storagebox.de 
```

## Backing up 'FOTO' data with rsync

Command:
```bash
rsync --progress -e 'ssh -p23 -i /home/bartb/.ssh/hetzner-storage-box/storage-box' --recursive /media/bartb/TOSHIBA_4TB/FOTO u525993@u525993.your-storagebox.de:/hom
```
Verification:

## Backup whole nextcloud

```bash
sync --progress -e 'ssh -p23 -i /home/bartb/.ssh/hetzner-storage-box/storage-box' --recursive /home/bartb/Nextcloud u525993@u525993.your-storagebox.de:/home/
```


