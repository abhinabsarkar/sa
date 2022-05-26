# Database - Technical interview questions & answers

1. Describe database normalization -  Normalization rules divides larger tables into smaller tables and links them using relationships. Database normalization is the process of structuring a relational database in accordance with a series of so-called normal forms in order to reduce data redundancy and improve data integrity. [Explanation](https://www.guru99.com/database-normalization.html)
    * 1NF - Each record needs to be unique (Primary key)
    * 2NF - Be in 1NF. Primary & Foreign key relationship to establish referential integrity
    * 3NF - Be in 2NF. Have no transitive functional dependencies i.e. when changing a non-key column, might cause any of the other non-key columns to change

2. what is RAID (Redundant Array of Independent Disks). what is RAID-10. what are other types of RAID - data storage virtualization technology that combines multiple physical disk drive components into one or more logical units for the purposes of data redundancy, performance improvement, or both [Video Explanation - RAID 0, 1, 5, 10](https://www.youtube.com/watch?v=U-OCdTeZLac)
    * Data "stripe" - segmenting logically sequential data, such as a file, so that consecutive segments are stored on different physical storage devices

* Which RAID would a DB use? RAID 10 for redundancy and performance, for databases like SQL Server, MongoDB and MySQL. For distributed databases like Cassandra, it is not the best decision to use RAID unless you have a small cluster. [RAID storage for Databases](https://www.xenonstack.com/blog/raid-storage-databases)

* Parity - Parity is a fault tolerance technique used in RAID drive arrays  by calculating the data in two drives and storing the results on a third. After a failed drive is replaced, the RAID controller rebuilds the lost data from the other two drives. [RAID 5, 6 & Parity](https://youtu.be/UuUgfCvt9-Q?t=21). 

    To explain how it does this, think back to high school algebra class, with equations like “9 = X + 4. Solve for X”. In this case, “X” is unknown data that was previously stored on a drive that has failed. “4” meanwhile, is data that is stored on a drive you can read, and “9” is parity data stored on a third drive, that was previously calculated for redundancy purposes. By solving for X, we can re-construct that the missing data should have been “5”. This allows you to have redundancy without storing a full extra copy of your data, saving disk space compared to RAID 1 or RAID 10. [RAID parity explained](https://ioflood.com/blog/2016/02/26/what-is-raid-5-raid-parity-explained/)

3. how do you design a clustered database environment? what's a hot standby? describe failover - [Explanation](https://docs.oracle.com/cd/B28359_01/server.111/b28281/architectures.htm#CIHCECGE)
* DB clustering - a collection of two or more servers (nodes) connected on a network, each of which host a DB server instance and have the same access to shared storage. Clustering provides high availability if a server hosting the DB instance fails. If you are on a standalone server, a hardware failure can bring your operations to a halt. However, with clustering, if a node has problems, you can automatically failover to another node.

    ![Alt text](/images/highava-sqlcluster.gif)

* The shared storage itself is made HA by having it replicated or mirrored to another storage instance.

    ![Alt text](/images/Oracle_RAC_Extended_cluster.jpg)

4. Replication vs mirroring - [Explanation](https://techdifferences.com/difference-between-mirroring-and-replication.html)
* DBM - Database is Mirrored (Also known as <ins>**Shadowing**</ins>) i.e. copy a database to another location / server. 
* DR - Data is Replicated i.e. data & database objects are copied to another database.  
    * **Snapshot replication** copies the data and database objects same as they appear in an instant. Snapshot replication is the ideal replication method under any of the following conditions:
      * When data changes infrequently
      * When the publisher and subscriber are not required to be in sync at all times
      * When data changes are large but occur over a short period of time
    * **Transactional replication** starts with a snapshot of the database objects and data. Subsequent data changes and schema modifications made at the Publisher are usually delivered to the Subscriber as they occur (in near real time).
      * For example, a customer’s account balance in a commercial bank’s publisher database initially reads $2,000. Then, within the span of a few minutes, the customer deposits $500 and then withdraws $1000 from the ATM. The net effect is $2000+$500-$1000=$1500. However, a transactional replication does not simply update the subscriber client account as $1500. Each of these two transactions also must be written to the subscriber.
    * **Merge replication** starts with a snapshot of the database objects and data. Subsequent changes and schema modifications made at the Publisher and Subscribers are tracked with triggers. The Subscriber synchronizes with the Publisher when connected to the network since the last time synchronization occurred.

5. Describe tools for data replication? - These tools support active-passive data replications as well as active-active replication mode. Data Guard supports active-passive replication. One of the database is the primary database and the other one is in an inactive Data Guard mode. GoldenGate supports an active-active replication mode and allows both systems to work simultaneously while maintaining the data integrity. E.g. Oracle Dataguard & Oracle Golden Gate. [Explanation](https://oracledbwr.com/oracle-goldengate-vs-oracle-data-guard/)

6. NAS (Network Attached Storage) vs SAN (Storage Area Network) vs DAS (Direct Access Storage) - Big enterprises will generally have SAN storage as it offers higher performance, scalability at the same time costs more. Storage Area Networks (SAN) storage solution is the ability to share the storage arrays to multiple servers. Higher levels of performance throughput are typical in a SAN environment, and data is highly available through redundant disk controllers and drives.  [Simple video explanation](https://www.youtube.com/watch?v=bpUzGZLO948) [Video explanation](https://www.youtube.com/watch?v=3yZDDr0JKVc&feature=youtu.be&t=27) 
   * [DAS](https://www.purestorage.com/knowledge/what-is-direct-attached-storage.html)
   * NAS - Shared storage over a shared network. Data is stored as File Storage. 
   * SAN - Shared storage over a dedicated network. Data is stores as block storage. Highly scalable, redundant (network as well as storage), fast as well as expensive

7. File Storage vs Block storage vs Object Storage - File storage stores data in hierarchical structure in folders and files e.g NAS. Block storage e.g SAN stores data in chunks i.e. blocks of size say 4KB which can be stored in a distributed manner. The data when has to be retrieved is re-assembled by the underlying software using the Id. Object storage e.g. Azure Blob Storage is stored in a object which comprises of Id, metadata & blob (unstructured data). To retrieve the data, the storage operating system uses the metadata and identifiers, which distributes the load better. The object storage is accessed using REST API. [Explanation](https://www.redhat.com/en/topics/data-storage/file-block-object-storage). [Video - Block vs File Storage](https://youtu.be/5EqAXnNm0FE?t=16) & [Detailed video](https://www.youtube.com/watch?v=3r9RGJ0_Bls)

|  | File Storage | Block Storage | Object Storage |
| ------------ | ------------ | ------------- | -------------- |
| Definition |	Stores data in hierarchical structure in folders (root, sub folder) and files e.g NAS |	Stores data in chunks i.e. blocks (of size say 4KB) e.g. SAN | 	Stored data in a object which comprises of Id, metadata & blob (unstructured data) e.g. Azure Blob storage |
| Data type	| Mix of Structured, Unstructured |	Structured	Unstructured |
| Data access |	Data is accessed using path |	The data when has to be retrieved is re-assembled by the underlying software using its unique Id |	To retrieve the data, the storage operating system uses the metadata and identifiers, which distributes the load better |
| Protocol	| NFS (Unix/Linux), CIFS (Windows), SMB	| FC (Fibre Channel), iSCSI(Internet Small Computer System Interface) |	HTTP REST APIs |
| Biggest strength	| Simplified access & management |	High Performance |	Scalability & distributed access |
| Best suited for |	Text files, Shared data space for users like NAS |	Transactional data like Database, Disks for VMs | 	Video, log files, Images |
| Cost | In-between object & block storage |	Expensive	| Cheapest |

8. How to scale an write DB? To scale database writes, scale up as much as you can "afford" and then scale out. [OLTP write scaling blog - Oracle](https://blogs.oracle.com/database/post/oltp-write-scaling-is-hard)

    ![Alt text](/images/scale-write-heavy-oltp-db.png)

    Developing applications for a sharded database [eg manually sharded MySQL or PostgreSQL] is difficult. You need to have custom code to route reads and writes to the correct shard. Usually doing complex queries that span database shards is either difficult or not allowed. Unless you have expert DBAs and developers who know all of the ins and outs of designing, developing, operating and maintaining a sharded database system, do not consider this approach. You can use products like "Oracle TimesTen Scaleout" database to simplify the sharding approach.

* What is a database index? A database index is a <ins>data structure</ins> that improves the speed of data retrieval operations on a database table at the cost of additional writes and storage space to maintain the index data structure. Indexes are used to <ins>quickly locate data without having to search every row in a database table</ins> every time a database table is accessed. Indexes can be created using one or more columns of a database table.
    * How indexes work?
        * Clustered index is a sorted table using a column in the DB. There can be only one clustered index per table because the data rows themselves can be stored in only one order. Primary key by default is a clustered index.
        * Non-clustered index - it contains reference or pointer to the row. Unique key by default would be an example of non-clustered index. (unique key can have null)
    * Drawback - An index is pure redundancy. It contains only data that is also stored in the table. During write operations, the database must keep those redundancies consistent. Specifically, it means that insert, delete and update not only affect the table but also the indexes that hold a copy of the affected data.
