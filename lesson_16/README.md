# Настраиваем центральный сервер для сбора логов

## Домашнее задание

```txt
Настраиваем центральный сервер для сбора логов
в вагранте поднимаем 2 машины web и log
на web поднимаем nginx
на log настраиваем центральный лог сервер на любой системе на выбор
- journald
- rsyslog
- elk
настраиваем аудит следящий за изменением конфигов нжинкса

все критичные логи с web должны собираться и локально и удаленно
все логи с nginx должны уходить на удаленный сервер (локально только критичные)
логи аудита должны также уходить на удаленную систему


* развернуть еще машину elk
и таким образом настроить 2 центральных лог системы elk И какую либо еще
в elk должны уходить только логи нжинкса
во вторую систему все остальное
Критерии оценки: 4 - если присылают только логи скриншоты без вагранта
5 - за полную настройку
6 - если выполнено задание со звездочкой
```

## Описание

### Запуск Стенда

```bash
cd lesson_16
python3.8 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt

vagrant up
ansible -i inventory/vagrant.yml -m ping all
ansible-playbook -i inventory/vagrant.yml playbooks/install_logging.yml
```