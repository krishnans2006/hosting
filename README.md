# hosting

This repository handles my personal site and bot hosting on the cloud.

| Name | Type | Uses |
| --- | --- | --- |
| ChessCord v1 | Discord Bot | Python -> Systemd |
| ChessCord v2 | Discord Bot | Python -> Systemd |
| GitCord | Discord Bot | Python -> Systemd |
| TJ CSL | Discord Bot | Python -> Systemd |
| Personal | Website | Python -> Gunicorn (:5000) -> Systemd -> Nginx (:80, www.) |
| Wakapi | Website | Docker (:3000 -> :3100) -> Systemd -> Nginx (:80, waka.) |
| Vaultwarden | Website | Docker (:80 -> :3001) -> Systemd -> Nginx (:80 -> :443, vaultwarden.) |

## SSL Setup

- Use `/home/ubuntu/ssl/star_krishy_dev.*`
- Ensure Cloudflare is set to Full SSL (see [here](https://serverfault.com/a/1131003/968608)), either globally or through a page rule
- Clear browser cache when testing, since the redirect is a 301
