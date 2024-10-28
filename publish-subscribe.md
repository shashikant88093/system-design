# Prerequisites

> Polling 

  The act of fetching a resource or piece of data regularly at an interval to make sure your data is not too stale.

> Streaming 
  
  In networking, it usually refers to the act of continuously getting a feed of information from a server by keeping an open connection between the two machines or processes.

> Persistent Storage

  Usually refers to disk, but in general it is any form of storage that persists if the process in charge of managing it dies.

# Key Terms

> Publish/Subscribe Pattern

  Often shortened as ***Pub/Sub***, the publish/Subcribe pattern is a popular messaging model that consists of ***Publishers*** and ***Subcribers***. Publishers publish message to special ***topics*** ( sometimes called ***Channels***) without caring about or even knowing who will read those messages, and subscribe to topics and read messages coming through those topics.

  Pub/Sub systems often come with very powerful guarantees like ***at-least-once delivery , persistent storage, ordering*** of messages, and ***replayability*** of messages.

> Idempotent Operation 

  An Operation that has the same ultimate outcome regardless of how many times it's performed. If an operation can be performed multiple times without changing its overall effect, it's idompotent. Operations performed through a ***Pub/Sub*** messaging system typically have to be idempotent, since Pub/Sub systems tend to allow the same message to be consumed multiple times.

  For example, increasing an integer value in a database is not an idempotation operation, since repeating this operations will have the same effect as if it had been performed only once. Conversely, setting a value to "Complete" is an idempotent operation, since repeating will always yield the same result: the value will be "Complete".

> Apache Kafka

  A distributed messaging system created by LinkedIn. Very Useful When using the ***Streaming*** paradigm as opposed to ***polling***.

> Cloud Pub/Sub

  A highly-scalabe Pub/Sub messaging service created by Google. Guarantees ***at-least-once delivery*** of messages and supports "rewinding" in order to reprocess messages.  