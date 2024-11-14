<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="200" alt="Nest Logo" /></a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

  <p align="center">A progressive <a href="http://nodejs.org" target="_blank">Node.js</a> framework for building efficient and scalable server-side applications.</p>
<p align="center">
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/dm/@nestjs/common.svg" alt="NPM Downloads" /></a>
<a href="https://circleci.com/gh/nestjs/nest" target="_blank"><img src="https://img.shields.io/circleci/build/github/nestjs/nest/master" alt="CircleCI" /></a>
<a href="https://coveralls.io/github/nestjs/nest?branch=master" target="_blank"><img src="https://coveralls.io/repos/github/nestjs/nest/badge.svg?branch=master#9" alt="Coverage" /></a>
<a href="https://discord.gg/G7Qnnhy" target="_blank"><img src="https://img.shields.io/badge/discord-online-brightgreen.svg" alt="Discord"/></a>
<a href="https://opencollective.com/nest#backer" target="_blank"><img src="https://opencollective.com/nest/backers/badge.svg" alt="Backers on Open Collective" /></a>
<a href="https://opencollective.com/nest#sponsor" target="_blank"><img src="https://opencollective.com/nest/sponsors/badge.svg" alt="Sponsors on Open Collective" /></a>
  <a href="https://paypal.me/kamilmysliwiec" target="_blank"><img src="https://img.shields.io/badge/Donate-PayPal-ff3f59.svg"/></a>
<a href="https://opencollective.com/nest#sponsor"  target="_blank"><img src="https://img.shields.io/badge/Support%20us-Open%20Collective-41B883.svg" alt="Support us"></a>
  <a href="https://twitter.com/nestframework" target="_blank"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow"></a>
</p>
  <!--[![Backers on Open Collective](https://opencollective.com/nest/backers/badge.svg)](https://opencollective.com/nest#backer)
  [![Sponsors on Open Collective](https://opencollective.com/nest/sponsors/badge.svg)](https://opencollective.com/nest#sponsor)-->

## Description

[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository.

## Installation

```bash
# with pnpm
$ pnpm install

# with docker
$ docker compose build
```

## Useful command

```bash
# update database schema
$ pnpm db:push

# generate model from connection
$ pnpm db:pull

# generate db client
$ pnpm db:generate

# create new feature with single command
$ pnpm make:app

# run app with single command
$ docker compose up -d
```

## Running the app

```bash
# development
$ pnpm run start

# watch mode
$ pnpm run start:dev

# production mode
$ pnpm run start:prod

# production mode with docker
$ docker compose up -d
```

## Test

```bash
# unit tests
$ pnpm run test

# e2e tests
$ pnpm run test:e2e

# test coverage
$ pnpm run test:cov
```

## Install Nginx

1. **Update your package list**:

```bash
sudo apt update
```

2. **Install Nginx**:

```bash
sudo apt install nginx -y
```

3. **Start and enable Nginx**:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

4. **Verify Nginx Installation**:

Visit your server's IP in a browser to see if Nginx’s default page is displayed.

---

## Configure Nginx as a Reverse Proxy

1. **Create a new configuration file**:

```bash
sudo nano /etc/nginx/sites-available/myapp.conf
```

2. **Add the reverse proxy configuration**:

Replace `myapp.example.com` with your domain name and `http://localhost:3000` with the IP and port of the service you’re proxying to.

```nginx
    server {
    listen 80;
    server_name myapp.example.com;

    location / {
    proxy_pass http://localhost:3000;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
}
}
```

3. **Enable the configuration**:

```bash
sudo ln -s /etc/nginx/sites-available/myapp.conf /etc/nginx/sites-enabled/
```

4. **Test the configuration**:

```bash
sudo nginx -t
```

5. **Reload Nginx**:

```bash
sudo systemctl reload nginx
```

---

## Install Certbot and Configure SSL

1. **Install Certbot**:

```bash
sudo apt install certbot python3-certbot-nginx -y
```

2. **Request an SSL Certificate**:

```bash
sudo certbot --nginx -d myapp.example.com
```

3. **Follow the prompts**:
- Certbot will ask for your email and agreement to terms of service.
- It will automatically modify your Nginx configuration to support SSL.

4. **Verify SSL**:

Visit `https://myapp.example.com` in your browser to ensure the certificate is active.

5. **Set up Automatic Renewal**:

Certbot installs a cron job to renew certificates automatically. You can test it with:

```bash
sudo certbot renew --dry-run
```

---

## Configure Firewall (Using UFW)

1. **Install UFW (if not already installed)**:

```bash
sudo apt install ufw -y
```

2. **Allow OpenSSH** (to prevent locking yourself out):

```bash
sudo ufw allow OpenSSH
```

3. **Allow HTTP and HTTPS traffic**:

```bash
sudo ufw allow 'Nginx Full'
```

4. **Enable the Firewall**:

```bash
sudo ufw enable
```

5. **Check the Status**:

```bash
sudo ufw status
```
