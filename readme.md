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


