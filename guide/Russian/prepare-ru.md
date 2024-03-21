<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Linux на Xiaomi Pad 5

## Подготовка устройства [→](install-ru.md)

### Требования:
- Мозги

- [Образ vbmeta](https://timoxa0.su/share/nabu/vbmeta_disabled.img)

- [Образ рекавери](https://timoxa0.su/share/nabu/orangefox.img)

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

#### Перезагрузите планшет в fastboot

#### Прошейте vbmeta_disabled.img
```
fastboot flash vbmeta_ab <vbmeta_disabled.img>
```
> Замените <vbmeta_disabled.img> на путь к vbmeta_disabled.img

#### Запустите recovery с компьютера при помощи команды
```
fastboot boot <recovery.img>
```
> Замените <recovery.img> на путь к recovery.img

#### Выполните переразметку
```
adb shell partition [размер раздела под linux в GB]
```

#### Сделайте резервную копию dtbo
```
adb shell backupdtbo
adb pull /tmp/dtbo.img
```
> Резервная копия будет создана в текущей директории

#### Проверьте, запускается ли Android
Просто перезапустите планшет и убедитесь, что Android запускается. Если система не запускается или вы получили бутлуп, отформатируйте `data` в recovery.

### [Следующий шаг: установка Linux](/guide/Russian/install-ru.md)
