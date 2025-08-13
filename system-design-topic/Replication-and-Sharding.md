# Key Terms

 > Replication 
  
   The act of duplicating that data from one database server to others. This is sometimes used to increase the redundancy of your system and tolerate regional failures for instance. Other time you can use replication to move data closer to your clients, thus decreasing the latency if accessing specific data.

> Sharding

  Sometimes called ***data partitioning***, sharding is the act of splitting a database into two or more pieces called ***shards*** and is typically done to increase the throughput of your database. Popular sharding strategies includes:

   - Sharding based on a client's region
   - Sharding based on the type of data being stored (e.g user data gets stored in one shard, payment data gets stored in another shard)
   - Sharding based on the hash of a column(only for structured data).
  
> Hot Spot 

  When distributing a workload a set of servers, that workload might be spread unevenly. This can happen if your ***sharding Key*** or your ***hashing function*** are suboptimal, or if your workload is naturally skewed: some servers will receive a lot more traffic than others, thus creatiing a "hot spot".