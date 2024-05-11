# S4DFarm

This is a fork of [DestructiveFarm](https://github.com/DestructiveVoice/DestructiveFarm), 
rewritten by the C4T BuT S4D team over the years.

## Setup
- In compose.yml change `SERVER_PASSWORD` env for service `farm` and `EXTERNAL_REDIS_PASSWORD` env in `external_redis` launch cmd
- Fill [./server/app/config.py](./server/app/config.py) with info from CTF's organizers
- If needed, develop checksystem protocol code and store it in `server/app/protocols/`. Change the [./server/app/config.py](./server/app/config.py) to setup protocol settings

## Running

Before launching, `docker-compose` must be installed on the system. Here is example of commands that is needed to
install `docker-compose` on Ubuntu 22.04:
```
sudo apt-get update
sudo apt-get install git apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce

mkdir -p ~/.docker/cli-plugins/
curl -SL https://github.com/docker/compose/releases/download/v2.3.3/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose
chmod +x ~/.docker/cli-plugins/docker-compose
```

Then, you can run farm by:
```
docker compose up --build -d
```

## Removal
If you need to reset farm, you can do it by executing:
```
docker compose down -v
# Remove DB
rm -rf ./vol
```

## Screenshots

![flags](resources/flags.png)

![teams](resources/teams.png)
