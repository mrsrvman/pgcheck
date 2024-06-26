## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=xiongcccc/pgcheck&type=Date)](https://star-history.com/#xiongcccc/pgcheck&Date)

## Introduce

pgcheck is a one-click tool to get the running status of PostgreSQL, including stream replication/lock/wait events/partition/index/relation,etc., which makes the operation and maintenance more efficient.

The script currently being refactored with golang, so stay tuned!

### Note

The current supported versions include 11, 12, 13, 14, and 15. Other versions may be a little incompatible, and some of them report errors, but most of them can also be used. Currently supported platform is x86.

## Usage

~~~shell
Description: The utility is used to collect specified information
Current Version: 1.0.4
Usage:
 ./pgcheck relation database schema         : list information about tables and indexes in the specified schema
 ./pgcheck relconstraint database relname   : list all constraint corresponding to the specified table
 ./pgcheck alltoast database schema         : list all toasts and their corresponding tables
 ./pgcheck reltoast database relname        : list the toast information of the specified table
 ./pgcheck dbstatus                         : list all database status and statistics
 ./pgcheck index_bloat database             : index bloat information (estimated value)
 ./pgcheck index_duplicate database         : index duplicate information
 ./pgcheck index_low database               : index low efficiency information
 ./pgcheck index_state database             : index detail information
 ./pgcheck lock database                    : lock wait queue and lock wait state
 ./pgcheck checkpoint                       : background and checkpointer state
 ./pgcheck freeze database                  : database transaction id consuming state and detail
 ./pgcheck replication                      : streaming replication (physical) state
 ./pgcheck connections database             : database connections and current query
 ./pgcheck long_transaction database        : long transaction detail
 ./pgcheck relation_bloat database          : relation bloat information (estimated value)
 ./pgcheck vacuum_state database            : current vacuum progress information
 ./pgcheck vacuum_need database             : show tables that need vacuum
 ./pgcheck index_create database            : index create progress information
 ./pgcheck wal_archive                      : wal archive progress information
 ./pgcheck wal_generate wal_path            : wal generate speed (you should provide extra wal directory)
 ./pgcheck wait_event database              : wait event and wait event type
 ./pgcheck partition database               : native and inherit partition info (estimated value)
 ./pgcheck object database user             : get the objects owned by the user in the specified database
 ./pgcheck --help or -h                     : print this help information

 Author: xiongcc@PostgreSQL学徒, github: https://github.com/xiongcccc.
 If you have any feedback or suggestions, feel free to contact with me.
 Email: xiongcc_1994@126.com/xiongcc_1994@outlook.com. Wechat: _xiongcc
~~~
Currently supported features include：

- View the table status information in the specified schema
- View the information of all toast tables in the specified schema and the toast information of a specified table
- View the overall status information of the database, which will be different in different versions (please specify the exact version of the psql environment variable, because the system views of different versions will be different, and the judgment is made in the code, otherwise an error may be reported)
- View index bloat ratio/redundant index/inefficient index/index overall information
- View index information
- View lock state and lock queue 
- View checkpoint and background writer process status
- View age and transaction id consuming detail at database level
- View streaming replication status
- View the number of connections and queries currently being allowed
- View long transactions
- View table bloat, table bloat depends on statistical information, so in order to be more accurate, it is best to do an analysis before doing it, this query will take a little time
- View tables that need to execute vacuum and retrieves the oldest value for each of the vacuum operation blockers 
- Check the index creation progress, only supported in versions after 12, and the previous version will prompt that the view does not exist and exit
- View WAL archive status
- View WAL generation speed
- View wait event 
- View partition table information, including native partitions and inherited partitions
- View objects owned by a user, and member relationship

The default port used is 5432. If there are multiple instances on the server, you can specify environment variables before use, such as export PGPORT=5433。

If you have any feedback or suggestions, feel free to contact with me.
