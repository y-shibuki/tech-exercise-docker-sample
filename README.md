# tech-exercise-docker-sample

## フォルダ構成

```bash
tech-exercise-docker-sample
├── README.md
├── docker
│   ├── Dockerfile
│   ├── apache
│   │   ├── django-apache.conf
│   │   └── ports.conf
│   └── mysql
│       └── my.cnf
├── docker-compose.yml
├── project
│   └── ...
└── requirements.txt
```

## Dockerの導入手順（CentOS 9）

```bash
sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
docker --version
```

dockerの起動

```bash
sudo systemctl enable docker
sudo systemctl start docker
sudo systemctl status docker
```

sudo無しでdockerを実行できるように変更。コマンド実行後にログインし直す。

```bash
sudo gpasswd -a ユーザ名 docker
```

以下のコマンドで、バージョンが表示されたらOK

```bash
docker compose version
```

## 実行方法

```bash
sudo dnf install -y git
git clone リポジトリURL
cd tech-exercise-docker-sample
```

環境変数を設定

```bash
cp project/.env.sample project/.env.local
vi project/.env.local
```

コンテナの立ち上げ

```bash
docker compose up -d
```
