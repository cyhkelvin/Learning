# PostgreSQL

## basic commands
 - `psql -h <ip> -d <name> -p <port> -U <user>`
 - `EXPLAIN ANALYSE`
 - dump table: `\copy table_name to 'filename.csv' csv header` 
 [ref](https://serverfault.com/questions/393260/how-to-dump-a-part-of-a-table-from-postgresql)
 - read table: `COPY sample_table_name FROM 'C:\sampledb\sample_data.csv' DELIMITER ',' CSV HEADER;`
 [ref](https://www.postgresqltutorial.com/import-csv-file-into-posgresql-table/)
 - `SELECT COLUMN_NAME, DATA_TYPE FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = 'yourTableName'`
 [ref](https://stackoverflow.com/questions/13405572/sql-statement-to-get-column-type)
