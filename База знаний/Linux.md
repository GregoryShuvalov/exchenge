## Каталоги

| /bin       | Для основных утилит                                                                                                                                                                              |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **/boot**  | Файлы, связанные с загрузкой                                                                                                                                                                     |
| **/dev**   | Файлы, связанные с устройствами                                                                                                                                                                  |
| **/lib**   | Библиотеки, необходимые для исполняемых файлов системы                                                                                                                                           |
| **/media** | Похожа на /mnt, но сюда подключаются сменные устройства, вроде usb или cdrom                                                                                                                     |
| **/proc**  | Здесь мы можем увидеть процессы, исполняемые в системе в виде файлов. О процессах мы также поговорим                                                                                             |
| /**root**  | Домашний каталог суперпользователя. Вынесен из папки /home для целей аварийного восстановления. Типы аккаунтов мы рассмотрим в отдельной теме /run - данные о том, что в данный момент запущено  |
| **/sbin**  | Похоже на bin. Здесь системные утилиты                                                                                                                                                           |
| **/srv**   | Здесь службы размещают свои данные. Например такие службы, как веб-серверы                                                                                                                       |
| **/sys**   | Информация об устройствах и их драйверах                                                                                                                                                         |
| **/usr**   | Вторичная иерархия для данных пользователя. Используется для утилит в многопользовательском режиме. Обычно здесь лежат такие вещи, как текстовый редактор vim, почтовые клиенты или веб-браузеры |
| **/tmp**   | Директория временных файлов                                                                                                                                                                      |
| **/mnt**   | Предназначена для подключения временных файловых систем                                                                                                                                          |
| **/etc**   | Используется для хранения большинства файлов конфигурации                                                                                                                                        |
| **/var**   | Хранятся изменяемые файлы, логи кеш .....                                                                                                                                                        |

## Пользователи

- **Id** – Подробная информация о пользователе (uid, gid и группа).
- **last** – Список информации о последних входах в систему, включая время, имя пользователя, ip-адрес и длительность сеанса.
- **who** – Просмотр авторизованных пользователей
- **groupadd “testgroup”** – Создает группу с именем “testgroup”.
- **adduser NewUser** – Добавляет пользователя с именем “NewUser”.
- **userdel NewUser** – Удаляет пользователя с именем “NewUser”.
- **usermod NewUser** – изменяет информацию о пользователе “NewUser”.

## Навигация по каталогам

- **cd /.** – Переход в основной каталог
- **cd –** Переход в домашний каталог (переменная $HOME)
- **cd /root** – Переход в каталог /root
- **cd ..** – Переход на один уровень ниже
- **cd /root/.ssh** – Переход в скрытую папку .ssh

## Работа с файлами

- **ls -al** – Показывает файлы и каталоги в текущей папке
- **pwd** – Отображает текущий рабочий каталог
- **mkdir NewFolder** – Создает новый каталог с именем “NewFolder”.
- **rm NewFile** – Удаляет файл с именем “NewFile”
- **rm -f NewFile** – Принудительное удаление файла с именем “NewFile”
- **rm -r NewFolder** – Рекурсивно удаляет каталог с именем “NewFolder”
- **rm -rf NewFolder** – Принудительное удаление каталога с именем “NewFolder” рекурсивно
- **cp oldfile1 newfile2** – Копирует содержимое oldfile1 в newfile2
- **cp -r olddir1 newdir2** – Рекурсивно копирует каталог “olddir1” в “newdir2”. Dir2 будет создан, если он не существует.
- **mv oldfile1 newfile2** – Переименовывает “oldfile1” в “newfile2”.
- **ln -s /etc/log/file logfile** – Создает ярлык на файл 
- **ln file /path/file** - создание жесткой ссылки
- **touch newfile** – Создает пустой файл с именем newfile
- **cat > newfile** – Помещает STDIN в newfile
- **more newfile** – Выводит содержимое newfile по частям
- **head newfile** – Выводит первые 10 строк файла newfile
- **tail newfile** – Вывод последних 10 строк newfile
- **gpg -c newfile** – Шифрует newfile в формат gpg с помощью пароля и сохраняет его в том же каталоге.
- **gpg newfile.gpg** – Расшифровывает gpg файл
- **wc newfile** – Выводит количество байт, слов и строк нового файла.

## Права доступа к файлам/каталогам

- **chmod 777 /root/ssh** – устанавливает права rwx(чтение, запись, выполнение) на файл ssh для всех, кто имеет доступ к серверу (владелец, группа, другие)
- **chmod 755 /root/ssh** – Настраивает разрешения rwx для владельца и r_x для группы и других.
- **chmod 766 /root/ssh** – Устанавливает права rwx для владельца и rw для группы и других.
- **chown newuser newfile** – Меняет владельца newfile на newuser
- **chown newuser:newgroup newfile** – Изменяет владельца и группу-владельца для newfile на newuser и newgroup
- **chown newuser:newgroup newfolder** – Меняет владельца и группу-владельца каталога newfolder на newuser и newgroup
- **stat -c “%U %G” newfile** – отображает владельцев пользователей и групп newfile
- **sudo chown -R pollme /opt/pollme-code/**    - измени владельца ВСЕХ файлов и каталогов в /opt/pollme-code/ на пользователя pollme
- **chmod** : u - владелец           + разрешить         r - чтение
         g - группа                - запретить          w - запись
		 o - остальные         = назначить          x - выполнение
		 a - все
	пример : chmod ug+x file.py                  - добавить владельцу и группе право на выполнение
			chmod  o-r file.py                     - убрали остальным право на чтение
			chmod o=x file.py                     - назначили право на выполнение
			chmod o-r,o=x file/py file.py	   - в одну строку        
## Поиск

- **grep searchargument newfile** – Поиск аргумента searchargument в newfile
- **grep -r searchargument newfolder** – рекурсивно просматривает все файлы в папке newfolder на наличие поискового аргумента
- **locate newfile** – Показывает все местоположения нового файла
- **find /etc/ -name “searchargument”** – Находит файлы с именем, начинающимся с searchargument, в каталоге /etc
- **find /etc/ -size +50000k** – Найти файлы размером более 50000k в каталоге /etc.
- grep -ir "DATABASES = {" /opt/pollme-code
## Архивирование

- **tar -cf archive.tar newfile** – Создать архив ‘archive.tar’ из файла ‘newfile’
- **tar -xf archive.tar** – Распаковать файл ‘archive.tar’
- **tar -zcvf archive.tar.gz /var/log/** – Создать архив из каталога /var/log
- **gzip newfile** – Сжать новый файл (он будет иметь расширение .gz).

## Установка программ из пакетов

- **rpm -i pkg_program.rpm** – Устанавливает пакет rpm (CentOS, RHEL…)
- **rpm -e pkg_name** – Удаляет пакет rpm (CentOS, RHEL…)
- **dnf install pkg_name** – Устанавливает пакет с помощью dnf из репозитория. Ранее использовался YUM, но недавно YUM был заменен на DNF. (CentOS, RHEL…)
- **dpkg -i pkg_name** – Установка из deb-пакета (Debian, Ubuntu, Mint…)
- **dpkg -r pkg_name** – Удаляет deb-пакет (Debian, Ubuntu, Mint…)
- **apt install pkg_name** – Устанавливает пакет из репозитория (Debian, Ubuntu, Mint…)
- **apt remove pkg_name** – Удаляет пакет (Debian, Ubuntu, Mint…)
- **apt upgrade && apt update** – Обновление пакетов в системе (Debian, Ubuntu, Mint…) и последующее обновление репозиториев.

## Процессы

- **ps** – Выводит текущие запущенные процессы
- **ps -elf** - Таблица работающих процессов
- **pstree** - ---//--- древовидный формат
- **ps aux | grep ‘bash’** – Найти идентификатор процесса ‘bash’
- **pmap -x 11** – Сопоставить процесс с PID = 11 в памяти процесса
- **top** – Показывает все запущенные процессы
- **kill pid** – Завершить процесс по pid
- **killall process** – Завершить все процессы с именем “process”
- **pkill process-name** – Послать сигнал процессу
- **bg** – Отправить приостановленный процесс на фоновое выполнение
- **fg** – Вывести запущенный процесс из фона
- **fg process** – Вывести процесс с именем “process” из фонового режима
- **lsof** – Показать списки файлов, которые используют процессы
- **renice 19 PID** – Устанавливает самый низкий приоритет процесса
- **pgrep bash** – найти идентификатор процесса bash
- **pstree** – Показывает древовидное представление процессов
- **ls -l /proc/ | wc -l**   - Подсчет количества строк 
## Службы
Принцип 
1. **install** --- должна подниматься после загрузки.
2. **graphical.target** --- GUI и его зависимости должны работать
3. **agentx** --- Программа запускается от определенного пользователя
4. **mysql.service** --- База должна быть запущена до запуска
5. **on-failure-restart** --- Если приложение выходит с ошибкой, нужно подождать и попробовать запустить его снова. Не запускать, если мы сами его остановили
6. **env** --- Приложению надо предоставить порт и адрес хоста базы данных
7. l**ogs** --- События приложения фиксируются в единой системе логирования
пример службы:
[Unit]
Dscription=Simple Flask App
Documentation=https://rotoro.corp/man/agentx
After=mysql.service                                                 4
[Servise]
ExecStart=/opt/agentx/app.sh-address"8080"     1
Environment=/MYSQL_HOST=db01                        6
User=agent                                                               3
Restart=on-failure                                                    5
RestartSec=15                                                          5
[Install]
WantedBy=graphical.target                                     2
###SYESTEMD
	SYSTEMCTL --- Утилита для анализа и контроля состояния системы sistemd и диспетчера служб   !НЕ ПУТАТЬ С SYSCTL --- Управление параметрами ядра
 systemtctl-service
	 команды:
	 start, stop, restart, reload, enable, disable, status, deamond-reload, edit name --full
	 list-units --type=servisce
	  list-units --all
	 --type=servisce --state=active
	 jornalctl --- Просмотр событий из системы ведения логов systemd
	  jornalctl -b ---текущие
	.target --- группировка units по runlevels
			 Просмотр текущей system.target
			 Установка текущей system.target
			 Просмотр зависимостей
			 Просмотр списка units
	.servise --- отвечает за запуск служб
			 Запуск, перезапуск, остановка, перезагрузка service
			 Просмотр статуса и списка services
			 Добавление, изъятие services из автозагрузки
			 Перезагрузка конфигурации менеджера служб
			 Редактирование service
	.path --- управление иерархией файлов системы
	.mount --- точки монтирования файлов систем
	.automount --- авто монтирование 'на лету'
	.snapshot --- управление состоянием менеджера systemd
	.swap --- определение файлов подкачки
	.timer --- запуск units по расписанию
	.slice --- создание контейнера cgroups для служб
	.socket --- идентификация файлов сокетов
	.dedice --- реакция на подключение устройств
	.scope --- контрольные группы чужого дерева процессов 

**sudo systemctl enable pollme.service** - авто запуск службы

## Система

- **uname** – Показать информацию о системе
- **uname -r** – Показывает информацию о ядре Linux
- **uptime** – Продолжительность работы системы и средняя загрузка
- **hostname** – Показывает имя хоста
- **hostname -i** – Показывает IP-адрес хоста
- **last reboot** – Показывает историю перезагрузок
- **date** – Показывает дату и время
- **timedatectl** – Выводит и изменяет дату и время
- **cal** – Выводит календарь
- **w** – Отображает пользователей, работающих в системе
- **whoami** – Отображает ваше имя пользователя
- **finger root** – Показывает информацию о пользователе root (требуется установка с помощью “apt-get install finger”).
## Аппаратное обеспечение

- **dmesg** – Отображает системные сообщения при загрузке системы
- **cat /proc/cpuinfo** – Показывает информацию о процессоре
- **cat /proc/meminfo** – Показывает информацию об оперативной памяти
- **lshw** – Показывает информацию об устройствах
- **lsblk** – Показать информацию о жестком диске
-           или ls -l /dev/ | grep "^b"
- **free -m** – Освобождает память: RAM и swap (переключатель -m в MB)
- **lspci -tv** – Показывает информацию об устройствах PCI в виде дерева
- **lsusb -tv** – Отображает USB-устройства в древовидном виде.
- **dmidecode** – Показывает информацию об устройствах BIOS
- **hdparm -i /dev/xda** – Показывает информацию о диске
- **hdparm -tT /dev/xda** – Показывает скорость чтения и записи xda
- **badblocks -s /dev/xda** – Показывает тест на наличие битых секторов.

## Использование диска

- **df -h** – Показывает свободное пространство на смонтированных разделах (в байтах)
- **df -i** – Показывает свободные inodes в файловой системе
- **df -hP /tmp** -Показывает размер тома
- **fdisk -l** – Показывает информацию о диске, разделах и файловой системе
- **du -sh** – Отображает не распределенное пространство на смонтированных разделах в MB, GB, TB
- **findmnt** – Отображает все точки монтирования
- **mount /dev/sdb1 /mnt** – Монтирует раздел 1 диска sdb в /mnt
- **umount**  /dev/sdb1 - отключение тома  
 mkfc
 Пример gdisk - Создай раздел `GPT` с названием `vdb1` и размером `500M` на диске `/dev/vdb`

	  Запусти: `sudo gdisk /dev/vdb`  
	В интерактивном запросе введи `n`  
	Там выбери parition number = `1` (для vdb`1`)  
	Оставь по умолчанию first sector = `2048`  
	Выбери `+500M`, когда спросит про last sector  
	Используй дефолтный hex code = `8300`  
	В конце запиши все в таблице разделов с помощью `w`
		
 - **pvcreate** /dev/sdb1 /dev/sdc - создание physical volume
 - **vgcreate** "name" /dev/sdb1 /dev/sdc - создание volume group
 - **pvdisplay** - просмотр томов в VG
 - **lvcreate** -L 1G -n name VGname - создать логический том 
 - **mkfs.ext4 /dev/VGname/name** - cоздание файловой системы
 - **mount -t ext4 /dev/VGname/name** - смонтировать файловую систему 
 - **lgs** -просмотр VG
 - **lvresize -L +1G -n /dev/VGname/name** - добавить места VG
 - **resize2fs /dev/VGname/name** - изменение размера файловой системы(заполняет свободное пространство ранее добавленное)
 **/dev/name and /dev/mapper/name одинаковые ссылки на LV
 Пример  монтирования файловой системы и тома
	 sudo mkdir /mnt/media
	sudo mkfs.ext4 /dev/mapper/rotoro--vg-data
	sudo mount /dev/mapper/rotoro--vg-data /mnt/media/
mount | grep -w nfs** - посмотреть скока NFS

## Сеть

- **ip addr show** – Показывает IP-адреса всех доступных сетевых интерфейсов
- **ip address add 192.168.0.1/24 dev eth0** – Присваивает адрес 192.168.0.1 интерфейсу eth0
- **ifconfig** – Показывает IP-адреса всех доступных сетевых интерфейсов
- **ping 192.168.0.1** – Отправляет запрос по протоколу ICMP для подключения к узлу 192.168.0.1.
- **whois domain** – Показывает информацию о доменном имени
- **dig domain** – Получает информацию DNS о домене
- **dig -x 192.168.0.1** – Инвертирует разрешение имен
- **hostname -I** – Показывает локальные адреса
- **wget имя_файла(ссылка на файл)** – Загружает файл
- **netstat -pnltu** – Показывает все порты, прослушиваемые на хосте (требуется “apt-get install net-tools”)
- sudo netstat -tulpn | grep mysql | grep LISTEN   - проверить порт приложения
-----------------------------------------------
- **ip link** - физическое состояние 
- **ip addr - ip , mask** 
- **ip route** - маршруты и адрес шлюза по умолчанию
- **arp -vn -mac** адреса изернет
- **traceroute -l -n ya.ru** - трасировка 
- **tracerath -n ya.ru**  -----//------   (работает не из под рута)
- **mtr ya.ru** - при потере пакетов (сбор данных)
- ----------------------инструменты диагностики------------------------
- **host -v ya.ru**       info NDS
- **nslookup ya.ru**   info NDS
- **dig ya.ru**            info NDS
- or
- **cat /ect/resolv.conf**
- **nmcli connection show eth0 | grep dns**           (redhut)
- **systemd-resolve --status**                                  (deb)
- **ss -tulpn** - прослушка портов           / lsof -i -P -n 
- i**ptables -L** - правила допуска
- **firewall-cmd --list-all** 
- **curl app01:22** - curl для остованых на http приложениях
- -**-------------методы устранения проблем----------------**
- **ip link set dev name up** - поднять сетевой адаптер
- **netstart -tlpn | grep 80 | grep -i LIST** - какие порты прослушиваются
- s**udo systemctl nginx status**
## Удаленное подключение

- **ssh root@host** – Подключение к удаленному хосту по ssh от имени root
- **ssh -p port_number user@host** – Подключается к удаленному хосту, если используется порт ssh, отличный от 22.
- **ssh host** – Использует соединение по умолчанию в качестве текущего пользователя
- **telnet host** – Использует соединение telnet (порт 23).
## Примеры работы команд iptables
**sudo iptables -A INPUT -j DROP**
**sudo iptables -A OUTPUT -p TCP -d 172.20.235.10 --dport 3306 -j ACCEPT**
**sudo iptables -A OUTPUT -p TCP -d 172.20.236.10 --dport 80 -j ACCEPT**
**sudo iptables -A OUTPUT -p tcp --dport 80 -j DROP**
**sudo iptables -A OUTPUT -p tcp --dport 443 -j DROP**
**sudo iptables -i -A OUTPUT -p tcp -d google.com --dport -j ACCEPT** 
**sudo iptables -I OUTPUT -p tcp -d google.com --dport 443 -j ACCEPT** 
**sudo iptables -I OUTPUT -p tcp -d archive.ubuntu.com --dport 80 -j ACCEPT -m comment --comment "archive.ubuntu.com"**
**sudo iptables -I OUTPUT -p tcp -d archive.canonical.com --dport 80 -j ACCEPT -m comment --comment "archive.canonical.com"**
**sudo iptables -I OUTPUT -p tcp -d security.ubuntu.com --dport 80 -j ACCEPT -m comment --comment "security.ubuntu.com"**
**max@app01 ~$ sudo iptables -D INPUT 3**
