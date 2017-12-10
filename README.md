## Requirements:
- python modules: boto (for AWS)

## Usage:
- $ export AWS_ACCESS_KEY_ID='AK123'
- $ export AWS_SECRET_ACCESS_KEY='abc123'
- $ ansible-playbook aws.install.yml

create AWS key pair
create AWS security group and grant ssh access (22 port)

region, key, group, AMI image id - all connected

# Description:
Данный плейбук создает набор реплик и включает шардирование
Не включает в себя создание и шардирование конкретных баз.

## TODO:
- Добавить авторизацию и ограничения доступа в Mongo
- Добавить создание и управление сетями AWS
- Добавить переменные для настройки сетей, региона, образов EC2
- Переработать получение хостов для EC2 (динамический инвентарь)
- Добавить поддержку реплик для config-сервера
- Добавить поддержку множественного mongos-сервера
