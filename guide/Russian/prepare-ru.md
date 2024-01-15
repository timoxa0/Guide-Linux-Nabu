<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Linux на Xiaomi Pad 5

## Установка

### Подготовка устройства

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
> 
> НЕ ПЕРЕЗАГРУЖАЙТЕ ПЛАНШЕТ! Если вы считаете, что совершили ошибку, обратитесь за помощью в [чат Telegram](https://t.me/nabuwoa).
> 
>
>
>  Не запускайте все команды сразу, выполняйте их по очереди!
>
>
> Следуйте инструкции с осторожностью! В случае ошибки велика вероятность нарушить работоспособность устройства!

#### Прошейте vbmeta_disabled.img
```sh
fastboot flash vbmeta_ab <путь/к/vbmeta_disabled.img>
```

#### Запустите рекавери с компьютера при помощи команды
```sh
fastboot boot <recovery.img>
```

#### Перейдите в консоль recovery
```sh
adb shell
```

#### Размонтируйте /data
```sh
twrp unmount /data
```

#### Разширьте таблицу разделов
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

#### Создайте раздел efi (на будушие)
```
mkpart esp fat32 XGB YGB
```
> X замените на значение полученное в прошлом пункте \
> Y замените на X+1
> Если на андроид выделяем 16 GB, то команда выглядит так: `mkpart esp fat32 26.9GB 27.9GB`

#### Создайте раздел под linux
- для модели на 128 GB: `mkpart linux ext4 YGB 126GB`
- для модели на 256 GB: `mkpart linux ext4 YGB 254GB`
> Самените Y на X+1 \
> Если на андроид выделяем 16 GB, то команда выглядит так: \
> `mkpart linux ext4 27.9GB 126GB` для модели на 128 GB \
> `mkpart linux ext4 27.9GB 254GB` для модели на 256 GB

#### Проверьте, запускается ли Android
Просто перезапустите планшет и убедитесь, что Android запускается Если система не запускается или вы получили цикличную перезагрузку, используйте режим восстановления MIUI или другой режим восстановления чтобы отформатировать раздел `data`.

### [Следующий шаг: установка Linux](/guide/Russian/install-ru.md)
