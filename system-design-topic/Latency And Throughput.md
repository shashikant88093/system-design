# Latency And Throughput

### Prerequisites

> Disk

 Usually , the disk is the slowest component in a system. The disk is responsible for storing and retrieving.
 refers to **HDD (hard-disk drive)** or **SSD (solid-state drive). Data written to disk will persist through
 power failures and general machine crashes. Disk is also referred to as **non-volatile storage**.

 SSD is far faster then **HDD** (see latencies of accessing data from SSD and HDD) but also far more expensive from a financial point of view. Because of that, **HDD** will typically be used for data that's rarely accessed or updated. but that's stored for a long time, and SSD will be used for data  that's frequently accessed or updated.


> Memory 
 
  Short for **Random Access Memory(RAM)**. Data  stored in memory will be <ins>lost</ins> when the process that has written that data dies

# Key Terms 

> Latency 
 
 The time it takes for a certain operation to complete in a system. Most often this measure is a time duration, like milliseconds or second. You should know these orders of magnitude:

 - **Reading 1 MB from RAM:** 250 µs (0.25 ms)
 - **Reading 1 MB from SSD:** 1,000 µs (1 ms)  **4 times then Ram**
 - **Transfer 1 MB over Network:** 10,000 µs (10 ms) **10 times then Network**
 - **Reading 1 MB from HDD:** 20,000 µs (20 ms)
 - **Inter-Continental Round Trip:** 150,000 µs (150 ms)

> Throughput 

  The number of operations that a system can handle properly per time unit. For instance the throughput of a server can often be measured in requests per second (RPS or QPS).