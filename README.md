# LAB_1
Начало работы

`pwd` - Проверка какая директория открыта сейчас

1.Скачиваем пакет wget, с помощью команды.Данная утилита wget в Linux предназначена для скачивания файлов из интернета. Она поддерживает протоколы HTTP, HTTPS и FTP, что позволяет загружать как отдельные файлы, так и целые веб-сайты.

    sudo yum install wget

![image](https://github.com/user-attachments/assets/ed09c4e6-8b2b-4d0c-834f-34a5c30d8f07)


2.Скачиваем пакет curl, с помощью команды.Данная утилита curl в Linux предназначена для передачи данных с помощью различных сетевых протоколов, таких как HTTP, HTTPS, FTP и других. Она позволяет отправлять запросы к серверам, загружать или отправлять файлы, а также получать информацию о загруженных ресурсах.

    sudo yum install curl

![image](https://github.com/user-attachments/assets/77af68cd-c923-4495-b539-98fde6e261eb)

3.На данном скрине мы загружаем <b>docker-ce.repo</b> и сохраняем его в указанный каталог на скрине.

    sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo

![image](https://github.com/user-attachments/assets/f7fe0392-8fb3-432f-b73f-9dd48d4d6a78)

4. С помощью команды будет установлено программное обеспечение Docker и все необходимые его компоненты.

        sudo yum install docker-ce docker-ce-cli containerd.io

![image](https://github.com/user-attachments/assets/95ef434d-3d17-4fcb-a79a-608234e27fa3)
![image](https://github.com/user-attachments/assets/f6b0b24c-e4ff-4b1f-9915-52ebca3aee30)

5.Команда включает автозапуск Docker и сразу же запускает его

    sudo systemctl enable docker --now

![image](https://github.com/user-attachments/assets/2c0f0d31-d47b-47a2-a5c7-2602d98b760e)

6.Эта команда использует утилиту `curl` для выполнения HTTP-запроса к API GitHub, чтобы получить информацию о последнем релизе репозитория Docker Compose, а затем извлекает номер версии этого релиза.

    COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)

![image](https://github.com/user-attachments/assets/4086e19c-fc3c-4658-8906-2d5677f322bb)

7.Эта команда использует утилиту `curl` для загрузки последней версии Docker Compose и сохраняет её в системную директорию `/usr/bin/`.

    sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose

![image](https://github.com/user-attachments/assets/15260c10-7b2a-4ae0-9612-b6240c9b4483)

8.Эта команда изменяет права доступа к файлу `docker-compose`, чтобы сделать его исполняемым.

    sudo chmod +x /usr/bin/docker-compose

![image](https://github.com/user-attachments/assets/19db8dab-837d-48c0-8c31-826d66cd45a1)

9.Команда позволяющая узнать версию docker-compose

    docker --version

![image](https://github.com/user-attachments/assets/d9c574f1-117d-4cca-a50d-ef206071425a)

10.Эта команда использует утилиту git для клонирования (копирования) удаленного репозитория на ваш локальный компьютер.

    git clone https://github.com/skl256/grafana_stack_for_docker.git

![image](https://github.com/user-attachments/assets/3765c2df-9c3e-4f31-aaa1-9926bc9a9756)

11.Эта команда изменяет текущую рабочую директорию в терминале на директорию grafana_stack_for_docker.

    cd grafana_stack_for_docker

![image](https://github.com/user-attachments/assets/51b88fe8-db5d-470d-a1db-59c1c658e891)

12.Эта команда создает директорию `/mnt/common_volume/swarm/grafana/config` с использованием прав суперпользователя <b>root</b>.

    sudo mkdir -p /mnt/common_volume/swarm/grafana/config

![image](https://github.com/user-attachments/assets/a2a41086-d0da-487f-9ef7-42b35d8f2bba)

13.Эта команда создает несколько вложенных директорий в указанном пути с использованием прав суперпользователя <b>root</b>.

    sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}
    
![image](https://github.com/user-attachments/assets/b5614536-4d78-4151-bdc4-359b5c74cbdb)

14.Эта команда рекурсивно изменяет владельца и группу для указанных директорий и всех их содержимых файлов и поддиректорий. Владельцем и группой становятся текущий пользователь и его основная группа.

    sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}

![image](https://github.com/user-attachments/assets/cadc9df7-1535-4693-a148-7489a4493652)

15.Эта команда создаёт пустой файл grafana.ini в указанной директории, если его там нет, или обновляет время последнего доступа и изменения, если файл уже существует.

    touch /mnt/common_volume/grafana/grafana-config/grafana.ini

![image](https://github.com/user-attachments/assets/10edca70-2c41-4bc5-9239-271e038d1235)

16.Эта команда копирует все файлы и директории из каталога `config/` в каталог `/mnt/common_volume/swarm/grafana/config/`. Если файлы с такими же именами уже существуют в целевом каталоге, они будут перезаписаны.

    cp config/* /mnt/common_volume/swarm/grafana/config/

![image](https://github.com/user-attachments/assets/9df2d390-b56f-464d-81b5-eb25920e85fc)

17.Эта команда переименовывает файл `grafana.yaml` в `docker-compose.yaml`, что бы не потерять этот файл проверяем с помощью команды <b>ls</b>

    mv grafana.yaml docker-compose.yaml

![image](https://github.com/user-attachments/assets/07351c31-464e-4da0-8d13-9eb7817fc36c)

18.Эта команда используется для запуска и управления контейнерами Docker с помощью Docker Compose

    sudo docker compose up -d

![image](https://github.com/user-attachments/assets/567e247e-760f-46de-8203-83de860deaa4)
![image](https://github.com/user-attachments/assets/9869ce1d-da35-49d5-9263-1f4097746796)

19.После того как мы после закрытия VM открываем его по новой что бы запустить <b>docker compose</b> нужно ввести эти команды `cd grafana_stack_for_docker` и `sudo docker compose up -d`

    cd grafana_stack_for_docker
    sudo docker compose up -d

![image](https://github.com/user-attachments/assets/6ffc2b65-4641-4084-a90f-4432d6db4afe)

20.Что бы зайти в конфигурацию <b>docker-compose.yaml</b> нам нужно ввести команду `vi docker-compose.yaml` и что бы от туда выйти нужно нажать кнопки `ESC`,`Правый shift+:` и ввести `wq`

    vi docker-compose.yaml

![image](https://github.com/user-attachments/assets/ee93eb33-e4bb-493c-8df6-04374d924caa)

21.Данной командой мы переносим `prometheus.yaml` в правильную папку конфига

        mv prometheus.yaml /mnt/common_volume/swarm/grafana/config

![image](https://github.com/user-attachments/assets/15ba16d0-5fe7-4878-b4a1-d2f842a6f417)

22.С помощью этих двух команд, первое что мы делаем это переходим в папку с конфигом, а второй проверяем смогли мы удачно перенсти этот файл

        cd /mnt/common_volume/swarm/grafana/config
        ls

![image](https://github.com/user-attachments/assets/266f6c2b-bd36-4f04-b1e5-f487450ad8eb)

# Grafana

* переходим на сайт `localhost:3000`

* User & Password GRAFANA: `admin`

* Код графаны: `3000`

* Код прометеуса: `http://prometheus:9090`

<ul>
в меню выбираем вкладку Dashboards и создаем Dashboard

ждем кнопку `+Add visualization`, а после "Configure a new data source"

выбираем `Prometheus`
</ul>

* Connection

<ul>
    
http://prometheus:9090

Authentication

Basic authentication

User: `admin`
Password: `admin`
</ul>

* Нажимаем на Save & test и должно показывать зелёную галочку

<ul>
    
в меню выбираем вкладку Dashboards и создаем Dashboard

ждем кнопку "Import dashboard"

Find and import dashboards for common applications at grafana.com/dashboards: 1860 //ждем кнопку Load

Select Prometheus ждем кнопку "Import"
</ul>

![image](https://github.com/user-attachments/assets/d309fe5c-1a98-4c1d-9869-2582773fd3b3)

# Victoria
Вводим команду `echo -e "# TYPE light_metric1 gauge\nlight_metric1 0" | curl --data-binary @- http://localhost:8428/api/v1/import/prometheus` которая, отправляет бинарные данные (например, метрики в формате Prometheus) на локальный сервер, который слушает на порту 8428.

![image](https://github.com/user-attachments/assets/b7162512-8965-4fc1-b6a4-a1ec3d1e8176)

Переходим в браузере по ссылке http://localhost:8428/, открывается такое меню в нём нужно выбрать vmui

![image](https://github.com/user-attachments/assets/c7cad968-09e9-4aaf-ac42-51c753c7b750)

Вписываем light_metric1 и нажимаем Execute Query

![image](https://github.com/user-attachments/assets/d2e0a94b-b4da-499d-a24e-3de6c6e0cc92)

Переходим на http://localhost:3000 выбираем Dashboard и нажимаем New Dashboard, далее Add Visualization

![image](https://github.com/user-attachments/assets/44b1b426-823e-4552-9ac4-ea050677110b)

Нажимаем Configure a new data source и выбираем Prometheus

![image](https://github.com/user-attachments/assets/08d5ef99-dbc9-488c-bdd1-85995f6388a2)

Вписываем:

Name: vik

Connection: http://victoriametrics:8428

Нажимаем Save & Test

![image](https://github.com/user-attachments/assets/45dd1191-2616-4935-87c2-b3a66700e1d6)

Вписываем light_metric1

![image](https://github.com/user-attachments/assets/7cb40d5c-4853-42f1-9efc-ff9aaaa88bbb)

Выходит панель с графиком, где есть активность light_metric1

![image](https://github.com/user-attachments/assets/bbb896db-430c-4ed9-9808-eeb7ca7dbe09)














