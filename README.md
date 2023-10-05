## INSTALL DOCKER UBUNTU

### TAMBAHKAN KUNCI GPG DOCKER
```sudo apt update```

```sudo apt-get install ca-certificates curl gnupg```

```sudo install -m 0755 -d /etc/apt/keyrings```

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```sudo chmod a+r /etc/apt/keyrings/docker.gpg```

### TAMBAHKAN REPOSITORY DOCKER
```
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```sudo apt-get update```

### VERIFIKASI REPO DARI DOCKER
```apt-cache policy docker-ce```

### INSTALL
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-compose
```

### CEK STATUS DOCKER
```sudo systemctl status docker```

### TAMBAHKAN USER KE GROUP DOCKER
```sudo usermod -aG docker ${USER}```

Setelah user ditambahkan ke group docker, logout dulu kemudian login lagi.

### CEK GROUPS USER
```groups```

### CEK AKSES DOCKER
```docker info```

## INSTALL SERVER OWNCLOUD

Bikin folder dulu

```mkdir owncloud```

```cd owncloud```

Bikin file ```.env```

```
cat << EOF > .env
OWNCLOUD_VERSION=10.13
OWNCLOUD_DOMAIN=localhost:8080
OWNCLOUD_TRUSTED_DOMAINS=localhost
ADMIN_USERNAME=admin
ADMIN_PASSWORD=admin
HTTP_PORT=8080
EOF
```

### DOWNLOAD FILE OWNCLOUD YML UNTUK DOCKER-COMPOSE
```
wget https://raw.githubusercontent.com/owncloud/docs-server/master/modules/admin_manual/examples/installation/docker/docker-compose.yml
```

Kemudian jalankan ```docker-compose up atau docker-compose up -d``` untuk menginstall semua persyaratan yang dibutuhkan

### AKSES SERVER OWNCLOUD
Buka browser dan akses ```IP_SERVER:8080```