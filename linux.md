## Монтирование диска

1. Опредить UUID   
    ```
    sudo blkid
    ```

2. создать каталог монтирования 
    ```
    sudo mkdir /mnt/Shared /mnt/sdb1
    ```

3. в конец файла **/etc/fstab** добавить 
    - для NTFS:
    ```
    UUID="7ECCC7F5CCC7A62D" /mnt/Shared ntfs rw,nls=utf8,gid=plugdev,umask=0002 0 0
    ```

    - для FAT:
    
    ``` 
    UUID="355B-FE37" /mnt/TrendNet8Gb vfat rw,exec,codepage=866,nls=utf8,gid=plugdev,umask=0002,nofail,users 0 0
    ```
    - для ext4:
    
    ```
    UUID="bdc9dec8-7b0c-4d58-a626-644f8bdba99f" /mnt/sdb1 ext4 defaults
    ```
    
    Пользователь и группа, которым будут принадлежат файлы указываются параметрами
    ```
    uid=user 
    gid=plugdev
    ```
4. Примонтировать
    ```
    sudo mount -a
    ```
