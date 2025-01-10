**Данная инструкция применима только к Ubuntu 24.04.01.** 

**Для других ОС и других версий Ubuntu инструкция не применима!**

1. Обновить список пакетов: 

sudo apt update

1. Обновить пакеты:

sudo apt upgrade -y

1. Добавить репозиторий Debian contrib и non-free в /etc/apt/sources.list командой:

sudo nano /etc/apt/sources.list

Добавить или изменить существующий репозиторий на:    

deb http://deb.debian.org/debian/ buster main contrib non-free

Сохраните файл и выйдите из редактора 

(в nano нажмите Ctrl + X, затем Y, и Enter).

1. Обновить список пакетов: 

sudo apt update

1. Если возникает ошибка следующего вида:

Ошибка GPG: http://deb.debian.org/debian buster InRelease: Следующие подписи не могут быть проверены, так как недоступен открытый ключ: NO\_PUBKEY 648ACFD622F3D138 NO\_PUBKEY 0E98404D386FA1D9 NO\_PUBKEY DCC9EFBF77E11517

- Ключи могут быть другие, необходимо читать сообщение об ошибке.

В таком случае сделать следующие шаги:

1. Скачайте недостающие ключи:

<a name="ole_link1"></a><a name="ole_link2"></a>sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 648ACFD622F3D138

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0E98404D386FA1D9

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DCC9EFBF77E11517

Если сервер не отвечает, можно попробовать использовать другой протокол:

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 648ACFD622F3D138

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 0E98404D386FA1D9

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys DCC9EFBF77E11517

1. Обновить список пакетов:

sudo apt update

1. Установить Qt6: 

sudo apt install qt6-base-dev qt6-tools-dev qt6-tools-dev-tools qtcreator cmake -y

1. Проверить запуск из терминала: 

   qtcreator

1. Если запуск успешный, проверить, создался ли ярлык запуска, если ярлык для запуска не был создан в меню, его можно создать вручную:
   1. ` `Создайте файл с расширением .desktop в каталоге ~/.local/share/applications: 

nano ~/.local/share/applications/qtcreator.desktop

1. ` `Вставьте в файл следующий текст:

`   `[Desktop Entry]

`   `Name=Qt Creator

`   `Exec=/usr/bin/qtcreator

`   `Icon=qtcreator

`   `Type=Application

`   `Categories=Development;IDE;

1. ` `Сохраните файл и выйдите из редактора (в nano нажмите Ctrl + X, затем Y, и Enter).
1. ` `Если ярлык не появился, обновите кэш меню: 

update-desktop-database ~/.local/share/applications

1. ` `Запустить Qt через ярлык для проверки работоспособности.
