

## convert timestamp
 - from unixtime
   `select to_timestamp(unix_time) as datetime from table;`
 - create unixtime
    `SELECT DATE_PART('EPOCH', TIMESTAMP '2024-03-26');`
    `select extract(epoch from now());`
