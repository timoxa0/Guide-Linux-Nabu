<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Linux на Xiaomi Pad 5

## Подготовка устройства [→](install-ru.md)

### Требования:
- Мозги

- [Образ vbmeta](https://github.com/timoxa0/Guide-Linux-Nabu/releases/download/v0.0.1/vbmeta_disabled.img)

- [Образ рекавери](https://github.com/timoxa0/Guide-Linux-Nabu/releases/download/v0.0.1/orangefox.img)

- [ADB и Fastboot](https://developer.android.com/studio/releases/platform-tools)

### Примечание:
> [!WARNING]
> Все пользовательские файлы будут стерты! Создайте резервную копию, если это необходимо.
> 
> Эти команды были протестированы.
> 
> Игнорируйте ошибки `udevadm`.
> 
> Не выполняйте одну команду дважды.
>
> Не запускайте все команды сразу, выполняйте их по очереди!

#### Прошейте vbmeta_disabled.img
```sh
fastboot flash vbmeta_ab <vbmeta_disabled.img>
```
> Замените <vbmeta_disabled.img> на путь к vbmeta_disabled.img

#### Запустите ercovery с компьютера при помощи команды
```sh
fastboot boot <recovery.img>
```
> Замените <recovery.img> на путь к recovery.img

#### Перейдите в консоль recovery
```sh
adb shell
```

#### Размонтируйте /data
```sh
twrp unmount /data
```

#### Раcширьте таблицу разделов
```sh
sgdisk --resize-table 64 /dev/block/sda
```

#### Запустите редактор разделов parted
```sh
parted /dev/block/sda
```

#### Выведите список разделов командой `print` и запомните номер раздела userdata

```
...
31      10.9GB  126GB   126GB                userdata
...
```
> В данном случае раздел userdata имеет номер 31

#### Удалите раздел userdata командой `rm <номер>`
> Если раздел имеет номер 31, то команды выглядит так `rm 31`

#### Создайте новый раздел userdata командой
- Подставьте в формулу желаемый размер userdata: X = 10.9 + [размер в GB]
- Выполните команду `mkpart userdata ext4 10.9GB XGB`, заменив X на полученное значение
> Если на андроид выделяем 16 GB, то X = 10.9 + 16 = 26.9 \
> Соответственно, команда выглядит так: `mkpart userdata ext4 10.9GB 26.9GB`

#### Создайте раздел efi
```
mkpart esp fat32 XGB YGB
```
> X замените на значение полученное в прошлом пункте \
> Y замените на X+1
> Если на андроид выделяем 16 GB, то команда выглядит так: `mkpart esp fat32 26.9GB 27.9GB`

#### Создайте раздел под linux
- для модели на 128 GB: `mkpart linux ext4 YGB 126GB`
- для модели на 256 GB: `mkpart linux ext4 YGB 254GB`
> Замените Y на X+1 \
> Если на андроид выделяем 16 GB, то команда выглядит так: \
> `mkpart linux ext4 27.9GB 126GB` для модели на 128 GB \
> `mkpart linux ext4 27.9GB 254GB` для модели на 256 GB

#### Выйдите из parted
```
quit
```

#### Отформатируйте efi раздел
```
mkfs.fat -F32 -s1 /dev/block/sda33 -n ESPNABU
```

#### Выйдите из консоли recovery
```
exit
```

#### Сделайте резервную копию dtbo
```
adb shell "dd if=/dev/block/platform/soc/1d84000.ufshc/by-name/dtbo$(getprop ro.boot.slot_suffix) of=/tmp/normal_dtbo.img"; adb pull /tmp/normal_dtbo.img
```
> Резервная копия будет создана в текущей директории

#### Проверьте, запускается ли Android
Просто перезапустите планшет и убедитесь, что Android запускается. Если система не запускается или вы получили бутлуп, отформатируйте `data` в recovery.

### [Следующий шаг: установка Linux](/guide/Russian/install-ru.md)
