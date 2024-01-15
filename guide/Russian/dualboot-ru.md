<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Windows на Xiaomi Pad 5

## Двойная загрузка Android и Linux

### Требования

- Мозги

- Android с root-правами

- [boot-loader.tar.xz](https://mega.nz/folder/CVMGEAiB#7oazR3wpkKdAH2eZChtRTg) (рекомендуется Ubuntu-V0.91)

### Android side of Dual Boot

1) Установите [`linuxswitch.apk`](https://github.com/timoxa0/Switch2Linux-Nabu/releases/download/v1.0.2/linuxswitch.apk) на устройство.
2) Откройте программу и выдайте root-права
3) Нажмите "Dump android images"
4) Сохраните `android.boot.img` и `andoid.dtbo.img` на комьбтер из `/sdcard/linux/`
5) Распакуйте `boot-loader.tar.xz`
6) Достаньте из распакованного aрхива `boot_xiaomi-nabu_sda33.img` и, назвав его `linux.boot.img`, положите в `/sdcard/linux/`
7) Перезагрузитесь в linux, нажав "Switch to Linux"


### Linux side of Dual boot

1) Скачайте [`s2a.zip`](https://github.com/timoxa0/Switch2Linux-Nabu/releases/download/v1.0.1/s2a.zip)
2) Распакуйте `s2a.zip` в Linux
3) Положите android.boot.img и andoid.dtbo.img в папку s2a
4) Запустите терминал в папке с install.sh и выполните команду 
    ```console
    sudo ./install.sh
    ```
5) Перезагрузитесь в android, запустив "Switch2Android" и меню приложений

## Готово!
