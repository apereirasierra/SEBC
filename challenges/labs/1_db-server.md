command and output that shows the hostname of your database server
hostname ip-172-31-30-111.us-west-2.compute.internal

A command and output that reports the database server version
sudo cat /etc/cloudera-scm-server/db.properties
# Auto-generated by scm_prepare_database.sh on Fri Jul 21 10:25:37 EDT 2017
#
# For information describing how to configure the Cloudera Manager Server
# to connect to databases, see the "Cloudera Manager Installation Guide."
#
com.cloudera.cmf.db.type=mysql
com.cloudera.cmf.db.host=localhost
com.cloudera.cmf.db.name=cmdatabase
com.cloudera.cmf.db.user=root
com.cloudera.cmf.db.setupType=EXTERNAL
com.cloudera.cmf.db.password=**!

mysql --version
mysql  Ver 15.1 Distrib 5.5.52-MariaDB, for Linux (x86_64) using readline 5.1

A command and output that lists all the databases in the server
show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| scm                |
| cmdatabase         |
| hue                |
| mysql              |
| nav                |
| navms              |
| oozie              |
| performance_schema |
| rman               |
| hive               |
+--------------------+