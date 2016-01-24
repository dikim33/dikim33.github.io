---
layout: blog-article
title: Getting started with MySQL
meta: A very fundamental process to start up mysql
source:
category: linux
folder: linux
---

  * Install MySQL. If necessary, install mysql-server.
  * Start MySQL (/etc/init.d/mysqld start)
  * Setup root password
      {% highlight bash %}
        shell> mysql -u root
        mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpwd‘);
        mysql> SET PASSWORD FOR 'root'@'host_name‘ = PASSWORD(’newpwd‘);
      {% endhighlight %}
  * Create a normal user
      {% highlight bash %}
        mysql> GRANT ALL PRIVILEGES ON *.* TO 'monty'@'localhost'
        ->     IDENTIFIED BY 'some_pass'
       {% endhighlight %}
  * Don't forget to flush privileges
      {% highlight bash %}
        mysql> FLUSH PRIVILEGES;
      {% endhighlight %}


