<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">

# Запуск Linux на Xiaomi Pad 5

## [←](./install-ru.md) Дуалбут с использованием switch2linux

### Требования
- Мозги

- Рутированный android

- Уже установленный Дinux
  
- [mklonimg.cmd (Windows)](https://git.timoxa0.su/timoxa0/mklonimg/raw/branch/main/mklonimg.cmd)

- [mklonimg.sh (Linux/macOS)](https://git.timoxa0.su/timoxa0/mklonimg/raw/branch/main/mklonimg.sh)

- [Python 3](https://www.python.org/downloads/)

- [Zip пакет linux-nabu](https://timoxa0.su/?dir=share/nabu/packages/v3)

### Создание boot образа

1. #### Востановите ваш boot (можете пропустить если запускали lon-tool с флагом -Q)

2. #### Скачайте mklonimg.cmd для Windows или mklonimg.sh для Linux/macOS

3. #### Установите Python 3 (на Windows отметьте Add Python 3.x to PATH или Добовить Python 3.x в PATH)

4. #### Скачайте zip пакет linux-nabu нужной версии

5. #### Распакуйте vmlinuz-6.1.10-nabu и dtb-6.1.10-nabu из /boot/efi внутри zip архива

6. #### Откройте cmd на Windows или терминал на Linux/macOS

7. #### Запустите mklonimg
##### Windows
```
.\mklonimg.cmd путь\к\vmlinuz путь\к\dtb
```
##### Linux/macOS
```
bash mklonimg.sh путь/к/vmlinuz путь/к/dtb
```

8. #### Образ будет создан в текущей папке с именем linux.boot.img

9. #### Следуйте гайду по установке switch2linux -> [ссылка](https://git.timoxa0.su/timoxa0/Switch2Linux-Nabu/src/branch/main/README-RU.md)

### Готово!
