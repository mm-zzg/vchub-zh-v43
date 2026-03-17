# 支持的数据类型

SQL Query对于每个数据库，仅支持操作以下数据类型。

## SQLite

| 数据类型| 描述                         |
|:--------------|:----------------------------------|
| INTEGER      | 整数类型                         |
| NUMERIC      | 通用类型，可以为整数、浮点数或日期 |
| REAL         | 浮点数类型                       |
| TEXT         | 文本数据类型                     |

## MySQL

| 数据类型       | 描述               |
|:--------------------|:------------------------|
| BIGINT             | 大整数类型             |
| BIGINT UNSIGNED    | 无符号大整数类型       |
| BIT                | 位类型                 |
| BOOL               | 布尔类型               |
| CHAR               | 定长字符类型           |
| DATE               | 日期类型               |
| DATETIME           | 日期时间类型           |
| DECIMAL            | 精确小数类型           |
| DOUBLE             | 双精度浮动类型         |
| DOUBLE PRECISION   | 双精度浮动类型         |
| ENUM               | 枚举类型               |
| FLOAT              | 单精度浮动类型         |
| INT                | 整数类型               |
| INT UNSIGNED       | 无符号整数类型         |
| INTEGER            | 整数类型               |
| INTEGER UNSIGNED   | 无符号整数类型         |
| LONG VARCHAR       | 长文本类型             |
| LONGTEXT           | 长文本类型             |
| MEDIUMINT          | 中等范围整数类型       |
| MEDIUMINT UNSIGNED | 无符号中等范围整数类型 |
| MEDIUMTEXT         | 中等长度文本类型       |
| NUMERIC            | 精确小数类型           |
| REAL               | 单精度浮动类型         |
| SET                | 集合类型               |
| SMALLINT           | 小整数类型             |
| SMALLINT UNSIGNED  | 无符号小整数类型       |
| TEXT               | 可变长度文本类型       |
| TIME               | 时间类型               |
| TIMESTAMP          | 时间戳类型             |
| TINYINT            | 小整数类型             |
| TINYINT UNSIGNED   | 无符号小整数类型       |
| TINYTEXT           | 短文本类型             |
| VARCHAR            | 可变长度字符串类型     |
| YEAR               | 年份类型               |
| JSON               | JSON  数据类型         |

## SQL Server

| 数据类型     | 描述                    |
|:------------------|:-----------------------------|
| bigint           | 大整数类型                  |
| bit              | 位类型                      |
| char             | 定长字符类型                |
| date             | 日期类型                    |
| datetime         | 日期时间类型                |
| datetime2        | 精确日期时间类型            |
| datetimeoffset   | 日期时间类型                |
| decimal          | 精确小数类型                |
| float            | 双精度浮动类型              |
| int              | 整数类型                    |
| money            | 货币类型                    |
| nchar            | 定长 Unicode  字符类型      |
| ntext            | 大型  Unicode  文本类型     |
| numeric          | 精确小数类型                |
| nvarchar         | 可变长度  Unicode  字符类型 |
| real             | 单精度浮动类型              |
| smalldatetime    | 日期时间类型                |
| smallint         | 小整数类型                  |
| smallmoney       | 小范围货币类型              |
| sql_variant      | 通用数据类型                |
| sysname          | 系统对象名称类型            |
| text             | 大型  ASCII  文本类型       |
| time             | 时间类型                    |
| tinyint          | 小整数类型                  |
| uniqueidentifier | 全局唯一标识符（ GUID ）      |
| varchar          | 可变长度 ASCII 字符类型     |
| xml              | XML 类型                    |

## PostgreSQL

| 数据类型                                 | 描述                    |
|:-----------------------------------------------|:-----------------------------|
| bigint                                        | 大整数类型                  |
| bigserial                                     | 自增大整数类型              |
| boolean                                       | 布尔类型                    |
| character [ (***n*** ) ]                      | 定长字符类型                |
| character varying [ (***n*** ) ]              | 可变长度字符类型            |
| date                                          | 日期类型                    |
| double precision                              | 双精度浮点类型              |
| integer                                       | 整数类型                    |
| json                                          | JSON 类型                   |
| jsonb                                         | 二进制  JSON  类型          |
| numeric [ (p, s) ]                            | 精确小数类型                |
| real                                          | 单精度浮点类型              |
| smallint                                      | 小整数类型                  |
| smallserial                                   | 自增小整数类型              |
| serial                                        | 自增整数类型                |
| text                                          | 文本类型                    |
| time [ (***p*** ) ] [ without time zone ]     | 时间类型，不包含时区信息     |
| timestamp [ (***p*** ) ] [ without time zone] | 日期时间类型，不包含时区信息 |
| timestamp [ (***p*** ) ] with time zone       | 日期时间类型，包含时区信息   |
| uuid                                          | 通用唯一标识符（ UUID ）类型  |
| xml                                           | XML  类型                   |

## InfluxDB

支持所有类型的数据。