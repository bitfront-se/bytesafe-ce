# Bytesafe Community Edition

[Bytesafe](https://bytesafe.dev) is a security platform that protects organizations from open source software supply chain attacks.

Bytesafe provides repositories for **npm**, **Maven**, **Nuget** and **PyPI** package managers. It supports pulling packages from public repositories, caching and proxying them, and hosting private packages.
The Dependency Firewall capability provides automated security checks for all packages, such as vulnerability scanning, with automatic quarantining of policy breaking packages.

The Community Edition of Bytesafe is free to download and use. Data is stored in PostgreSQL and Redis for efficient caching. Package artifacts are stored in the local file system, making it a convenient solution for many use cases.

For production workflows requiring high availability, disaster recovery, the convenience of a managed service or more advanced features such as License Compliance, we recommend our [Business or Enterprise](https://bytesafe.dev/pricing) cloud offerings.

## Quick Start using Docker Compose

Using Docker Compose to install Bytesafe Community edition together with PostgreSQL and Redis will get you started in minutes:

1. Download the `docker-compose.yml` file to your host.
2. Create an **.env** file with a unique and secret value for the **DATA_ENCRYPTION_KEY** environment variable. This value is used to encrypt sensitive data such as credentials.
3. Use docker compose to start Bytesafe + PostgreSQL + Redis.


```bash
$ curl -O https://raw.githubusercontent.com/bitfront-se/bytesafe-ce/master/docker-compose.yml
$ echo "DATA_ENCRYPTION_KEY='$(cat /dev/urandom | LC_ALL=C tr -dc 'a-zA-Z0-9' | fold -w 50 | head -n 1)'" > .env
$ docker compose up
```

4. Open up a web browser and create your workspace owner account: [http://localhost:8081/](http://localhost:8081/)

For more information, detailed instructions and configuration options please see [Bytesafe Community docs](https://docs.bytesafe.dev/community-edition).
