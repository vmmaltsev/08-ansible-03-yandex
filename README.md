# Домашнее задание к занятию 3 «Использование Ansible» - `Мальцев Виктор`

---

Подготовка к выполнению
1. Подготовьте в Yandex Cloud три хоста: для clickhouse, для vector и для lighthouse.
2. Репозиторий LightHouse находится по ссылке.

---

Основная часть

1. Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает LightHouse.
2. При создании tasks рекомендую использовать модули: get_url, template, yum, apt.
3. Tasks должны: скачать статику LightHouse, установить Nginx или любой другой веб-сервер, настроить его конфиг для открытия LightHouse, запустить веб-сервер.
4. Подготовьте свой inventory-файл prod.yml.
5. Запустите ansible-lint site.yml и исправьте ошибки, если они есть.

![alt text](https://github.com/vmmaltsev/screenshot/blob/main/Screenshot_23.png)

6. Попробуйте запустить playbook на этом окружении с флагом --check.
7. Запустите playbook на prod.yml окружении с флагом --diff. Убедитесь, что изменения на системе произведены.
8. Повторно запустите playbook с флагом --diff и убедитесь, что playbook идемпотентен.

![alt text](https://github.com/vmmaltsev/screenshot/blob/main/Screenshot_24.png)

9. Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги.

Описание Playbook

Этот playbook предназначен для установки и настройки следующих компонентов:

    Clickhouse: ClickHouse - это быстрая open-source OLAP-система управления базами данных.
    Vector: Vector - это высокопроизводительный наблюдатель для сбора, преобразования и отправки логов и метрик.
    LightHouse: LightHouse - это инструмент командной строки для автоматизации проверки качества веб-страниц.

Параметры Playbook
Общие Параметры

    web_root: Корневой каталог для файлов веб-сайта. По умолчанию /var/www/html.

Параметры ClickHouse

    clickhouse_version: Версия ClickHouse для установки. Например, 21.3.9.56.
    clickhouse_packages: Список пакетов ClickHouse для скачивания и установки.

Параметры Vector

    vector_version: Версия Vector для установки. Например, 0.15.0.
    vector_rpm_url: URL-адрес RPM-пакета Vector.
    vector_config_template: Путь к файлу шаблона конфигурации Vector.
    vector_config_destination: Путь назначения для файла конфигурации Vector.

Параметры LightHouse

    web_root: Корневой каталог для файлов веб-сайта. По умолчанию /var/www/html.

Теги Playbook

    clickhouse: Только для задач, связанных с ClickHouse.
    vector: Только для задач, связанных с Vector.
    lighthouse: Только для задач, связанных с LightHouse.
    nginx: Только для задач, связанных с Nginx.

Как использовать

    Убедитесь, что у вас установлен Ansible.
    Отредактируйте файл inventory.ini, чтобы он содержал правильные хосты и параметры подключения.
    При необходимости отредактируйте переменные в файле site.yml или создайте файл vars.yml.
    Запустите playbook, используя команду ansible-playbook -i inventory.ini site.yml.

Примечание

    Playbook тестировался на CentOS 7.
    Для установки и настройки Nginx и LightHouse требуются права администратора. Убедитесь, что у вас есть необходимые права.

10. Готовый playbook выложите в свой репозиторий, поставьте тег 08-ansible-03-yandex на фиксирующий коммит, в ответ предоставьте ссылку на него.
