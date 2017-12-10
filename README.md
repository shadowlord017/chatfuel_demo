## Description:
- Ansible-playbook предназначен для создания кластера MongoDB в облаке AWS.
- 1. Создается replica_count * shard_count количество инстансов EC2 для MongoDB + 1 инстанс EC2 для MongoDB Config server и для MongoDB mongos (mongoc и mongos располагаются на одной машине)
- 2. На все машины устанавливаются необходимые пакеты из репозиторием MongoDB
- 3. Инициализируется replica set группами по replica_count машин (всего shard_count отдельных наборов)
- 4. Инициализируется Configuration server и mongos
- 5. К mongos добавляются шарды.

## Ограничения и недостатки:
- Нет защиты и авторизации, используются публичные адреса
- Mongos и mongoc запускаются только в 1 экземпляре

## Requirements:
- python modules: boto (for AWS)
- должны быть сгенерированы ключи доступа в AWS и установлены в ssh-agent на машине, где запускается ansible
- группа безопасности AWS должна разрешать внешние коннекты на 22, 27016, 27017 порты

## Usage:
- Прописать параметры в group_vars/all
- $ export AWS_ACCESS_KEY_ID='AK123'
- $ export AWS_SECRET_ACCESS_KEY='abc123'
- $ ansible-playbook aws.install.yml

## Как проверить:
- 1. Найти public ip EC2-машины с mongos (теги: name=mongo, group=mongos)
- 2. Подключиться: mongo <public ip>:27017
- 3. sh.status();
- 4. db.stats();

## TODO:
- Добавить авторизацию и ограничения доступа в Mongo
- Добавить создание и управление сетями AWS
- Добавить переменные для настройки сетей, региона, образов EC2
- Переработать получение хостов для EC2 (динамический инвентарь)
- Добавить поддержку реплик для config-сервера
- Добавить поддержку множественного mongos-сервера
- Использовать внутреннюю сеть для связи реплик и mongos вместо публичной
