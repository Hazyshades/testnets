# Официальные ссылки
### [Сайт](https://exorde.network/)
### [Документация](https://docs.exorde.network/)
### [Дискорд](https://discord.gg/exordelabs)
### [Еxplorer](https://explorer.exorde.network/)
### [Таблиця лидеров](https://explorer.exorde.network/leaderboard)

## Минимальные системные требования
- Минимум 2 CPU
- Минимум 1GB SSD
- Минимум 4GB RAM
- Минимум 100mbps 

# Установка ноды 

### Задаем переменную с адресом кошелька
```
WALLET_ADDRESS=<METAMASK WALLET ADDRESS>
```

Заменить `<METAMASK WALLET ADDRESS>` на ваш Metamask адресс

```
echo export WALLET_ADDRESS=${WALLET_ADDRESS} >> $HOME/.bash_profile
source ~/.bash_profile
```

### Обновление пакетов/зависимостей
```
cd $HOME
sudo apt update && sudo apt upgrade -y
sudo apt install curl build-essential git wget npm jq make gcc tmux -y && apt purge docker docker-engine docker.io containerd docker-compose -y
```

### Установка Docker
```
rm /usr/bin/docker-compose /usr/local/bin/docker-compose
curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh
systemctl restart docker
curl -SL https://github.com/docker/compose/releases/download/v2.5.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
docker --version
```

### Запуск Exorder CLI через  Docker
```
docker run \
-d \
--restart unless-stopped \
--pull always \
--name <CONTAINER_NAME> \
exordelabs/exorde-cli \
-m ${WALLET_ADDRESS} \
-l <LOGGING_LEVEL>
```
Где <CONTAINER_NAME> - название контейнера (вашей ноды), <LOGGING_LEVEL> - уровень логирования

Пример:

```
docker run \
-d \
--restart unless-stopped \
--pull always \
--name exorde-cli \
exordelabs/exorde-cli \
-m 0x273994219E6C0AD4B9dF71c67D062a0789FCFEAE \
-l 3
```

Подробнее про уровни логирования:

- 0 = ничего не логировать
- 1 = основные логи
- 2 = логи валидации
- 3 = логи валидации + логи журнала приложений
- 4 = детальные логи валидации + логи журнала приложений

### Проверка логов
```
docker logs Exorde
```
где Exorde - название контейнера 

Удаление ноды
```
sudo  docker stop Exorde &&  sudo  docker  rm Exorde
sudo  rm -rf ExordeModuleCLI
```
