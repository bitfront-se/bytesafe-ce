## Nginx configuration for SSL support 

Using the provided docker-compose-ssl.xml in addition to the docker-compose.xml will provide a local Bytesafe installation with HTTPS capabilities.

1. Clone the bytesafe-ce repository or download all the files indiviually
2. Create an **.env** file with a unique and secret value for the **DATA_ENCRYPTION_KEY** environment variable. This value is used to encrypt sensitive data such as credentials.
```shell
$ git clone https://github.com/bitfront-se/bytesafe-ce.git
$ cd examples/nginx-ssl
$ echo "DATA_ENCRYPTION_KEY='$(cat /dev/urandom | LC_ALL=C tr -dc 'a-zA-Z0-9' | fold -w 50 | head -n 1)'" > .env
```

3. Set up local certificates using [mkcert](https://github.com/FiloSottile/mkcert#installation).

:exclamation: Please note that this will install a root certificate in your system trust. Please make sure you understand what this means before proceeding.   

```shell
$ brew install mkcert
...
$ mkcert -install 
Created a new local CA 💥
The local CA is now installed in the system trust store! ⚡️
The local CA is now installed in the Firefox trust store (requires browser restart)! 🦊
$ mkcert -key-file certs/ssl.key -cert-file certs/ssl.crt localhost 
```
4. Use docker compose to start Bytesafe + PostgreSQL + Redis + Nginx.

```
$ docker compose -f docker-compose.yml -f docker-compose-ssl.yml up
```

5. Open up a web browser and create your workspace owner account: [https://localhost:8443/](https://localhost:8443/)

For more information, detailed instructions and configuration options please see [Bytesafe Community docs](https://docs.bytesafe.dev/community-edition).
