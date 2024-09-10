# Infrastructure Requirements and Explanations

## 1 Server:
- **Purpose**: Adding an additional server helps to separate the roles of components and improves resilience and load management.

## 1 Load Balancer (HAproxy):
- **Purpose**: Adding a load balancer HAproxy configured in a cluster with another load balancer improves traffic distribution and ensures high availability. If one load balancer fails, the other can take over, avoiding a single point of failure (SPOF).

## Separate Components (Web Server, Application Server, Database):
- **Purpose**: Deploying each component (web server, application server, database) on a separate server enhances performance and scalability. This separation allows for easier management and better resource allocation.

## Explanation of Added Elements:

- **Additional Server**: Adding a server allows for managing increased loads and separating different roles to prevent overloading a single server. This increases the flexibility and resilience of the system.

- **HAproxy Load Balancer in Cluster**: HAproxy in a cluster ensures even traffic distribution between servers and improves availability by avoiding SPOF. If one of the load balancers fails, the other continues to distribute traffic, ensuring service continuity.

- **Component Separation**: Deploying the web server, application server, and database on separate servers allows for better management of each part of the infrastructure. This enhances performance, maintenance, and scalability.
