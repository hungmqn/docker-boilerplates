# Start

1. Rename `.env.sample` to `.env`.
2. Command

```shell
docker-compose up -d
```

# Backup sql

docker exec -t postgres*postgres_1 pg_dumpall -c -U pgus > dump*$(date +%Y-%m-%d*%H*%M\_%S).sql

# Restore sql

cat dump_file.sql | docker exec -i postgres_postgres_1 psql -U pgus -d pgdb

# Backup gz

docker exec -t postgres*postgres_1 pg_dumpall -c -U pgus | gzip > dump*$(date +%Y-%m-%d*%H*%M\_%S).sql.gz

# Restore gz

gunzip < dump_file.sql.gz | docker exec -i postgres_postgres_1 psql -U pgus -d pgdb
