# Quick nginx server

I use this image to quickly set up a docker nginx image for local webserver testing without having to struggle with
certificates.

## usage

Create self-signed certificate.

```bash
openssl req -newkey rsa:2048 -noenc -keyout localhost.key -x509 -days 365 -out localhost.crt -subj "/C=DE/ST=State/L=Location/O=Amogus/OU=SUS/CN=localhost"
```

Copy the template

```bash
cp docker-compose.template.yml docker-compose.yml
```

Change the local_webserver part of this line in the compose file to the desired root.

```yml
[...]
volumes:
  - './local_webserver:/var/www'
[...]
```

Start the container

```bash
docker compose up -d
```
