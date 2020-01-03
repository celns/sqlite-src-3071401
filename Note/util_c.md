# util.c
基础通用工具(Utilities)函数或方法库
|函数定义|说明|
|:----:|:----:|
|int sqlite3Strlen30(const char *z);|计算字符串长度,最长30位
|void sqlite3Error(sqlite3 *db, int err_code, const char *zFormat, ...);|处理“db”错误代码“err_code”
|void sqlite3ErrorMsg(Parse *pParse, const char *zFormat, ...);|报告在运行过程中发生的任何错误
|int sqlite3Dequote(char *z)|转换SQL样式的带引号的字符串为普通字符串
|int sqlite3_stricmp(const char *zLeft, const char *zRight)|字符串比较
|int sqlite3AtoF(const char *z, double *pResult, int length, u8 enc)|将实数字符串转换为双精度浮点数
|