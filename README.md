# LabLune Database

## Description

This project is a technical describe for install and explain a database of LabLune project.

## DBMS

MariaDB version 10.11.11

## Server

Linux Debian 12 on Hetzner provider (ip: 157.180.75.132)

## Install

```bash
sudo apt update
sudo apt upgrade
sudo apt install mariadb-server
```

## Configuration

Modify MariaDB configuration file and replace `bind-address = 127.0.0.1` by `bind-address = 0.0.0.0`

```bash
view /etc/mysql/mariadb.conf.d/50-server.cnf
```

Restart MariaDB service

```bash
systemctl restart mariadb
```

Connect to MariaDB

```bash
mariadb
```

Execute SQL

```sql
CREATE USER 'projetbts'@'%' IDENTIFIED BY 'MotDePasseComplexe123';
GRANT USAGE, SHOW DATABASES ON *.* TO 'projetbts'@'%';
```

```sql
CREATE DATABASE `lune_db`;
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, REFERENCES, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES, EXECUTE, CREATE VIEW, SHOW VIEW, CREATE ROUTINE, ALTER ROUTINE, TRIGGER ON `lune_db`.* TO `projetbts`@`%` WITH GRANT OPTION;
SHOW GRANTS FOR 'projetbts'@'%';
```

## Parameter

For use this database in your project you must configure with:

username: `projetbts`

password: `MotDePasseComplexe123`

host: `157.180.75.132`
