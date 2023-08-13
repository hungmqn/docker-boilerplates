Backup sql

docker exec -t postgres_postgres_1 pg_dumpall -c -U pgus > dump_$(date +%Y-%m-%d_%H_%M_%S).sql

Restore sql

cat dump_file.sql | docker exec -i postgres_postgres_1 psql -U pgus -d pgdb


Backup gz

docker exec -t postgres_postgres_1 pg_dumpall -c -U pgus | gzip > dump_$(date +%Y-%m-%d_%H_%M_%S).sql.gz

Restore gz

gunzip < dump_file.sql.gz | docker exec -i postgres_postgres_1 psql -U pgus -d pgdb