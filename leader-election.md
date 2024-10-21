# Key Terms

> Leader Election 
 
  The process by which nodes in a cluster(for instance, server in a set of servers) elect a so-called "leader" amongest them, responsible for the primary operations of the service that these nodes support. When correctly implemented, leader election guarantees that all nodes in the cluster know which one is the leader at any given time and can elect a new leader if the leader dies for whatever reason.

> Consensus Algorithm 

  A type of complex algorithm used to have multiple entities agree on a single data value, like who the "leader" is amongst a group of machines. Two popular consensus algorithms are ***Paxos*** and ***Raft***.

> Paxos & Raft

  Two consensus algorithms that, when implemented correctly, allow for the synchronization of certain operations, even in a distributed setting.

> Etcd
  
  Etcd is a strongly consistent and highly available key-value store that's often used to implement leader election in asystem.

> Zookeeper 

  Zookeeper is a strongly consistent, highly available key-value store. It's often used to store important configuration or to perform leader election.