# Официальные ссылки
### [Site](https://exorde.network/)
### [Docs](https://docs.exorde.network/)
### [Discord](https://discord.gg/exordelabs)
### [Еxplorer](https://explorer.exorde.network/)
### [Leaderboard](https://explorer.exorde.network/leaderboard)


## System Requirements
- Windows 8.1/10/11 or Linux or macOS
- 4 GB RAM
- 2 CPU cores
- 1 GB storage (HDD or SSD)

# Node Install 

### Set variables
```
WALLET_ADDRESS=<METAMASK WALLET ADDRESS>
```

Where `<METAMASK WALLET ADDRESS>` is your Metamask address

```
echo export WALLET_ADDRESS=${WALLET_ADDRESS} >> $HOME/.bash_profile
source ~/.bash_profile
```

### Install the updates for each package and dependency
```
cd $HOME
sudo apt update && sudo apt upgrade -y
sudo apt install curl build-essential git wget npm jq make gcc tmux -y && apt purge docker docker-engine docker.io containerd docker-compose -y
```

### Install Docker
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

Example:

```
docker run \
-d \
--restart unless-stopped \
--pull always \
--name Exorde-container \
exordelabs/exorde-cli \
-m 0x273994219E6C0AD4B9dF71c67D062a0789FCFEAE \
-l 3
```

Where <CONTAINER_NAME> - container name, <LOGGING_LEVEL> is a level of logging

- 0 = no logs
- 1 = general logs
- 2 = validation logs
- 3 = validation + scraping logs
- 4 = detailed validation + scraping logs (e.g. for troubleshooting)

### How to Check the logs
```
docker logs Exorde-container
```
Where Exorde-container - name of you container

Удаление ноды
```
sudo  docker stop Exorde-container &&  sudo  docker  rm Exorde-container
sudo  rm -rf Exorde-container
```
