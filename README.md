# This is a shameless copy from 

https://github.com/kevin-morgan/trojan-caddy-docker-compose.git

Where I only replace docker-compose from building docker container locally to a pre-built image by me.

# trojan-caddy-docker-compose

Trojan server and Caddy integration with Docker compose。

Trojan server listens port 443. For https requests from normal sources, Trojan server will forward them to Caddy server for processing and return to the Web page while requests from Trojan client will be proxied by Trojan server which like V2ray+Websocket+TLS avoid GFW detection by disguising requests.

## Usage

Git clone this repo then change directory to this project.

1. Modify `./caddy/Caddyfile`:
    ```
    www.yourdomain.com:80 {
        root /usr/src/trojan
        log /usr/src/caddy.log
        index index.html
    }

    www.yourdomain.com:443 {
        root /usr/src/trojan
        log /usr/src/caddy.log
        index index.html
    }
    ```
    Replace `www.yourdomain.com` with your own domain name.

2. Modify `./trojan/config/config.json`:

    Change `your_password` to your own password on `config:json:8` , this is your trojan password just safekeeping.
    
    Change `your_domain_name` to your own domain name on `config:json:12-13`, this is your domain ssl certification path, Caddy server generate certs automatically on the path `/ssl/your_domain_name/your_domain_name.crt`
 
3. Run `docker-compose up` or `docker-compose up -d`  with Daemon mode

## Tips

If you encounter any problems during the deployment process, you can raise them in' issue' considering various unknown situations.
