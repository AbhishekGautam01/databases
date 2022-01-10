# Sharding 
* It is one of **patterns used to scale RDBMS database**
* Process of breaking a table into smaller shards that are stored across multiple servers. 
* Horizontal data partition that contain **subset of data set** 
* It serves a part of overall workload. 
* The Idea is to distribute the data which cannot fit on a single node to multiple distributed nodes. 

## Benefits 
*	Business applications that rely on a monolithic RDBMS hit bottlenecks as they grow. With limited CPU, storage capacity, and memory, query throughput and response times are bound to suffer. When it comes to adding resources to support database operations, vertical scaling (aka scaling up) has its own set of limits and eventually reaches a point of diminishing returns.
* 	On the other hand, horizontally partitioning a table means more compute capacity to serve incoming queries, and therefore you end up with faster query response times and index builds. By continuously balancing the load and data set over additional nodes, sharding also enables usage of additional capacity. Moreover, a network of smaller, cheaper servers may be more cost effective in the long term than maintaining one big server.
*	It helps in downtime as when the node is down still other shards will be accessible.

# [Continue Here](https://blog.yugabyte.com/how-data-sharding-works-in-a-distributed-sql-database/#:~:text=Sharding%20is%20the%20process%20of,portion%20of%20the%20overall%20workload)