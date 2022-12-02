---
title: '[SQL] Trigger를 활용하여 테이블 변화 Noti 보내기'
author: SongEun
date: 2022-11-28 12:00:00 +0000
categories: [Dev]
tags: [SQL, PostgreSQL, Trigger, Notification, Listen]
math: true
mermaid: true
---



### "NEW" and "OLD"
#### NEW
- Format : NEW.[column name] 
- column value of new/updated records

#### OLD
- Format : OLD.[column name] 
- previous column value before insert or update


## How to list trigger on a table

### Using psql
To list down triggers on a specific table using psql command-line, you can use the following command : 

```
\dS [table name]. 
```

## How to list function

```
\df
```

## How to drop function

```
DROP FUNCTION [function name];
```


# server-side SQL 

1. Declare Function
```
CREATE OR REPLACE FUNCTION notify_update()
returns trigger
AS $$
DECLARE
BEGIN
    NOTIFY NE_watcher;
    return NULL;
END; $$
LANGUAGE 'plpgsql';
```

2. Create Trigger
```
CREATE TRIGGER notify_update
         AFTER INSERT OR UPDATE OR DELETE
            ON nlu_dict_ne_common_regular
      FOR EACH ROW
      EXECUTE PROCEDURE notify_update();
```

<br>

___

## Reference

### PostgreSQL Notification and Listen
+ [https://www.postgresql.org/docs/12/sql-notify.html](https://www.>postgresql.org/docs/12/sql-notify.html)
+ [https://postgresql.kr/blog/pg_listen_notify.html](https://postgresql.kr/blog/pg_listen_notify.html)
+ [https://tapoueh.org/blog/2018/07/postgresql-listen-notify/](https://tapoueh.org/blog/2018/07/postgresql-listen-notify/)

### Trigger
+ [https://www.postgresql.org/docs/current/sql-createtrigger.html](https://www.postgresql.org/docs/current/sql-createtrigger.html)
+ [https://jaeone94.github.io/posts/Postgresql-%ED%8A%B8%EB%A6%AC%EA%B1%B0%EB%A5%BC-%EB%B0%B0%EC%9B%8C%EB%B3%B4%EC%9E%90/](https://jaeone94.github.io/posts/Postgresql-%ED%8A%B8%EB%A6%AC%EA%B1%B0%EB%A5%BC-%EB%B0%B0%EC%9B%8C%EB%B3%B4%EC%9E%90/)

### Trigger examples
+ [https://daspace.tistory.com/87](https://daspace.tistory.com/87)
+ [https://thinking-jmini.tistory.com/21](https://thinking-jmini.tistory.com/21)
+ [https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=chas0302&logNo=221890879467](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=chas0302&logNo=221890879467)

