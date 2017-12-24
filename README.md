# dash docset generation


## 环境准备

1. sqlite3安装

```bash
brew install sqlite3
```

2. 在对应的目录创建数据库

```
sqlite3 docSet.dsidx
```

3. 创建默认表

```sql
CREATE TABLE searchIndex(id INTEGER PRIMARY KEY, name TEXT, type TEXT, path TEXT);
```

4. 创建SQL添加数据

> 以此文档集为例

* 中文入门指南
* 中文api
* 中文模板语法
* regularjs

```
INSERT OR IGNORE INTO searchIndex(name, type, path) VALUES ('guide', 'Guide', './guide/zh/index.html');
INSERT OR IGNORE INTO searchIndex(name, type, path) VALUES ('syntax', 'Guide', './guide/zh/index.html');
INSERT OR IGNORE INTO searchIndex(name, type, path) VALUES ('api', 'Guide', './api/index.html?api-zh');
INSERT OR IGNORE INTO searchIndex(name, type, path) VALUES ('regularjs', 'Guide','https://github.com/regularjs');
```

> 注: [详细参考](https://kapeli.com/docsets)

## FAQ

1. 清空sqlite3数据

```sql
DELETE FROM searchIndex
```

2. 登录指定数据库

```
sqlite3 docSet.dsidx
```

3. 退出数据库

```sql
.exit
```

## 感谢

- [dash](https://kapeli.com/dash)
- [regular guide](https://github.com/regularjs/guide)
- [regular api](https://github.com/regularjs/blog)