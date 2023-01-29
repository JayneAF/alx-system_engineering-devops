## Signature.key
https://dev.mysql.com/doc/refman/5.7/en/checking-gpg-signature.html


## Create New Users
https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql

## Replicate
https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql

## Create Databases and Tables
https://www.cyberciti.biz/faq/howto-linux-unix-creating-database-and-table/

### The above Links are perfect to complete the  ALX projects


# Further reading and solutions

## Redundancy Plan To Ensure High Availability
https://www.digitalocean.com/community/tutorials/how-to-choose-a-redundancy-plan-to-ensure-high-availability#sql-replication

## How do I uninstall MySQL completely?
https://askubuntu.com/questions/640899/how-do-i-uninstall-mysql-completely

## Some MySQL slave errors?
https://dba.stackexchange.com/questions/23921/some-mysql-slave-errors

## Setup a Primary-Replica infrastructure using MySQL
https://medium.com/@estebandelahoz/setup-a-primary-replica-infrastructure-using-mysql-5bcab77c352

## Remove Database
https://www.google.com/search?q=remove+database+mysql&rlz=1C1CHBF_enNG998NG998&oq=remove+dat&aqs=chrome.2.69i57j0i512j0i20i263i512j0i512l3j69i60l2.6139j0j7&sourceid=chrome&ie=UTF-8

## How to SHOW USERS in MySQL and User Information Using Linux
https://www.hostinger.com/tutorials/mysql-show-users/#:~:text=2.-,Use%20the%20MySQL%20SHOW%20USERS%20Query,have%20been%20created%20in%20MySQL.

## mysql: Show GRANTs for all users
https://dba.stackexchange.com/questions/23265/mysql-show-grants-for-all-users

# MySQL

This project contains tasks for learning how to configure MySQL for production.

## Tasks To Complete

+ [x] 0. Install MySQL<br/>
  + Install MySQL on your web-01 and web-02 servers.
  + The MySQL distribution must be 5.7.x.
  + Make sure that task #3 of your [SSH project](../0x0B-ssh/README.md) is completed for `web-01` and `web-02`. The checker will connect to your servers to check MySQL status.

+ [x] 1. Let us in!<br/>
  + Create a MySQL user named `holberton_user` on both `web-01` and `web-02` with the host name set to `localhost` and the password `projectcorrection280hbtn`. This will allow us to access the replication status on both servers.
  + Make sure that `holberton_user` has permission to check the primary/replica status of your databases.

+ [x] 2. If only you could see what I've seen with your eyes<br/>
  + Create a database named `tyrell_corp`.
  + Within the `tyrell_corp` database create a table named `nexus6` and add at least one entry to it. This is needed for you to set up replication.
  + Make sure that `holberton_user` has `SELECT` permissions on your table so that we can check that the table exists and is not empty.

+ [x] 3. Quite an experience to live in fear, isn't it?<br/>
  + The name of the new user should be `replica_user`, with the host name set to `%`, and can have whatever password you’d like.
  + `replica_user` must have the appropriate permissions to replicate your primary MySQL server.
  + `holberton_user` will need SELECT privileges on the `mysql.user` table in order to check that `replica_user` was created with the correct permissions.

+ [x] 4. Setup a Primary-Replica infrastructure using MySQL<br/>
  + MySQL primary must be hosted on `web-01` - do not use the `bind-address`, just comment out this parameter
  + MySQL replica must be hosted on `web-02`.
  + Setup replication for the MySQL database named `tyrell_corp`.
  + [4-mysql_configuration_primary](4-mysql_configuration_primary) should contain your MySQL primary configuration file (`my.cnf` or `mysqld.cnf`).
  + [4-mysql_configuration_replica](4-mysql_configuration_replica) should contain your MySQL replica configuration file.
  + Once MySQL replication is setup, add a new record in your table via MySQL on web-01 and check if the record has been replicated in MySQL web-02. If you see it, it means your replication is working!
  + Make sure that `UFW` is allowing connections on port `3306` (default MySQL port) otherwise replication will not work.

+ [x] 5. MySQL backup<br/>_**[5-mysql_backup](5-mysql_backup)**_ contains a Bash script that generates a MySQL dump and creates a compressed archive out of it.
  + Requirements:
    + The MySQL dump must contain all your MySQL databases.
    + The MySQL dump must be named `backup.sql`.
    + The MySQL dump file has to be compressed to a `tar.gz` archive.
    + This archive must have the following name format: `day-month-year.tar.gz.`
    + The user to connect to the MySQL database must be `root`.
    + The Bash script accepts one argument that is the password used to connect to the MySQL database.
