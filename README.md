# Simple knowledge base - Kicking off sqitch, just follow steps

## run docker locally server

```
docker run -p 5432:5432 \
--name some-postgres \
 --network=bridge \
 -e POSTGRES_PASSWORD=root \
 -d postgres
```

## docker UI pgadmin (not required)

```
docker run -p 8080:80 \
 -e 'PGADMIN_DEFAULT_EMAIL=root' \
 -e 'PGADMIN_DEFAULT_PASSWORD=root' \
 -d dpage/pgadmin4 --network=bridge
 ```

## pull latest sqitch image

```
docker pull sqitch/sqitch
```

## create db
```
Note: Install psql client

createdb flipr_test -h localhost -U postgres
```

## setup project 
```
./sqitch.sh init sqitch-base --engine pg
```

```
./sqitch.sh target add sqitch-base db:postgresql://localhost/flipr_test
```

```
export SQITCH_USERNAME="postgres"
export SQITCH_PASSWORD="root"
export HOST="localhost"
```

## creating a new object to apply (check sqitch.plan after applying code below)

```
./sqitch add appschema -n 'Add schema for all flipr objects.'
```

After setup we just need to call functions below:

```
./sqitch.sh deploy
```

```
./sqitch.sh verify
```

```
./sqitch.sh status
```

```
./sqitch.sh revert
```

```
./sqitch.sh log
```