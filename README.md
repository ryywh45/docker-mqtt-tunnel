# docker-mqtt-tunnel

A minimal Docker Compose setup that exposes a **Mosquitto MQTT broker** through a **Cloudflare Tunnel**.
This allows you to run Mosquitto locally and securely access it from the internet without opening firewall ports or owning a public IP.

---

## File structure

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

## Quick Start

1. **Clone the repository**

    ```bash
    git clone https://github.com/ryywh45/docker-mqtt-tunnel.git
    cd docker-mqtt-tunnel
    ```

2. **Copy and edit the environment file**

    ```bash
    cp .env.example .env
    ```

    Open `.env` in an editor and provide the following values:

    - `CF_TUNNEL_TOKEN` – your Cloudflare Tunnel token.
    - `MQTT_USERNAME` – username to authenticate with the Mosquitto broker.
    - `MQTT_PASSWORD` – password for the MQTT user (plaintext is used by Mosquitto; consider using Docker secrets for production).

3. **Start the stack**

    ```bash
    docker compose up -d
    # or the legacy command: docker-compose up -d
    ```

    This will launch two containers:
    - `mosquitto` – the MQTT broker listening on `1883` internally.
    - `cloudflared` – the Cloudflare Tunnel client exposing the broker on a public hostname.

## Configuration

- **mosquitto.conf**: located in `mosquitto/config/mosquitto.conf`. You can adjust listener ports, persistence, logging, ACLs, etc.
- **.env variables**: control credentials and tunnel behaviour. See `.env.example` for defaults.
- **Persistence**: data and logs are stored under `mosquitto/data` and `mosquitto/log` with Docker volumes defined in `docker-compose.yml`.
