# config-file-collector-utility

<h2>Описание:</h2>
Основной принцип работы подразумевает последовательное подключение к хостам по протоколу SSH-2 (usernameSSH, passwordSSH) затем из директории на удаленной машине производится выгрузка файлов конфигурации (fileNames). 
Директории указываются по абсолютному пути, есть возможность указать несколько директорий (remoteFolders) в случае если в первой по списку директории не окажутся нужные файлы поиск повторится для следующей директории в списке, 
так пока файлы не будут найдены или пока директории в списке не кончаться.

В системной директории (Temp) создается папка с названием совпадающим с наименованием сервиса (указывается в serviceName), внутри создаются папки с названиями соответствующими хостам которые в свою очередь содержат выгруженные файлы конфигураций. (Temp/название сервиса/название хоста/файлы конфигурации).
Пары состоящие из (Хостнейм : IP адрес) как и все вышеперечисленные параметры задаются в файле настроек.
(образец такого файла с настройками можно найти в проекте "src/main/resources/settings.json")
Утилита (JAR-файл) после запуска запрашивает путь к такому .json файлу с настройками, его (путь) потребуется ввести в консоль.

<h2>Протестированные сценарии:</h2>

<ul>
  <li>один из узлов недоступен - в консоль выведется сообщение об ошибке с "проблемным" IP, продолжится работа по списку узлов;</li>
  <li>логин пароль неверные - в консоль выведется сообщение об ошибке с "проблемным" IP, продолжится работа по списку узлов;</li>
  <li>в директории ожидаемых файлов нет - в консоль выведется сообщение об ошибке с названием директории, продолжится работа по списку директорий;</li>
  <li>нужного файла нет - в консоль выведется сообщение об ошибке с file name, продолжится работа по списку файлов.</li>
</ul>
