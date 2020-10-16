# Как начать работать с {{ mms-short-name }}

Чтобы начать работу с сервисом:

1. [Создайте кластер](#cluster-create).
1. [Подключитесь к БД](#connect).

## Перед началом работы {#before-you-begin}

1. Перейдите в [консоль управления]({{ link-console-main }}), затем войдите в {{ yandex-cloud }} или зарегистрируйтесь, если вы еще не зарегистрированы.
1. Если у вас еще нет каталога, создайте его:

    {% include [create-folder](../_includes/create-folder.md) %}

Подключаться к кластерам БД можно как изнутри, так и извне {{ yandex-cloud }}:

1. Чтобы подключаться изнутри {{ yandex-cloud }}, создайте виртуальную машину в той же сети, что и кластер БД (на основе [Linux](../compute/quickstart/quick-create-linux.md) или [Windows](../compute/quickstart/quick-create-windows.md)).
1. Чтобы подключаться к кластеру из интернета, запросите публичный доступ к хостам при создании кластера.

## Создайте кластер {#cluster-create}

1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором нужно создать кластер БД.
1. Выберите сервис **{{ mms-name }}**.
1. Нажмите кнопку **Создать кластер**.
1. Задайте параметры кластера и нажмите кнопку **Создать кластер**. Процесс подробно рассмотрен в разделе [{#T}](operations/cluster-create.md).
1. Когда кластер будет готов к работе, его статус сменится на **Running**, а состояние — на **Alive**. Это может занять некоторое время.

## Подключитесь к БД {#connect}

1. [Создайте виртуальную машину Linux](../compute/quickstart/quick-create-linux.md) в той же [виртуальной сети](../vpc/concepts/network.md), что и кластер.
1. [Подключитесь](../compute/operations/vm-connect/ssh.md) к виртуальной машине по SSH.
1. Установите зависимости и клиентское приложение `mssql-cli`:

   ```bash
   $ sudo apt update
   $ sudo apt install python3-pip python-is-python3
   $ pip3 install mssql-cli
   $ source ~/.profile
   ```

1. Подключитесь к базе данных:

   ```bash
   $ mssql-cli -U <имя пользователя> \
             -d <имя базы данных> \
             -S <FQDN хоста>,1433
   ```
   После выполнения команды введите пароль пользователя для завершения процедуры подключения.

## Что дальше

- Изучите [концепции сервиса](concepts/index.md).
- Узнайте подробнее о [создании кластера](operations/cluster-create.md) и [подключении к БД](operations/connect.md).
- Ознакомьтесь с [вопросами и ответами](qa/general.md).