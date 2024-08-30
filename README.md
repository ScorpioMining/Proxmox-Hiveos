## Following the below steps will help enable Hiveos Mining on Proxmox VE

## Prepare Proxmox Host

Check for IOMMU
```
dmesg | grep -e DMAR -e IOMMU
```
Update /etc/modules
```
nano /etc/modules
```
Add following to /etc/modules and save
```
vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
```
Check if IOMMU remapping is enabled
```
dmesg | grep 'remapping'
```

Download latest [HiveOS](https://download.hiveos.farm/) image

```
wget https://download.hiveos.farm/history/hiveos-0.6-227-beta@240531.img.xz
```
Unzip image
```
unxz hiveos-0.6-227-beta@240531.img.xz
```

Import HiveOS image to VM \
- local-lvm is whatever the name of your storage is called \
- 114 - Change to your proxmox VM number 
```
qm importdisk 114 hiveos-0.6-227-beta@240531.img. local-lvm
```


