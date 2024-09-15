# Part 1. Установка ОС

## Вывод команды cat /etc/issue:
![Screenshot 1](part1-full.png)

Ввод команды:
```bash
sudo nano /etc/hostname
```
Замена названия в редакторе и сохранение файла.  
Применение изменений:
```bash
sudo hostname "cat /etc/hostname"
```

## Установка часового пояса
Находим название часового пояса:
```bash
timedatectl list-timezones | grep Moscow
```
![Screenshot 1](screenshot1.png)

```bash
Europe/Moscow
```
Устанавливаем часовой пояс:
```bash
sudo timedatectl set-timezone Europe/Moscow
```