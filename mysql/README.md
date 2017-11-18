# MySQL and MariaDB Cheatsheet


## Create Database and User

```
# mysql -u root -p
```
```
CREATE DATABASE database_name;
```
```
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
```
```
GRANT ALL PRIVILEGES ON database_name.* TO 'newuser'@'localhost';
```
```
FLUSH PRIVILEGES;
```
```
quit
```


# Migrate MySQL DB to another server

```
mysqldump -u db_user -p some_database | gzip | ssh someuser@newserver 'gzip -d | mysql -u db_user --password=db_pass some_database'
```

- or instead of gzip you can use ssh with option `-C`
- you can create an error log: add `--log-error=error.log` to mysqldump command.


# Moving from MySQL to MariaDB

MariaDB is a drop in replacement for MySQL, using the same commands.

Replacing is 3 simple steps:

- Backup databases (just in case)
- Uninstall MySQL
- Install MariaDB

```
// uninstall MySQL:
    sudo apt-get purge mysql-server mysql-common mysql*
```
```
// cleanup:
    sudo apt-get autoclean; sudo apt-get clean; sudo apt-get autoremove; 
```
```
// check if you catched them all:
    dpkg -l | grep -i -e "sql\|maria" 
```
```
// install MariaDB:
    sudo apt-get install mariadb-server 
```
