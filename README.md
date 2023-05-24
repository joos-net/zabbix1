# Домашнее задание к занятию "`Система мониторинга Zabbix`"
# `Островский Евгений`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

Установите Zabbix Server с веб-интерфейсом.

### Требования к результаты

1. Прикрепите в файл README.md скриншот авторизации в админке
2. Приложите в файл README.md текст использованных команд в GitHub

```
apt install postgresql

wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
dpkg -i zabbix-release_6.0-4+debian11_all.deb
apt update

sudo apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts

sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix

zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

sudo nano /etc/zabbix/zabbix_server.conf

sudo systemctl restart zabbix-server apache2

sudo systemctl enable zabbix-server apache2
```


![Zabbix1](https://github.com/joos-net/zabbix1/blob/main/zab1.png)

![Zabbix2](https://github.com/joos-net/zabbix1/blob/main/zab2.png)

---

### Задание 2

Установите Zabbix Agent на два хоста.

### Требования к результатам

1. Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
2. Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
3. Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
4. Приложите в файл README.md текст использованных команд в GitHub


```
Linux
wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
dpkg -i zabbix-release_6.0-4+debian11_all.deb
apt update
 
sudo apt install zabbix-agent

sudo systemctl restart zabbix-agent
sudo systemctl enable zabbix-agent


MacOS
Download https://cdn.zabbix.com/zabbix/binaries/stable/6.0/6.0.17/zabbix_agent-6.0.17-macos-amd64-gnutls.pkg
sudo installer -pkg zabbix_agent-6.0.17-macos-amd64-gnutls.pkgg -target /
sudo launchctl start com.zabbix.zabbix_agentd

```

![Zabbix3](https://github.com/joos-net/zabbix1/blob/main/zab3.png)

![Zabbix4](https://github.com/joos-net/zabbix1/blob/main/zab4.png)

![Zabbix5](https://github.com/joos-net/zabbix1/blob/main/zab5.png)

---
## Дополнительные задания (со звездочкой*)

Эти задания дополнительные (не обязательные к выполнению) и никак не повлияют на получение вами зачета по этому домашнему заданию. Вы можете их выполнить, если хотите глубже и/или шире разобраться в материале.

### Задание 3

Установите Zabbix Agent на Windows (компьютер) и подключите его к серверу Zabbix.

### Требования к результаты

Приложите в файл README.md скриншот раздела Latest Data, где видно свободное место на диске C:

![Zabbix6](https://github.com/joos-net/zabbix1/blob/main/zab6.png)
