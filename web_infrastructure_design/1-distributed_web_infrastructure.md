# Additional Servers:

Adding two additional servers helps distribute the load and improve the system's resilience. If one server goes down, the others can continue to handle requests, ensuring the site's availability. This reduces the risk of a single point of failure (SPOF).

# Load Balancing (HAProxy):

Adding HAProxy as a load balancer allows traffic to be distributed across multiple servers. This improves traffic management and prevents a single server from becoming overloaded. Load balancing also provides better fault tolerance.

# Web Server (Nginx):

Nginx is used as a web server to handle HTTP requests from users. It serves static files directly (images, CSS, etc.) and redirects dynamic requests to the application server.

# Application Server:

The application server is responsible for executing the logic of the application. It receives requests processed by Nginx, interacts with the database if necessary, and generates dynamic responses to be returned to Nginx, which then serves them to the user.

# MySQL Database:

MySQL is used to store the structured data of the application. The application server connects to it to read or write the necessary information (users, products, etc.).

# Load Balancer Distribution Algorithm:

The load balancing algorithm used by HAProxy can be:

- **Round Robin**: This algorithm distributes requests in a circular and equal manner among the available servers. It is simple and ensures that each server receives roughly the same number of requests.

- **Least Connections**: This algorithm sends requests to the server with the fewest active connections. It is useful when requests vary in processing time.

# Active-Active or Active-Passive Configuration:

- **Active-Active**: In this configuration, multiple servers are active simultaneously, sharing the workload. This allows for better resource utilization and ensures high availability.

- **Active-Passive**: In this configuration, one server is active and handles all traffic, while the other is on standby (passive). If the active server goes down, the passive one takes over. This guarantees availability but does not use both servers simultaneously.

# Primary-Replica (Master-Slave) Database Cluster:

A Primary-Replica (or Master-Slave) cluster allows data to be replicated across multiple database servers.

- **Primary Node (or Master)**: This is the main node where all write operations (INSERT, UPDATE, DELETE) are performed. It is responsible for data modifications.

- **Replica Node (or Slave)**: The Replica node receives copies of the data from the Primary and is mainly used for reading operations (SELECT). This reduces the read load on the Primary and improves overall performance.

# Difference Between Primary and Replica Node:

- **Primary Node**: Handles all write operations.
- **Replica Node**: Primarily handles read operations to offload the Primary. The application interacts with the Primary for data modifications and can interact with the Replicas for read-intensive queries.

# Potential Issues with This Infrastructure:

## Single Points of Failure (SPOF):

- The HAProxy load balancer can become a SPOF. If HAProxy goes down, access to the site will be impossible, even if the other servers are functioning. A solution would be to configure a second HAProxy for redundancy.

## Security Issues:

- **No Firewall**: Without a firewall, the infrastructure is vulnerable to network attacks.
- **No HTTPS**: If traffic is not encrypted with HTTPS, data exchanged between the server and the user (such as passwords) can be intercepted by attackers.

## Lack of Monitoring:

- Without a monitoring system, it is difficult to detect real-time performance issues, failures, or security threats. Monitoring is essential to ensure the availability and security of the infrastructure.
