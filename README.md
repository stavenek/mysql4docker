mysql4docker
============

Dockerfile to create a MySQL4 environment for legacy testing purposes

Usage
=====

Specify the MYSQL_ROOT_PASSWORD environment variable when launching a new container, e.g:

<pre><code>docker run -d -P -e "MYSQL_ROOT_PASSWORD=password" stevemayne/mysql4</code></pre>

Root user will be bound to the wildcard % host to allow login from outside the container.

Some more logs about how to start and init...
<pre>
docker build -t pp/mysql4:0.1 .
docker run --name db -p 6603:3306 -e MYSQL_ROOT_PASSWORD=root -d pp/mysql4:0.1

#setup db
mysql -uroot -proot -P6603 -h192.168.99.100 < create_rom_db.sql
mysql -uroot -proot -P6603 -h192.168.99.100 -Drom < rom-2016-04-16.sql

#connect
mysql -uroot -proot -P6603 -h192.168.99.100 -Drom
</pre>
