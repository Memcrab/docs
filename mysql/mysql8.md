---
parent: MySQL
title: MySQL 8 migration issues
---

# MySQL 8 migration issues
{: .no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# PHP Cant connect to MySQL 8

Reasons can be like:

```terminal
Unexpected server response while doing caching_sha2 auth: 109
```
```terminal
mysqli_real_connect(): (HY000/2006): MySQL server has gone away
```
```terminal
SQLSTATE[HY000] [2054] The server requested authentication method unknown to the client
```

It comes with support for MySQL 8's new password authentication plugin: `caching_sha2_password`

The following errors might pop up if you have been using MySQL 8 with PHP 7.3 or older, and using `mysql_native_password` plugin to deal with PHP's then-lack of support for the new `caching_sha2_password` plugin.

## Solution 1: Upgrade PHP to 7.4 and upper

check your version of php `php -v` and upgrade it to 7.4 or upper. With the upgrade to 7.4, PHP natively supports the new default authentication plugin `caching_sha2_password`.

## Solution 2: Change Auth method to older one

1. Connect to the database as root
2. Check existing authentication plugin:
```sql
mysql> SELECT user,plugin from mysql.user;
```
Sample output
```sql
+------------------+-----------------------+
| user             | plugin                |
+------------------+-----------------------+
| Ayesh            | caching_sha2_password |
| debian-sys-maint | mysql_native_password |
| mysql.infoschema | caching_sha2_password |
| mysql.session    | mysql_native_password |
| mysql.sys        | caching_sha2_password |
| root             | auth_socket           |
| testuser         | mysql_native_password |
+------------------+-----------------------+
```
The easiest way to fix that would be to alter your existing user with the following:
```sql
mysql> ALTER USER myuser IDENTIFIED WITH mysql_native_password BY 'mypassword';
```
Another thing that you could do is to create a new user with mysql_native_password. To do that you could use the following:
```sql
mysql> CREATE USER 'your_user'@'your_server_ip ' IDENTIFIED WITH mysql_native_password BY 'your_password';
```