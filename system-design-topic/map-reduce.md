# Prerequisites

> File System

  An abstraction over a storage medium that defines how to manage data. While there exist many different types of file systems, most follow a hierarchical structure that consists of directories and files, like the ***Unix file system***'s structure.
> Idempotent Operation 

  An Operation that has the same ultimate outcome regardless of how many times it's performed. If an operation can be performed multiple times without changing its overall effect, it's idompotent. Operations performed through a ***Pub/Sub*** messaging system typically have to be idempotent, since Pub/Sub systems tend to allow the same message to be consumed multiple times.

  For example, increasing an integer value in a database is not an idempotation operation, since repeating this operations will have the same effect as if it had been performed only once. Conversely, setting a value to "Complete" is an idempotent operation, since repeating will always yield the same result: the value will be "Complete".

# Key Terms

> Map Reduce

  A Popular framework for processing very large datasets in a distributed setting efficiently, quickly, and in a fault-tolerant manner. A Map Reduce Job is comprised of 3 main steps:

  - The ***Map*** step, which runs a ***map function*** on the versions chunks of the dataset and transforms these chunks into intermediate ***Key-Values pairs***.
  - The ***Shuffle*** step, which reorganizes the intermediate ***key-value pairs*** such that pairs of the same key are routed to the same machine in the final step.
  - The ***Reduce*** step, which runs a ***reduce function*** on the newly shuffled ***key-value-pairs*** and transforms them into more meaningful data.
  
  The canonical example of a MapReduce use case in counting the number of occurrences of words in a large text file.

  when dealing with a MapReduce library, engineers and/or systems adminstators only need to worry about the map and reduce functions, as well as their inputs and output. All other concerns, including the parallelization of tasks and the fault-tolerance of the MapReduce job, are abstracted away and taken care of by the MapReduce Implementation.

# Distributed File System (DFS)

A Distributed File System (DFS) is a file system that allows access to files from multiple locations across a network. Unlike traditional file systems that operate on a single server, a DFS distributes files across multiple machines, improving storage efficiency, accessibility, and reliability.

## Key Concepts of Distributed File Systems

### 1. Data Distribution
- Files are split into chunks or blocks and distributed across various nodes (servers/computers) in the network.
- This setup ensures that the storage and retrieval load is shared among several machines, enhancing system scalability and efficiency.

### 2. Data Redundancy and Fault Tolerance
- Data is often duplicated across multiple nodes to ensure availability and fault tolerance.
- Redundancy allows recovery of files from other nodes in case one node fails, which is crucial for systems requiring high availability, such as cloud storage services or large-scale data centers.

### 3. Scalability
- DFS systems are designed to scale horizontally by adding more machines to the network as data volume increases.
- This approach manages growing storage demands without overloading a single server or creating a bottleneck.

### 4. Data Consistency
- Ensuring data consistency across distributed nodes is essential, especially when files are accessed and modified by multiple users.
- Consistency models used by DFS include:
  - **Strong Consistency**: Ensures immediate updates across nodes.
  - **Eventual Consistency**: Ensures updates propagate over time.

### 5. Parallelism
- DFS allows parallel access to data chunks, improving processing speeds for large-scale applications, such as machine learning or data analytics.
- Nodes can process different data chunks simultaneously, optimizing performance for intensive operations.

### 6. Network Transparency
- DFS abstracts the complexities of data location from users, creating a seamless experience as if files are on a single system, even though they’re distributed across several nodes.
- Users can interact with files without needing to know their actual location.

## Popular Distributed File Systems
- **HDFS (Hadoop Distributed File System)**: Used in big data applications, it splits files into large blocks and distributes them across nodes for fault tolerance and high throughput.
- **Google File System (GFS)**: Created by Google for scalable storage and retrieval across Google’s distributed infrastructure.
- **Ceph and GlusterFS**: Open-source distributed file systems often used for cloud storage and high-performance computing.

## Advantages of DFS
- **Fault Tolerance**: Data redundancy prevents data loss even in case of system failures.
- **High Availability and Scalability**: Suitable for large organizations with extensive data needs.
- **Improved Performance**: Parallelism and load balancing across nodes increase data retrieval speeds.

## Challenges of DFS
- **Data Consistency Management**: Maintaining data integrity across distributed nodes can be complex.
- **Network Latency**: High latency can occur when nodes are geographically distant.
- **System Complexity**: Managing distributed systems requires complex infrastructure and expertise.

---

In summary, a Distributed File System is a powerful tool for handling large-scale data storage and access needs, providing high availability, fault tolerance, and scalability.
