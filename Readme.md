# What is it?
This repo contains docker-compose.yml file which allows you to create docker container with mysql example database - sakila.<br> 
You can connect to the database using localhost:3306 with root/root.

# Getting started:

## Requirement: install docker and docker-compose
https://www.docker.com/get-started

https://docs.docker.com/compose/install/

### 1. Run docker-compose

```bash
$ docker compose up

Attaching to sakila_mysql_db_1
...blah blah blah...
db_1  | 2020-12-14 19:46:24+00:00 [Note] [Entrypoint]: Creating database sakila
db_1  | 
db_1  | 2020-12-14 19:46:24+00:00 [Note] [Entrypoint]: /usr/local/bin/docker-entrypoint.sh: running /docker-entrypoint-initdb.d/1_sakila.sql
db_1  | 
db_1  | 
db_1  | 2020-12-14 19:46:25+00:00 [Note] [Entrypoint]: /usr/local/bin/docker-entrypoint.sh: running /docker-entrypoint-initdb.d/2_sakila.sql
db_1  | 
db_1  | 
db_1  | 2020-12-14 19:46:26+00:00 [Note] [Entrypoint]: Stopping temporary server
db_1  | 2020-12-14 19:46:28+00:00 [Note] [Entrypoint]: Temporary server stopped
db_1  | 
db_1  | 2020-12-14 19:46:28+00:00 [Note] [Entrypoint]: MySQL init process done. Ready for start up.
db_1  | 
db_1  | 2020-12-14T19:46:28.465715Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.22) starting as process 1
db_1  | 2020-12-14T19:46:28.478826Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
db_1  | 2020-12-14T19:46:28.655325Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
db_1  | 2020-12-14T19:46:28.738585Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Bind-address: '::' port: 33060, socket: /var/run/mysqld/mysqlx.sock
db_1  | 2020-12-14T19:46:28.847916Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
db_1  | 2020-12-14T19:46:28.848051Z 0 [System] [MY-013602] [Server] Channel mysql_main configured to support TLS. Encrypted connections are now supported for this channel.
db_1  | 2020-12-14T19:46:28.851679Z 0 [Warning] [MY-011810] [Server] Insecure configuration for --pid-file: Location '/var/run/mysqld' in the path is accessible to all OS users. Consider choosing a different directory.
db_1  | 2020-12-14T19:46:28.866651Z 0 [System] [MY-010931] [Server] /usr/sbin/mysqld: ready for connections. Version: '8.0.22'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server - GPL.
```

#### 2. Connect to mysql with mysql cli client & run some queries

```bash
$ mysql --protocol=tcp -u root -p  -P 3306 

mysql> use sakila;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> select * from actor;
+----------+-------------+--------------+---------------------+
| actor_id | first_name  | last_name    | last_update         |
+----------+-------------+--------------+---------------------+
|        1 | PENELOPE    | GUINESS      | 2006-02-15 04:34:33 |
|        2 | NICK        | WAHLBERG     | 2006-02-15 04:34:33 |
|        3 | ED          | CHASE        | 2006-02-15 04:34:33 |
|        4 | JENNIFER    | DAVIS        | 2006-02-15 04:34:33 |
```

#### 3. stop docker 
```bash
docker-compose down
```

Data will persist in ./dbdata catalog. You can remove it to recreate the fresh db.



LICENSE:

The contents of the 1_sakila.sql (sakila_schema.sql) and 2_sakila.sql (sakila_data.sql) files are licensed under the New BSD license.
See [sakila license](Sakila_license.md).

This repo is licensed under New BSD license. 