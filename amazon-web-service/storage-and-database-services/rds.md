# RDS

RDS is a fully managed Relational Database Service: 

* Does not allow access to the underlying operating system \(fully-managed\) 
* You connect to the RDS database server in the same way you would connect to a traditional on-premises database instance \(i.e., MySQL command line\) 
* RDS has the ability to provision/resize hardware on demand for scaling 
* You can enable Multi-AZ deployments for backup and high available solutions 
* Utilize Read Replicas \(MySQL/PostgreSQL/Aurora\) - to help offload hits on your primary database 
* Relational databases are databases that organize stored data into tables 
* The associated tables have defined relationships between them

Databases Supported By RDS: 

* MySQL 
* MariaDB 
* PostgreSQL 
* Oracle 
* MS SQL Server 
* Aurora: 
  * Is a home grown Relational Database that has been forked from, and fully compatible with MySQL 
  * It has fives times better performance then MySQL. and a lower price point than commercial databases

Benefits of running RDS instead of a database on your own instance: 

* Automatic minor updates 
* Automatic backups \(point-in-time snapshots\) 
* Not required to manage an operating system 
* Multi-AZ with a single click 
* Automatic recovery in event of a failover

