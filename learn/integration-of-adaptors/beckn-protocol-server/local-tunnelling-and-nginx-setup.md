# Local Tunnelling and Nginx Setup

## Exposing local Protocol-server to Internet

### Setting up LocalTunnel when there is no DNS tool available

Note: use this when you don't have any DNS URLs to assign

1. Install local tunnel globally using `npm install -g localtunnel`.
2. Run `lt --port <BAP/BPP network port> --subdomain <any subdomain>` for both BAP and BPP networks (use the same subdomain each time for consistency). \[Example: `lt --port 5001 --subdomain beckn-bap-network`]

**Note: Whenever the system or LocalTunnel is restarted the the generated localtunnel DNS will be changed. We have to register the newly generated local-tunnel DNS after restarting in Registry and default.yml files respectively.**

### Nginx in Production System (Ubuntu) if you have DNS Tools

Nginx is used to

1. Update your system: `sudo apt update`.
2. Install Nginx: `sudo apt-get install nginx -y`.
3. Navigate to the Nginx configuration directory: `cd /etc/nginx/conf.d`.
4. Create a new configuration file: `sudo nano {enter-any-name.conf}`. Enter the configuration to map your DNS with the port of BAP/BPP Network\&Client.

**Example Configuration:**

```
server {
    listen 80;
    listen [::]:80;
    server_name example.domain.com;

    location / {
        proxy_set_header Host $http_host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";

        proxy_pass http://localhost:port;
    }
}

server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    server_name example.domain.com;

    location / {
        proxy_set_header Host $http_host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";

        proxy_pass http://localhost:port;
    }

    ssl_certificate /etc/letsencrypt/live/example.domain.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/example.domain.com/privkey.pem;

    ssl_session_timeout 1d;
    ssl_session_cache shared:MozSSL:10m;
    ssl_session_tickets off;

    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-
    ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384;
    ssl_prefer_server_ciphers on;

    add_header Strict-Transport-Security "max-age=63072000" always;

    ssl_stapling on;
    ssl_stapling_verify on;

    resolver 8.8.8.8;
}
```

Replace `example.domain.com` and `port` with your desired values in multiple places.

Obtain an SSL certificate for your domain and configure it on your machine.
