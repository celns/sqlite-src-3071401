### `main.c`作为实现了SQLite大部分接口的源文件，以下是对其接口及相关说明的表格整理
|函数定义|说明|
|:----:|:----:|
|int sqlite3_threadsafe(void);|测试以查看库是否是线程安全的
|int sqlite3_initialize(void)|初始化SQLite库
|int  sqlite3_shutdown(void)|取消分配由sqlite3_initialize()分配的所有资源
|int  sqlite3_config(int op，...)|用于对SQLite进行全局配置更改
|int  sqlite3_db_release_memory(sqlite3 * db)|尝试从数据库连接D释放尽可能多的堆内存
|int  sqlite3_db_config(sqlite3 * db，int op，...)|对数据库连接进行配置更改
|int  sqlite3_changes(sqlite3 * db)|返回由only参数指定的数据库连接上最近完成的INSERT，UPDATE或DELETE语句修改，插入或删除的行数
|int  sqlite3_total_changes(sqlite3 * db)|返回自打开数据库连接以来已完成的所有INSERT，UPDATE或DELETE语句插入，修改或删除的行总数，包括作为触发器程序一部分执行的行数
|int sqlite3_busy_handler(sqlite3*,int(\*)(void*,int),void*);|注册回调以处理SQLITE_BUSY错误
|void sqlite3_progress_handler(sqlite3*, int, int(\*)(void*), void*);|查询进度回调
|void sqlite3_interrupt(sqlite3*);|中断长时间运行的查询
|int sqlite3_create_function(sqlite3 \*db,const char \*zFunctionName,int nArg,int eTextRep,void \*pApp,void (\*xFunc)(sqlite3_context*,int,sqlite3_value*\*),void (\*xStep)(sqlite3_context*,int,sqlite3_value*\*),void (\*xFinal)(sqlite3_context*));|创建或重新定义SQL函数
|int sqlite3_overload_function(sqlite3*, const char *zFuncName, int nArg);|重载虚拟表的功能
|void \*sqlite3_trace(sqlite3*,void(\*xTrace)(void*,const char*), void*);|跟踪和分析函数
|void \*sqlite3_commit_hook(sqlite3*, int(\*)(void*), void*);|提交hook回调, 只要提交事务即可调用该回调函数
|int sqlite3_wal_autocheckpoint(sqlite3 *db, int N);|配置自动检查点
|int sqlite3_limit(sqlite3*, int id, int newVal);|运行时限制, 允许在每个连接的上限制各种构造的大小
|int sqlite3_open(const char *filename,sqlite3 *\*ppDb);|打开一个新的数据库连接
|int sqlite3_create_collation(sqlite3*, const char \*zName, int eTextRep, void \*pArg,int(\*xCompare)(void*,int,const void*,int,const void*));|定义新的整理顺序
|int sqlite3_collation_needed(sqlite3*, void*, void(\*)(void*,sqlite3*,int eTextRep,const char*));|排序规则需求的回调, 为了避免在使用数据库之前必须注册所有排序规则序列，只要需要未定义的排序规则序列，就可以向要调用的数据库连接注册单个回调函数 
|int sqlite3_table_column_metadata(...);|提取有关表的列的元数据
|int sqlite3_sleep(int);|使当前线程在其参数中指定的以毫秒为单位的时间内挂起
|int sqlite3_extended_result_codes(sqlite3*, int onoff);|启用或禁用扩展结果代码，默认情况下，扩展结果代码是禁用的
|int sqlite3_test_control(int op, ...);|测试接口
|const char *sqlite3_db_filename(sqlite3 *db, const char *zDbName);|返回数据库连接的文件名
***
以上表格囊括了`main.c`中大部分的接口，未包括的还有一些SQLite对错误和异常进行处理的接口和一些基础库信息获取的接口（例如SQLite运行时版本号等等）。