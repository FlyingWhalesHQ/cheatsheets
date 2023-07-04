---
layout: default
title: Postgresql
parent: Database
---

{% include toc.md %}

## Connection Strings

Postgresql has the connection string format as follow

```
postgresql://[user[:password]@][netloc][:port][/dbname][?param1=value1&...]
```

`postgresql://` or `postgres://` is the required prefix to identify that
this is a string in the standard connection format. The rest is optional.

Examples:

```
postgresql://
postgresql://localhost
postgresql://localhost:5433
postgresql://localhost/mydb
postgresql://user@localhost
postgresql://user:secret@localhost
postgresql://other@localhost/otherdb?connect_timeout=10&application_name=myapp
postgresql://host1:123,host2:456/somedb?target_session_attrs=any&application_name=myapp
```

Ref: [https://www.postgresql.org/docs/current/libpq-connect.html#LIBPQ-CONNSTRING](https://www.postgresql.org/docs/current/libpq-connect.html#LIBPQ-CONNSTRING)

## Backup & Restore

With `pg_dump` and `pg_restore`:

```sh
# backup
# -h: host URL, default is localhost
# -U: admin username of the database
# -p: port, default is 5432
# -Fc: custom dump format that is compatible with pg_restore
pg_dump -h <db_host> -U <db_username> -p <db_port> -Fc <db_name> > <path/to/dump_file.pgsql>

# restore
# -d: connection string to the database to restore to
# --jobs: number of parallel jobs to use for restoring
pg_restore -d <db_connection_string> --jobs 4 <path/to/your_dump_file.pgsql>
```

With `pg_dumpall` and `psql`:

```sh
# backup
# -h: host URL, default is localhost
# -U: admin username of the database
# -p: port, default is 5432
pg_dumpall -h <db_host> -U <db_username> -p <db_port> > <path/to/dump_file.sql>

# restore
# -d: connection string to the database to restore to
psql -d <db_connection_string> < <path/to/dump_file.sql>
```
