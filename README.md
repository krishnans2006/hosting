# Hosting

This repository handles my personal site and bot hosting on the cloud.

| Name | Type | Uses |
| --- | --- | --- |
| chesscordv1 | Discord Bot | Python -> Systemd |
| chesscordv2 | Discord Bot | Python -> Systemd |
| gitcord | Discord Bot | Python -> Systemd |
| tjcsl-discord-bot | Discord Bot | Python -> Systemd |
| website | Website | Python -> Gunicorn (:5000) -> Systemd -> Nginx (:80, www.) |
| vaultwarden | Website | Docker (:80 -> :3001) -> Systemd -> Nginx (:80 -> :443, vaultwarden.) |
| atuin | Website | Docker (:8888 -> :3002) -> Systemd -> Nginx (:80 -> :443, atuin.) |
| wakapi | Website | Docker (:3000 -> :3003) -> Systemd -> Nginx (:80, waka.) |

## App Setup

### ChessCord v1

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

Secrets:
- `.env` matching `sample.env`
- `creds.json` of a Firebase service account

### ChessCord v2

```bash
poetry install
```

Secrets:
- `.env` with `PYTHONUNBUFFERED=1`, `SECRET_KEY`, and `TOKEN`
- `data/creds.json` of a Firebase service account

### GitCord

```bash
poetry install
```

Secrets:
- `gitcord/config/secret.py` with `DEBUG = False` and `DISCORD_TOKEN = "..."`
- `gitcord/data/creds.json` of a Firebase service account

### TJ CSL Discord Bot

```bash
poetry install
```

Secrets:
- `tjcsl_discord_bot/config/secret.py` with `BOT_TOKEN = "..."` and `API_TOKEN = "..."`

### Website

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

Secrets:
- `creds.json` of a Firebase service account

### Vaultwarden

```
docker compose up
```

Secrets:
- `.env` with `PUSH_INSTALLATION_ID=...` and `PUSH_INSTALLATION_KEY=...`

### Atuin

```
docker compose up
```

Secrets:
- `.env` with `ATUIN_DB_NAME=atuin`, `ATUIN_DB_USERNAME=atuin`, and `ATUIN_DB_PASSWORD=...`

### Wakapi

```
docker compose up
```

Secrets:
- `.env` with `WAKAPI_PASSWORD_SALT=...`, `WAKAPI_MAIL_SMTP_PASS=...`, and `WAKAPI_DB_PASSWORD=...`

## Generic SSL Setup

- Use `/home/ubuntu/ssl/star_krishy_dev.*`
- Ensure Cloudflare is set to Full SSL (see [here](https://serverfault.com/a/1131003/968608)), either globally or through a page rule
- Clear browser cache when testing, since the redirect is a 301
