# Installing postgres (pg)
Full instructions at https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-centos-7

## Setup a new database
```
sudo postgresql-setup initdb
```

##  Start a database
```
pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log start
```

## Stop database
```
pg_ctl -D /usr/local/var/postgres stop -s -m fast
```

## Connect to database
```
psql -h hostname -U username databasename
```


## Create a DB users
```
CREATE USER username WITH PASSWORD password;
GRANT ALL PRIVILEGES ON DATABASE databsename to username;
```

## Common psql commands

List all databases
```
\l
```

List tables in databases using psql
```
\d
```
(d stands for describe)

For more details:
```
\d+
```


Describe a table
```
\d employees
\d+ employees
```
