Requirements:
python modules: boto (for AWS)
export AWS_ACCESS_KEY_ID='AK123'
export AWS_SECRET_ACCESS_KEY='abc123'
create AWS key pair
create AWS security group and grant ssh access (22 port)

region, key, group, AMI image id - all connected


TODO:
Добавить авторизацию и ограничения доступа в Mongo
Добавить создание и управление сетями AWS
Добавить переменные для настройки сетей, региона, образов EC2
Переработать получение хостов для EC2 (динамический инвентарь)
