# Bytesafe-CE PostgreSQL Schema 
The following is provided as reference for users that want or need to create the bytesafe-ce databases manually. 

The scripts here are embedded in bytesafe-ce and executed when  `--setupdb` command line option is provided **and** bytesafe-ce fails to connect to the `bytesafe` database.

The scripts are executed in the following order "01-system", "bytesafe", "advisories", "events", "metrics".

Scripts are expected to be executed by PostgreSQL admin user. Bytesafe-CE defaults to "postgres", this can be overridden with `DB_ADMIN_*` environment variables.
For more information, detailed instructions and configuration options please see [Bytesafe Community docs](https://docs.bytesafe.dev/community-edition).
