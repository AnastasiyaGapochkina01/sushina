# Конспект команд по LVM
```
# посмотреть phisical volumes
sudo pvs
# посмотреть volume groups
sudo vgs
# посмотреть logical volumes
sudo lvs

# посмотреть физические диски
lsblk
# посмотреть логическую структуру с подробностями
df -h
df -Th

# создать PV <disk> - диск или раздел, который отдаем под PV
sudo pvcreate <disk>
# создать VG <vgname> - имя группы, которую хотим создать; <pvname> - имя PV, из которого создаем VG
sudo vgcreate <vgname> <pvname>
# отрезаем logical volume <lvname> - имя логического тома; <vgname> - имя группы, от которой отрезаем;
sudo lvcreate -n <lvname> -L2G <vgname>
# создать ФС на новом разделе
sudo mkfs.ext4 /dev/<vgname>/<lvname>
# выяснить id полученного раздела
sudo blkid
# прописать автомонтирование
sudo nano /etc/fstab
  UUID=<uuid-lv> <mount-point> <type> <options> <dump> <check>

# Пример
sudo pvcreate /dev/sdb
sudo vgcreate local-vg /dev/sdb
sudo lvcreate -n tmp -L2G local-vg
sudo lvs
sudo blkid
# допустим UUID 477eaf46-6baf-43a9-8cc6-ab7d3650e607
sudo nano /etc/fstab
  UUID=477eaf46-6baf-43a9-8cc6-ab7d3650e607 /opt/tmp ext4 defaults 0 2
sudo mkdir /opt/tmp
sudo systemctl daemon-reload
sudo mount -a
df -Th
```
