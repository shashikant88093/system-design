# Key Terms

> Load Balancer

  A type of **reverse proxy** that distributes traffic across servers. Load balancers can be found in many parts of a system, from the DNS layer all the way to the database layer

> Server-Selection Strategy 

  How a **load balancer** chooses servers when distributing traffic amongst multiple server. Commonly used strategies include round-robin, random selection, performance-based selection (choosing the server with the best performance metric, like the fastest response time or the least amount of traffic), and IP-based routing.

> Hot Spot 

  When distributing a workload across a set of servers, that workload might be spread unevenly. This can happen if your **sharding key** or your **hashing function** are suboptimal, or if your workload is naturally skewed: some servers will receive a lot more traffic than other, thus creating a "hot spot".

> Nginx 

  Pronounced "engine X" --not "N jinx", Nginx is very popular webserver that's often used as a **reversed proxy** and **load balancer**.


 [!Ngix](https://www.f5.com/go/product/welcome-to-nginx)