# LAB_1
Начало работы 

1.Скачиваем пакет wget, с помощью команды(<b>sudo yum install wget</b>).Данная утилита wget в Linux предназначена для скачивания файлов из интернета. Она поддерживает протоколы HTTP, HTTPS и FTP, что позволяет загружать как отдельные файлы, так и целые веб-сайты.

![image](https://github.com/user-attachments/assets/ed09c4e6-8b2b-4d0c-834f-34a5c30d8f07)


2.Скачиваем пакет curl, с помощью команды(<b>sudo yum install curl</b>).Данная утилита curl в Linux предназначена для передачи данных с помощью различных сетевых протоколов, таких как HTTP, HTTPS, FTP и других. Она позволяет отправлять запросы к серверам, загружать или отправлять файлы, а также получать информацию о загруженных ресурсах.

![image](https://github.com/user-attachments/assets/77af68cd-c923-4495-b539-98fde6e261eb)

3.На данном скрине мы загружаем <b>docker-ce.repo</b> и сохраняем его в указанный каталог на скрине.

![image](https://github.com/user-attachments/assets/f7fe0392-8fb3-432f-b73f-9dd48d4d6a78)

4. С помощью команды(<b>sudo yum install docker-ce docker-ce-cli containerd.io</b>)будет установлено программное обеспечение Docker и все необходимые его компоненты.

![image](https://github.com/user-attachments/assets/95ef434d-3d17-4fcb-a79a-608234e27fa3)
![image](https://github.com/user-attachments/assets/f6b0b24c-e4ff-4b1f-9915-52ebca3aee30)

5.Команда (<b>sudo systemctl enable docker --now</b>включает автозапуск Docker и сразу же запускает его

![image](https://github.com/user-attachments/assets/2c0f0d31-d47b-47a2-a5c7-2602d98b760e)

6.Эта команда использует утилиту `curl` для выполнения HTTP-запроса к API GitHub, чтобы получить информацию о последнем релизе репозитория Docker Compose, а затем извлекает номер версии этого релиза.

![image](https://github.com/user-attachments/assets/4086e19c-fc3c-4658-8906-2d5677f322bb)

7.Эта команда использует утилиту `curl` для загрузки последней версии Docker Compose и сохраняет её в системную директорию `/usr/bin/`.

![image](https://github.com/user-attachments/assets/15260c10-7b2a-4ae0-9612-b6240c9b4483)

8.Эта команда изменяет права доступа к файлу `docker-compose`, чтобы сделать его исполняемым.

![image](https://github.com/user-attachments/assets/19db8dab-837d-48c0-8c31-826d66cd45a1)

9.`docker --version` команда позволяющая узнать версию docker-compose

![image](https://github.com/user-attachments/assets/d9c574f1-117d-4cca-a50d-ef206071425a)

10.Эта команда использует утилиту git для клонирования (копирования) удаленного репозитория на ваш локальный компьютер.

![image](https://github.com/user-attachments/assets/3765c2df-9c3e-4f31-aaa1-9926bc9a9756)

11.Эта команда изменяет текущую рабочую директорию в терминале на директорию grafana_stack_for_docker.

![image](https://github.com/user-attachments/assets/51b88fe8-db5d-470d-a1db-59c1c658e891)

12.Эта команда создает директорию `/mnt/common_volume/swarm/grafana/config` с использованием прав суперпользователя <b>root</b>.

![image](https://github.com/user-attachments/assets/a2a41086-d0da-487f-9ef7-42b35d8f2bba)

13.Эта команда создает несколько вложенных директорий в указанном пути с использованием прав суперпользователя <b>root</b>.

![image](https://github.com/user-attachments/assets/b5614536-4d78-4151-bdc4-359b5c74cbdb)

14.Эта команда рекурсивно изменяет владельца и группу для указанных директорий и всех их содержимых файлов и поддиректорий. Владельцем и группой становятся текущий пользователь и его основная группа.

![image](https://github.com/user-attachments/assets/cadc9df7-1535-4693-a148-7489a4493652)

15.Эта команда создаёт пустой файл grafana.ini в указанной директории, если его там нет, или обновляет время последнего доступа и изменения, если файл уже существует.

![image](https://github.com/user-attachments/assets/10edca70-2c41-4bc5-9239-271e038d1235)

16.Эта команда копирует все файлы и директории из каталога `config/` в каталог `/mnt/common_volume/swarm/grafana/config/`. Если файлы с такими же именами уже существуют в целевом каталоге, они будут перезаписаны.

![image](https://github.com/user-attachments/assets/9df2d390-b56f-464d-81b5-eb25920e85fc)

17.`mv grafana.yaml docker-compose.yaml` эта команда переименовывает файл `grafana.yaml` в `docker-compose.yaml`, что бы не потерять этот файл проверяем с помощью команды <b>ls</b>

![image](https://github.com/user-attachments/assets/07351c31-464e-4da0-8d13-9eb7817fc36c)

18.`sudo docker compose up -d` Эта команда используется для запуска и управления контейнерами Docker с помощью Docker Compose

![image](https://github.com/user-attachments/assets/567e247e-760f-46de-8203-83de860deaa4)
![image](https://github.com/user-attachments/assets/9869ce1d-da35-49d5-9263-1f4097746796)











