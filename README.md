# Домашнее задание к занятию «Система мониторинга Zabbix» - Егоров Дмитрий

В практике есть 2 основных и 1 дополнительное (со звездочкой) задания. Первые два нужно выполнять обязательно, третье - по желанию и его решение никак не повлияет на получение вами зачета по этому домашнему заданию, при этом вы сможете глубже и/или шире разобраться в материале. 

Пожалуйста, присылайте на проверку всю задачу сразу. Любые вопросы по решению задач задавайте в чате учебной группы.

### Цели задания
1. Научиться устанавливать Zabbix Server c веб-интерфейсом
2. Научиться устанавливать Zabbix Agent на хосты
3. Научиться устанавливать Zabbix Agent на компьютер и подключать его к серверу Zabbix 

### Чеклист готовности к домашнему заданию
- [ ] Просмотрите в личном кабинете занятие "Система мониторинга Zabbix" 

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и ваши фамилию и имя;
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   - для корректного добавления скриншотов воспользуйтесь инструкцией [«Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

---

### Задание 1 

Установите Zabbix Server с веб-интерфейсом.

#### Процесс выполнения
1. Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
2. Установите PostgreSQL. Для установки достаточна та версия, что есть в системном репозитороии Debian 11.
3. Пользуясь конфигуратором команд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache.
4. Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server.

#### Требования к результатам 
1. Прикрепите в файл README.md скриншот авторизации в админке.
<img width="1640" height="929" alt="image" src="https://github.com/user-attachments/assets/5835a024-ed0e-40a9-a8f4-fe400a9792f0" />

3. Приложите в файл README.md текст использованных команд в GitHub.
```
  222  sudo -s 
  223  sudo systemctl status postgresql
  224  sudo ept update
  225  sudo apt update
  226  sudo apt install postgresql
  227  sudo systemctl status postgresql
  228  wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_6.0+ubuntu24.04_all.deb
  229  dpkg -i zabbix-release_latest_6.0+ubuntu24.04_all.deb
  230  sudo dpkg -i zabbix-release_latest_6.0+ubuntu24.04_all.deb
  231  apt update 
  232  sudo apt update 
  233  sudo apt install zabbix-server-pgsql zabbix-frontend-php php8.3-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
  234  sudo -u postgres createuser --pwprompt zabbix
  235  sudo -u postgres createdb -O zabbix zabbix
  236  zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
  237  cd /etc/zabbix/zabbix_server.conf
  238  cd /etc/zabbix/
  239  ll
  240  nano zabbix_server.conf # поменял ip адрес сервера на адрес ВМ
  241  sudo nano zabbix_server.conf 
  242  systemctl restart zabbix-server zabbix-agent apache2
  243  systemctl enable zabbix-server zabbix-agent apache2
  244  systemctl status zabbix-server.service
  249  systemctl status zabbix-server.service


```
---

### Задание 2 

Установите Zabbix Agent на два хоста.

#### Процесс выполнения
1. Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
2. Установите Zabbix Agent на 2 вирт.машины, одной из них может быть ваш Zabbix Server.
3. Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов.
4. Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera.
5. Проверьте, что в разделе Latest Data начали появляться данные с добавленных агентов.

#### Требования к результатам
1. Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
2. Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
3. Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
4. Приложите в файл README.md текст использованных команд в GitHub

скриншот раздела Configuration > Hosts
<img width="1645" height="947" alt="image" src="https://github.com/user-attachments/assets/75223975-ca05-48db-b16a-2f5432bb8a18" />

скриншот лога zabbix agent
<img width="1547" height="923" alt="image" src="https://github.com/user-attachments/assets/7dc1777e-353f-4653-97e1-e5fd76a9ef95" />

скриншот раздела Monitoring > Latest data
<img width="1659" height="944" alt="image" src="https://github.com/user-attachments/assets/45bece29-8af2-48ee-a4bd-7b3ff8217c92" />

текст использованных команд в GitHub

```
447  wget https://repo.zabbix.com/zabbix/6.0/ubuntu-arm64/pool/main/z/zabbix-release/zabbix-release_latest_6.0+ubuntu24.04_all.deb
  448  dpkg -i zabbix-release_latest_6.0+ubuntu24.04_all.deb
  449  cd /etc/apt
  450  ll
  451  cat sources.list
  452  nano sources.list
  453  cat sources.list.d
  454  cd sources.list.d
  455  ll
  456  cd
  457  apt update
  458  apt install zabbix-server-pgsql zabbix-frontend-php php8.3-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
  459  dpkg -i zabbix-release_latest_6.0+ubuntu24.04_all.deb
  460  apt update
  461  apt install zabbix-server-pgsql zabbix-frontend-php php8.3-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
  462  sudo -u postgres createuser --pwprompt zabbix
  463  sudo -u postgres createdb -O zabbix zabbix
  464  zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
  465  nano /etc/zabbix/zabbix_server.conf
  466  systemctl restart zabbix-server zabbix-agent apache2
  467  systemctl enable zabbix-server zabbix-agent apache2
  468  exit
  469  wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_6.0+ubuntu24.04_all.deb
  470  dpkg -i zabbix-release_latest_6.0+ubuntu24.04_all.deb
  471  apt update
  472  apt install zabbix-server-pgsql zabbix-frontend-php php8.3-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
  473  sudo -u postgres createuser --pwprompt zabbix
  474  sudo -u postgres createdb -O zabbix zabbix
  475  cd /etc/zabbix/zabbix_server.conf
  476  cd /etc/zabbix/
  477  nano zabbix_server.conf
  478  systemctl restart zabbix-server zabbix-agent apache2
  479  systemctl enable zabbix-server zabbix-agent apache2
  480  ip a
  481  sudo ip link set enp0s3 down
  482  ip addr add 10.0.2.17/24 dev enp0s3
  483  sudo ip link set enp0s3 up
  484  ip a
  485  sudo ip link set enp0s3 down
  486  ip addr add 10.0.2.17/24 dev enp0s3
  487  sudo ip link set enp0s3 up
  488  ip addr show
  489  ping 10.0.2.15
  490  ip addr show
  491  cd /etc/network/interfaces
  492  cd /etc/network/

```
