# Инструмент для обнаружения инверсии приоритетов

Скрипт предназначен для обнаружения инверсии приоритетов в ОС на базе ядра Linux.
Приведены две версии скрипта.

## С ограниченным временем работы

PI_Detect_timed работает заданное время.
Задать время работы скрипта можно в строчке interval через двоеточие еденица измерения времени и временной промежуток.
Так, например, значение по умолчанию, interval:s:300 говорит о том, что программа будет работать на протяжении 300 секунд.

## С неограниченным временем работы

PI_Detect_endless завершит работу при команде от пользователя.

# Использование

Для работы скрипта необходимо установить трассировщик Bpftrace.


## Ubuntu

Для установки на Ubutu воспользуйтесь следующей командой.

    sudo apt-get install -y bpftrace

Как альтернативный вариант установки для версий 16.04 и позже можно воспользоваться следующими командами.
    
    sudo snap install
    sudo snap connect bpftrace:system-trace
    
Подробнее про установку можно найти по [этой](https://github.com/iovisor/bpftrace/blob/master/INSTALL.md) ссылке
  
## Android

### Требования

Одним из главных требований для запуска скрипта и для работы Bpftrace в целом в ОС Android является то, что устройство должно иметь доступ к файлам системы, иными словами иметь root-access.
К сожалению, получить root-access можно не во всех случаях. Для этого можно воспользоваться одним из готовых Android-приложений либо приложениями для ПК, способными предоставить root-доступ.


### Установка
Так как Bpftrace пока не поддерживается на Android, для работы на ОС Android необходимо воспользоваться утилитой [adeb](https://github.com/joelagnel/adeb). (Привычная утилита adb не может предоставить для этого достаточного функционала)

Необходимо скачать adeb, подключиться к реальному Android-устройству посредством usb либо к эмулятору Android-устройства, после чего выполнить следующие команды.

    cd adeb
    sudo ln -s $(pwd)/adeb /usr/bin/adeb
    adeb prepare --build --bcc
    
Эти команды помогут установить и настроить adeb.

Если в ходе установки возникнут ошибки, убедитесь, что устройство подключено и работает правильно при помощи следующей команды
    
    adb devices

После этого остаётся только запустить оболочку.

    adeb shell
    
Подробнее про установку посредством adeb можно узнать [здесь](https://github.com/joelagnel/adeb) и [здесь](https://github.com/joelagnel/adeb/blob/master/BCC.md).
Подробнее про использование Bpftrace в Android можно узнать по этой [ссылке](https://evilpan.com/2022/01/03/kernel-tracing/). (Возможно, придется воспользоваться переводом страницы)
