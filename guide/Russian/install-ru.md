﻿<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Windows на Xiaomi Pad 5

## Установка Linux

### Требования
- Мозги
  
- [rootfs.img.xz](https://mega.nz/folder/CVMGEAiB#7oazR3wpkKdAH2eZChtRTg) (рекомендуется Ubuntu-V0.91)

### Установка

#### Извлеките `rootfs.img` из `rootfs.img.xz`

#### Перезапустите планшет в fastboot для прошивки

#### Прошейте образ linux через fastboot
```cmd
fastboot flash linux <rootfs.img>
```
> Замените <rootfs.img> на путь к rootfs.img

#### Перезапуститесь в android для настройки дуалбута
```sh
fastboot reboot
```

## Готово!

### [Последний шаг: Установка дуалбута](dualboot-ru.md)