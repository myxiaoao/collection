# Where
Collection 和 Laravel 本身的 ORM 系统 Eloquent 密不可分，因此也配合许多 where 语法，可以仿造 SQL 的方式操作。

> 假定大家都了解 Eloquent 哦。

## 1. firstWhere()
可以在用 where 条件匹配到数据后，只返回第一条。

## 2. where() , whereStrict()
没错，where 也支持严格模式操作。

## 3. whereBetween , whereIn , whereNull , whereNotIn, whereNotInStrict , whereNotNull
常见的 where 语法，In 同时也支持严格模式，基本上都支持 Not 否定判断模式。

## 4. whereInstanceOf
可以判断是否包含特定数据。
