![j2](./logos/pocoo_jinja-icon.svg) ![apache](./logos/apache-svgrepo-com.svg) ![ansible](./logos/ansible-svgrepo-com(1).png)
# Деплой файла index.j2 на веб-сервер
Данный проект представляет собой автоматизированный процесс развертывания файла index.j2 на веб-сервере. 
index.j2 является шаблоном веб-страницы, который содержит динамические данные, подставляемые в соответствующие места при генерации конечного файла index.html.

## Описание
Основная цель проекта заключается в демонстрации простого автоматического развертывания файла index.j2 на веб-сервере. В процессе вылолнения проекта были выполнены следующие шаги:

1. Подготовка окружения: установка необходимых зависимостей и конфигурация системы.
Для рассматриваемого примера была поднята Виртуальная машина в [Yandex Compute Cloud](https://cloud.yandex.ru/docs/compute/) на базе Ubuntu версии 20.04.

![pic](screen.png)

2. Сформированы конфигурационные файлы: в ansible.cfg содержится путь к hosts.ini, который включает в себя публичный адрес удаленной машины и имя хоста, принадлежащие определенной группе. Директория ./group_vars содержит переменные группы из файла hosts.ini.

3. Компиляция шаблона и написание сценария Ansible: с использованием движка шаблонов [Jinja2](https://jinja.palletsprojects.com/en/3.1.x/) заполнен index.j2,
сценарий [Ansible](https://docs.ansible.com/) написан в формате YAML.

3. Перенос на веб-сервер осуществляется запуском плейбука


## Использование
Управляющий узел Ansible может быть установлен только на ОС Linux
Для использования данного проекта необходимо выполнить следующие действия:
- установить Ansible
```bash
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install ansible -y
```
- клонировать репозиторий с проектом на локальную машину: 
```bash
git clone https://github.com/nakhush/ansible-deploy.git
```

- настроить конфигурацию проекта в соответствии с требованиями вашего веб-сервера.
- запустить сценарий деплоя, который автоматически выполнит все необходимые шаги для развертывания файла index.j2 на веб-сервере.
```bash
ansible-playbook playbook.yml
```