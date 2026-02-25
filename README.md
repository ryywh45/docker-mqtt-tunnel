# docker-mqtt-tunnel

### File structure
```
├── .github/
├── mosquitto/
│   ├── config/
│   │   └── mosquitto.conf
│   ├── data/
│   └── log/
├── .env.example
├── .gitignore
├── docker-compose.yml
└── README.md
```

### Quick Start
1. Clone:
```Bash
git clone https://github.com/ryywh45/docker-mqtt-tunnel.git
cd docker-mqtt-tunnel
```

2. Setup environment:
```Bash
cp .env.example .env
# Edit .env and add your Cloudflare Tunnel Token
```

3. Launch the stack:
```Bash
docker compose up -d
# or legacy "docker-compose up -d"
```

4. Create a User:
```Bash
docker exec -it mosquitto mosquitto_passwd -c /mosquitto/config/pwfile your_username_here
```
