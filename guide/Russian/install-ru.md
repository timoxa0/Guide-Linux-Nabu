﻿<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">

# Linux на Xiaomi Pad 5

## [←](prepare-ru.md) Установка Linux

### Требования
- Мозги

- Android с root-правами
  
- [Образ rootfs](./distros-ru.md)

- [Образ ядра](https://timoxa0.su/share/nabu/images/linux-6.1.10-nabu-gc033672c6f54.boot.img)

- [Установщик UEFI](https://timoxa0.su/share/nabu/uefi-installer-nabu.zip)

### Установка

#### Перезапустите планшет в fastboot для прошивки

#### Прошейте образ Linux через fastboot
```
fastboot flash linux <rootfs.img>
```
> Замените <rootfs.img> на путь к образу rootfs

#### Перезапуститесь в bootloader
```
fastboot reboot bootloader
```

#### Очистите dtbo
```
fastboot erase dtbo
```

#### Временно запустите Linux с ПК
```
fastboot boot <linux-boot.img>
```
> Замените <linux-boot.img> на путь к образу ядра

#### Пройдите первоначальную настройку и перезагрузите планшет в bootloader

#### Восстановите резервную копию dtbo
```
fastboot flash dtbo <dtbo.img>
```
> Замените <dtbo.img> на путь к резервной копии dtbo

#### Перезагрузите планшет в android
```
fastboot reboot
```

### Настройка dualboot

#### Прошейте установщик UEFI через Magisk или recovery
> После перезагрузки появляется меню, в котором вы можете ориентироваться, используя кнопки громкости и питания

### Готово!