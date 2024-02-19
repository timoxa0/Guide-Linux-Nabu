﻿<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Windows на Xiaomi Pad 5

## [←](prepare-ru.md) Установка Linux [→](dualboot-ru.md)

### Требования
- Мозги

- Android с root-правами
  
- [Образ rootfs](https://timoxa0.su/share/nabu/images) (ubuntu.img или arch.img)

- [Образ ядра](https://timoxa0.su/share/nabu/images/linux-6.1.10-nabu.boot.img)

- [Установщик UEFI](https://timoxa0.su/share/nabu/uefi-installer-nabu.zip)

### Установка

#### Перезапустите планшет в fastboot для прошивки

#### Прошейте образ linux через fastboot
```cmd
fastboot flash linux <rootfs.img>
```
> Замените <rootfs.img> на путь к ubuntu.img или arch.img

#### Перезапуститесь в bootloader
```sh
fastboot reboot bootloader
```

#### Очистите dtbo
```sh
fastboot erase dtbo
```

#### Временно запустите linux с ПК
```sh
fastboot boot <linux-boot.img>
```
> Замените <linux-boot.img> на путь к образу ядра

#### Пройдите первоначальную настройку и перезагрузите планшет в bootloader

#### Восстановите резервную копию dtbo
```sh
fastboot flash dtbo <dtbo.img>
```
> Замените <dtbo.img> на путь к резервной копии dtbo

#### Перезагрузите планшет в android
```sh
fastboot reboot
```

### Настройка dualboot

#### Прошейте установщик UEFI через Magisk или recovery
> После перезагрузки появляется меню, в котором вы можете ориентироваться, используя кнопки громкости и питания

### Готово!