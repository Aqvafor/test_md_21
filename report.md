# Part 1. Установка ОС

- Вывод команды `cat /etc/issue`:
![Screenshot 1](part1-full.png)

# Part 2. Создание профиля

- Вызов команды для создания пользователя:
![Screenshot 2](part2-min1.png)
![Screenshot 3](part2-min2.png)
![Screenshot 4](part2-min3.png)

- Вывод команды `cat /etc/passwd`:
![Screenshot 5](part2-ful2.png)


# Part 3. Настройка сети ОС

- Смена названия машины user-1:
![Screenshot 6](part3-min1.png)

- Установка часового пояса:
![Screenshot 7](part3-min2.png)

- Вывод названий сетевых интерфейсов:
![Screenshot 8](part3-min3.png)
enpOs3 - Это сетевой адаптер Ethernet
lo (loopback device) - это виртуальный интерфейс, который служит для подключения по сети к текущей машине. Он есть по умолчанию в Linux. С этим интерфейсом всегда связан адрес 127.0.0.1 и имя localhost.

- Получение ip адреса машины от DHCP сервера:
![Screenshot 9](part3-min4.png)
DHCP — это протокол прикладного уровня, который помогает назначать IP-адреса устройствам при подключении к серверу. Протокол DHCP автоматизирует выдачу адресов, а также их передачу следующим пользователям после отключения устройств или их перехода из одной подсети в другую

- Внешний ip-адрес шлюза (ip) и внутренний IP-адрес шлюза (gw):
![Screenshot 10](part3-min5.png)
`ip = 10.0.2.2`
`gw = 95.104.188.195`

- Статичные настройки ip, gw, dns:
`sudo nano /etc/netplan/00-installer-config.yaml`
![Screenshot 11](part3-min6-2.png)

- Перезагрузка и проверка ip, gw, dns:
`reboot`
![Screenshot 12](part3-min7.png)
Все изменения настроек после перезагрузки машины остались.


- Перезагрузка и проверка ip, gw, dns:
`reboot`
![Screenshot 13](part3-min8.png)


# Part 4. Обновление ОС

- Команды:
 `sudo apt update`
 `sudo apt upgrade`
![Screenshot 14](part4-min1.png)

- Повторный запуск upgrade:
![Screenshot 15](part4-min2.png)


# Part 5. Использование команды sudo

- Разрешение пользователю, выполнять команду sudo:
![Screenshot 16](part5-min1.png)

- sudo - это утилита, которая позволяет выполнять команды от имени суперпользователя root, либо других пользователей. Правила используемые sudo для принятия решения о предоставлении доступа, находятся в файле /etc/sudoers.

- Изменение hostname ОС от имени пользователя new_obduliar:
![Screenshot 17](part5-min2.png)

- Перезагрузка машины и проверка, что hostname, остался перемеинованным:
 `reboot`
![Screenshot 18](part5-min3.png)


# Part 6. Установка и настройка службы времени

- Время часового пояса, и команда `timedatectl show`:
![Screenshot 19](part6.png)
 Вывод содержит `NTPSynchronized=yes`


# Part 7. Установка и использование текстовых редакторов.

- Так как vim и nano уже установлены на системы, третьим редактором установил Neo Vim:
`sudo apt install neovim`

- Создание файлов в редакторах:
`vim test_vim.txt` Для выхода с сохранением: `esc` + `:wq`
![Screenshot 20](part7-vim.png)

`nano test_nano.txt` Для выхода с сохранением: `ctrl+o` + `enter` + `ctrl+x`
![Screenshot 21](part7-nano.png)

`nvimtest_nvim.txt` Для выхода с сохранением: `esc` + `:wq`
![Screenshot 22](part7-nvim.png)


# Part 8. Установка и базовая настройка сервиса SSHD.

- Установка службы SSHD: `sudo apt install openssh-server`
- Установка службы SSHD: `sudo apt install openssh-server`
`sudo apt install neovim`
![Screenshot 23](part8-min1.png)

- Перенастройка службы SSHD на порт 2022:
![Screenshot 24](part8-min3.png)

- Перезапуск ssh:
![Screenshot 25](part8-min4.png)


- Поиск наличия процесса sshd:
![Screenshot 26](part8-min5.png)
Утилита ps предназначена для вывода процессов на экран.
Ключ -e выводит все процессы


- Перезагрузка машины: `reboot`
- Установка `net-tools` для команды `netstat`:
![Screenshot 27](part8-min6.png)

- Вывод команды `netstat -tan` содержит `tcp 0 0 0.0.0.0:2022 0.0.0.0:* LISTEN`:
![Screenshot 28](part8-min7.png)
Ключи:
t - Отображние сокетов только по tcp протоколу.
a - Показывает прослушиваемые и непрослушиваемые сокеты.
n - ОТображение нумерованных адресов вместо именованых (ip и порт вместо dns имен)
Столбцы:
Proto - Протокол (tcp, udp, udpl, raw), оспользуемый сокетом 
Recv-Q - Количество байт, которые не были скопированы пользовательской программой, подключенной к данному сокету.
Send-Q - Количество байт, которые не были распознаны удаленным хостом.
Local Address - Локальный адрес и опрт сокета
Foreign Address - Удаленный адрес и порт сокета.
State - Состояние сокета. Ячейка может быть пустая для RAW, UDP и UDPLite.
начение 0.0.0.0 - прослушиваются все адреса установления соеденения.


# Part 9. Установка и использование утилит top, htop.

- Утилита `top` по умолчанию установлена:
![Screenshot 29](part9-1.png)
uptime - 7 min
количество авторизованных пользователей - 1
общая загрузка системы - 0% за минуту, 1% за 5 минут, 0% за 15 минут
общее количество процессов - 96
загрузка cpu - 0.0
загрузка памяти 1971.6 total (142.3 used)
режим сортировки входится с помощью комбинации `shift + f`, для сохранения сортировки нужно нажать `s`, для выхода `q`
pid процесса занимающего больше памяти 666 - snapd
![Screenshot 30](part9-mem.png)
pid процесса, занимающего больше всего процессорного времмени  1 - system  
![Screenshot 31](part9-cpu.png)


- Использование `htop`:
Сортировка по PID
![Screenshot 32](part9-htopPID.png)

Сортировка по PERCENT_CPU
![Screenshot 33](part9-htopPercent_CPU.png)

Сортировка по PERCENT_MEM
![Screenshot 34](part9-htopPercent_MEM.png)

Сортировка по ВРЕМЕНИ
![Screenshot 35](part9-htopTIME.png)

Поиск по sshd
![Screenshot 36](part9-sshd.png)

Поиск  syslog
![Screenshot 37](part9-syslog.png)

Добавление вывода с hostname, clock, uptime
![Screenshot 38](part9-clockUptimeHostname.png)


# Part 10. Использование утилиты fdisk.

- Команда `fdisk -l`:
![Screenshot 39](part10.png)
Данные о жестком диске:
Название:/dev/sda VBOX HARDDISK
Размер: 25 GiB
Количество секторов: 52428800
Размер swap: 2Gib (`swapon -s`)


# Part 11. Использование утилиты df.

- Команда `df /` для корневого раздела в байтах:
![Screenshot 40](part11-New-df.png)
Размер раздела: 11758760
Размер занятого пространства: 4884804
Размер свободного пространтства: 6254848
Процент использования: 44

- Команда `df /` для корневого раздела в байтах:
![Screenshot 41](part11-New-dfTh.png)
Размер раздела: 12G
Размер занятого пространства: 4,7G
Размер свободного пространтства: 6.0G
Процент использования: 44
Тип файловой системы: ext4 (журналируемая файловая система)


# Part 12. Использование утилиты du.

- Команда `du`:
Флаг `-s` - означает "summary" (суммарный). Она показывает общее использование дискового пространства для указанного каталога, без детального отображения каждого файла или подкаталога внутри него
Флаг `-b` - означает "bytes" (байты). Она выводит размер в байтах, что позволяет получить более точное значение размера файлов или каталогов
Флаг `-h` - означает "human-readable" (удобочитаемый формат). Она преобразует вывод в удобочитаемый формат, используя сокращения для единиц измерения (например, K, M, G для килобайт, мегабайт и гигабайт).
Размер папки `/home`
![Screenshot 42](part12-2.png)

Размер папки `/var`
![Screenshot 43](part12-3.png)

Размер папки `/var/log`
![Screenshot 44](part12-4.png)

Размер всего содержимого `/var/log/*`
![Screenshot 45](part12-5.png)


# Part 13. Установка и использование утилиты ncdu.

- Установка утилиты  `apt install ncdu`:
![Screenshot 46](part13-1.png)


- Команда  `ncdu -x /`
![Screenshot 47](part13-2.png)
Размер папки `/home`: 108.0 KiB
Размер папки `/var`: 812.3 MiB

![Screenshot 48](part13-3.png)
Размер папки `/var/log`: 43.3MiB


# Part 14. Работа с системными журналами.

- Открытие для просмотра:  `less /ver/log/...`
`less /ver/log/dmesg`
`less /ver/log/syslog`
`less /ver/log/auth.log`

- Просмотр `auth.log`:
![Screenshot 49](part14-6.png)
Время последней успешной авторизации: 
Имя пользователя: obduliar
Метод входа в систему: pts/0 (ssh2), password

- Рестарт SSHd `sudo systemctl restart ssh`:
![Screenshot 50](part14-7.png)


# Part 15. Использование планировщика заданий CRON.

- Планирование запуска uptime каждые 2 минуты:
Открытие настроек: `crontab -e`
Добавление строчки: */2 * * * * uptime

![Screenshot 51](part15.png)
![Screenshot 52](part15-2.png)


- Записи о выполнении в системных журналах:
`sudo less /var/log/syslog | grep CRON`
![Screenshot 53](part15-3.png)


- Вывод на экран списка текущих задач для CRON:
![Screenshot 54](part15_2min.png)

- Удаление всех заданий из планироващика:
`crontab -r`
![Screenshot 55](part15-final.png)