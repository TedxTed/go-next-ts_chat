# Database Setup

## Pull PostgreSQL Image

```bash
docker pull postgres:15-alpine
```

## Run PostgreSQL Container

```bash
docker run --name postgres15 -p 5433:5432 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=password -d postgres:15-alpine
```

## Create database

```bash
docker exec -it postgres15 createdb --username=root --owner=root go-chat
```

## check db
go into container
```bash
docker exec -it postgres15 psql
```
check db list -> `\l`
```bash
root=#  \l
```
exit
```bash
root=# \q
```

## migrate package

https://github.com/golang-migrate/migrate

use cli create migration 
```bash
migrate create  -ext sql -dir db/migrations add_users_table
```

migrate up 
```bash
migrate -path db/migrations -database "postgresql://root:password@localhost:5433/go-chat?sslmode=disable" -verbose up
```

### check users is exist 
#### into db
```bash
make postgres
```
#### list all db 
```bash
psql (15.6)
Type "help" for help.

root=# \l
```

#### go into go-chat
```bash
root=# \c go-chat
```

#### list all table 
```bash
go-chat=# \d
```

#### list specfic table info
```bash
go-chat=# \d users 
```

