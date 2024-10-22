# Домашнее задание к занятию 3 «Резервное копирование» - `Пронин Дмитрий Андреевич`

---

### Задание 1

* Составьте команду rsync, которая позволяет создавать зеркальную копию домашней директории пользователя в директорию /tmp/backup
``` - команда  rsync -av --delete /home/developer/ /tmp/backup/ ```
![скрин](https://github.com/dmitriypronin48/fork-cicd/blob/main/img/z1-1.jpg)

* Необходимо исключить из синхронизации все директории, начинающиеся с точки (скрытые)
  ``` - команда rsync -av --delete --exclude '.*' /home/developer/ /tmp/backup/ ```
![скрин](https://github.com/dmitriypronin48/fork-cicd/blob/main/img/z1-2.jpg)

* Необходимо сделать так, чтобы rsync подсчитывал хэш-суммы для всех файлов, даже если их время модификации и размер идентичны в источнике и приемнике.
``` - команда rsync -av --delete --checksum --exclude '.*' /home/developer/ /tmp/backup/```
![скрин](https://github.com/dmitriypronin48/fork-cicd/blob/main/img/z1-3.jpg)

* На проверку направить скриншот с командой и результатом ее выполнения
``` направлено выше ```




---

### Задание 2



* Написать скрипт и настроить задачу на регулярное резервное копирование домашней директории пользователя с помощью rsync и cron.
* Резервная копия должна быть полностью зеркальной
* Резервная копия должна создаваться раз в день, в системном логе должна появляться запись об успешном или неуспешном выполнении операции
* Резервная копия размещается локально, в директории /tmp/backup
* На проверку направить файл crontab и скриншот с результатом работы утилиты.

![скрин](https://github.com/dmitriypronin48/fork-cicd/blob/main/img/z2-1.jpg)

```
#!/bin/bash

log_access="/opt/log_acces_backup" #успешно выполнился
log_error="/opt/log_error_backup"  #не успешно выполнился

# Создание бэкапа
rsync -av --delete --checksum /home/developer/ /tmp/backup/ 2>> "$log_error"
status_code=$?  # Сохраняем код выхода rsync
if [ $status_code -eq 0 ]; then
    echo "Бекап сделан от $(date)" >> "$log_access"
    exit 0
else
    echo "Что то не так, проблема от $(date) , ошибка $status_code " >> "$log_error"
    exit 1
fi
```
![скрин](https://github.com/dmitriypronin48/fork-cicd/blob/main/img/z2-2.jpg)
