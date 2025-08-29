Docker Setup

https://docs.docker.com/engine/install/

```bash
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

# Add Docker's official GPG key:
```bash

sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

# Add the repository to Apt sources:
```bash

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

```bash
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

```bash

sudo docker run hello-world


sudo groupadd docker

sudo usermod -aG docker $USER

newgrp docker

docker run hello-world



docker run --env-file .env -p 80:80 dwani/proxy-server:latest
```

- Build Proxy Server 
```bash
docker build -t dwani/proxy-server:latest -f Dockerfile .


docker push dwani/proxy-server:latest
```

---


Proxy Server

```bash
git clone https://github.com/dwani-ai/proxy-server.git
cd proxy-server
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

python src/server/main.py
```

For Load balancer 

```bash
git clone https://github.com/dwani-ai/proxy-server.git
cd proxy-server
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

python src/server/load_balancer.py

```