[[junior linux]]

1. /etc:
   - Содержит конфигурационные файлы системы и приложений.
   - Примеры файлов: `passwd` (информация о пользователях), `hosts` (соответствия IP-адресов и имен хостов), `fstab` (информация о файловых системах).

2. /dev:
   - Содержит файлы устройств (device files), которые представляют собой интерфейсы к аппаратным устройствам.
   - Например: `/dev/sda` (жесткий диск), `/dev/tty` (терминальные устройства).

3. /proc:
   - Виртуальная файловая система, предоставляющая информацию о работающей системе, включая процессы и параметры ядра.
   - Примеры: `/proc/cpuinfo` (информация о процессоре), `/proc/meminfo` (информация о памяти).

4. /sys:
   - Представляет собой интерфейс к ядру, позволяя взаимодействовать с устройствами и настройками системы.
   - Содержит информацию о текущем состоянии устройств и драйверов.

5. /lib:
   - Содержит библиотеки, необходимые для работы системных и пользовательских программ.
   - Примеры: динамические библиотеки, такие как `libc.so`, которые необходимы для выполнения программ.

6. /var:
   - Хранит данные, которые могут меняться во время работы системы, такие как журналы, временные файлы и базы данных.
   - Примеры: `/var/log` (журналы системы), `/var/tmp` (временные файлы, которые могут храниться длительное время).

Эта структура помогает организовать файлы и облегчает управление системой.
