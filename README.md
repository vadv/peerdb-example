# peerdb-example

## clickhouse:

```sql
create database peerdb;
create role peerdb_role;
grant all on peerdb.* TO peerdb_role;
grant CREATE TEMPORARY TABLE, S3 ON *.* to peerdb_role;
create user peerdb_user DEFAULT ROLE ALL IDENTIFIED WITH plaintext_password BY 'password';
grant peerdb_role to peerdb_user;

CREATE TABLE peerdb.test_table
(
    `id` Int32,
    `float` Float32,
    `uid` Nullable(String),
    `int32` Int32,
    `datetime` Nullable(DateTime64(6)),
    `bool` Bool,
...
)
ENGINE = ReplacingMergeTree(id)
PRIMARY KEY id
ORDER BY id
SETTINGS index_granularity = 8192;
```

```bash
$ cat /etc/hosts

127.0.0.1 host.docker.internal
```

## postgresql:

```sql
create user peerdb_user with password 'password';
grant pg_read_all_data to peerdb_user;
```