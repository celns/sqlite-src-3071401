# util.c
### 基础通用工具(Utilities)包括了一些基本的函数或方法库，以下是函数列表整理
|函数定义|说明|
|:----:|:----:|
|int sqlite3Strlen30(const char *z);|计算字符串长度,最长30位
|void sqlite3Error(sqlite3 *db, int err_code, const char *zFormat, ...);|处理“db”错误代码“err_code”
|void sqlite3ErrorMsg(Parse *pParse, const char *zFormat, ...);|报告在运行过程中发生的任何错误
|int sqlite3Dequote(char *z);|转换SQL样式的带引号的字符串为普通字符串
|int sqlite3_stricmp(const char *zLeft, const char *zRight);|字符串比较
|int sqlite3AtoF(const char *z, double *pResult, int length, u8 enc);|将实数字符串转换为双精度浮点数
|static int compare2pow63(const char *zNum, int incr);|将19个字符的字符串zNum与2^63比较
|int sqlite3Atoi64(const char *zNum, i64 *pNum, int length, u8 enc);|将zNum转换为64位有符号整数
|int sqlite3GetInt32(const char *zNum, int *pValue);|返回zNum表示的32位的整数
|int sqlite3Atoi(const char *z);|返回从字符串中提取的32位整数值
|int sqlite3PutVarint(unsigned char *p, u64 v);|从p\[0]开始将64位可变长整数写入内存
|int sqlite3PutVarint32(unsigned char *p, u32 v);|`sqlite3PutVarint()`的更快版本
|u8 sqlite3GetVarint(const unsigned char *p, u64 *v);|从p\[0]开始从内存中读取64位可变长度整数
|u8 sqlite3GetVarint32(const unsigned char *p, u32 *v);|从p\[0]开始从内存中读取32位可变长度整数
|int sqlite3VarintLen(u64 v);|返回存储给定字节所需的字节数
|u32 sqlite3Get4byte(const u8 *p);|读取一个四字节的big-endian整数值
|void sqlite3Put4byte(unsigned char *p, u32 v);|写入一个四字节的big-endian整数值
|u8 sqlite3HexToInt(int h);|将十六进制的单个字节转换为整数
|void *sqlite3HexToBlob(sqlite3 *db, const char *z, int n);|将形式为“ x'hhhhhh'”的BLOB文字转换为其二进制值
|static void logBadConnection(const char *zType);|记录一个连接错误
|int sqlite3SafetyCheckOk(sqlite3 *db);|检查以确保我们具有有效的数据库指针
|int sqlite3SafetyCheckSickOrOk(sqlite3 *db);|确保数据库指针可以有效使用

# 总结
`util.c`包含了字符串到数字的转换，db指针的有效性验证，还有内存的读写，简而言之就是一个内部基础库。