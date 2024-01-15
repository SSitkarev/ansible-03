# Домашнее задание к занятию 3 «Использование Ansible» - Сергей Ситкарёв

1. Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает LightHouse.

2. При создании tasks рекомендую использовать модули: get_url, template, yum, apt.

3. Tasks должны: скачать статику LightHouse, установить Nginx или любой другой веб-сервер, настроить его конфиг для открытия LightHouse, запустить веб-сервер.

4. Подготовьте свой inventory-файл prod.yml.

5. Запустите ansible-lint site.yml и исправьте ошибки, если они есть.

6. Попробуйте запустить playbook на этом окружении с флагом --check.

![Задание6](https://github.com/SSitkarev/ansible-03/blob/main/img/6.jpg)

7. Запустите playbook на prod.yml окружении с флагом --diff. Убедитесь, что изменения на системе произведены.

![Задание7](https://github.com/SSitkarev/ansible-03/blob/main/img/7.jpg)

8. Повторно запустите playbook с флагом --diff и убедитесь, что playbook идемпотентен.

![Задание8](https://github.com/SSitkarev/ansible-03/blob/main/img/8.jpg)

Изменения из-за перезапуска Vector-а и из-за повторного клонирования репозитория LightHouse (в плейбуке указан ключ ansible.builtin.git.force: true)

![Задание8](https://github.com/SSitkarev/ansible-03/blob/main/img/8-1.jpg)

9. Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги.

## Порядок выполнения данного ДЗ:

- Предварительно были созданы 3 виртуальные машины.

![Задание0](https://github.com/SSitkarev/ansible-03/blob/main/img/0.jpg)

- IP адреса машин были указаны в [inventory файле](https://github.com/SSitkarev/ansible-03/tree/main/inventory/prod.yml).

- Переменные указаны в соответствующих папках [group_vars](https://github.com/SSitkarev/ansible-03/tree/main/group_vars).

- Шаблоны для запуска сервисов находятся в директории [templates](https://github.com/SSitkarev/ansible-03/tree/main/templates).

- Исполняемый playbook [site.yml](https://github.com/SSitkarev/ansible-03/tree/main/site.yml).

Плейбук выполняет на хосте lighthouse установку Nginx, т.к. Lighthouse необходим веб-сервер, клонирует репозиторий Lighthouse с GitHub (plays помечены тегами Nginx и Lighthouse);

На хосте clickhouse выполняется установка clickhouse-common-static, clickhouse-client, clickhouse-server пакетов (тег Clickhouse)

На хосте Vector выполняется установка Vector (тег Vector)

10. Готовый playbook выложите в свой репозиторий, поставьте тег 08-ansible-03-yandex на фиксирующий коммит, в ответ предоставьте ссылку на него.