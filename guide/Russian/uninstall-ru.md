<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">

# Linux на Xiaomi Pad 5

## Удаление

Если вы хотите удалить Linux, используйте данный упрощенный метод вместо ручного удаления разделов чтобы исключить риск ошибки.

Если вы хотите заблокировать загрузчик обратно, убедитесь что таблица разделов находится в заводском состоянии.

### Требования

- [ADB и Fastboot](https://developer.android.com/studio/releases/platform-tools)
- [gpt_both0.bin](https://timoxa0.su/share/nabu/manual/gpt_both0.bin)

### Восстановление GPT
> Замените ```<gpt_both0.bin>``` путём к файлу `gpt_both0.bin`.

```cmd
fastboot flash partition:0 <gpt_both0.bin>
```

### Очистите раздел `userdata` чтобы избежать цикличной перезагрузки и восстановить размер файловой системы
```cmd
fastboot -w
```
