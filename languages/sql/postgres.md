# PostgreSQL

## basic commands
 - `psql -h <host ip> -d <database name> -p <port> -U <user>`
 - `EXPLAIN ANALYSE`
 - dump table: `\copy table_name to 'filename.csv' csv header` 
 [ref](https://serverfault.com/questions/393260/how-to-dump-a-part-of-a-table-from-postgresql)
 - read table: `COPY sample_table_name FROM 'C:\sampledb\sample_data.csv' DELIMITER ',' CSV HEADER;`
 [ref](https://www.postgresqltutorial.com/import-csv-file-into-posgresql-table/)
 - `SELECT COLUMN_NAME, DATA_TYPE FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = 'yourTableName'`
 [ref](https://stackoverflow.com/questions/13405572/sql-statement-to-get-column-type)
 - `\d <table name>`
 - `\v <view name>`
 - `select * from information_schema` list table
 - copy db: https://stackoverflow.com/questions/3195125/copy-a-table-from-one-database-to-another-in-postgres
   `pg_dump -t table_to_copy source_db | psql target_db`
## psql function
 - create change to alter might be great
 - https://www.postgresqltutorial.com/postgresql-plpgsql/postgresql-create-function/
 - https://www.postgresqltutorial.com/postgresql-plpgsql/postgresql-create-function/
 - document of create function https://www.postgresql.org/docs/current/sql-createfunction.html
 - variable in function
 - https://stackoverflow.com/questions/57690012/how-to-pass-a-string-parameter-to-plpgsql-function
 - https://stackoverflow.com/questions/24757976/using-variables-in-postgresql-function
 - qsql do script: https://stackoverflow.com/questions/38174506/psql-command-line-arguments-in-do-script
