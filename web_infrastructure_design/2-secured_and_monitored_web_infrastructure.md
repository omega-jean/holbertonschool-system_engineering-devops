# Web Infrastructure with Firewalls, SSL, and Monitoring

## Firewalls (3):

- **Why add them**: Firewalls protect each server from unauthorized attacks. They filter incoming and outgoing traffic based on security rules, blocking malicious access attempts.
- **Role of firewalls**: They limit access to necessary services only. For example, allowing only HTTP/HTTPS traffic for the web server and database traffic for authorized servers.

## SSL Certificate (1):

- **Why serve traffic over HTTPS**: HTTPS encrypts communications between the user and the server, preventing "man-in-the-middle" attacks and protecting sensitive information such as passwords and personal data.

## Monitoring Clients (3):

- **Why add them**: Monitoring allows you to quickly detect anomalies, outages, and performance issues. It provides real-time visibility into the state of the infrastructure.
- **Role of monitoring**: Monitoring tools collect data on server performance, load, resource usage, and trigger alerts in case of incidents. This data is sent to a platform like Sumologic.
- **Data collection**: Monitoring clients are installed on each server, collecting metrics like CPU usage, memory, and queries per second (QPS) on the web server.
- **Monitoring QPS on the web server**: Use monitoring tools to set an alert when the number of queries per second exceeds a critical threshold, allowing you to react before site performance is affected.

## Potential Issues with the Infrastructure:

### SSL Terminated at the Load Balancer:

- **Problem**: If SSL encryption is terminated at the load balancer, communication between the load balancer and backend servers is not encrypted, creating a vulnerability within your internal network. To fully secure the chain, it is recommended to use SSL between the load balancer and the servers.

### A Single MySQL Server Handling Writes:

- **Problem**: If only one instance of MySQL handles writes, it creates a single point of failure (SPOF). If this server goes down, no data can be written to the database, making the application partially or fully unusable. A better solution would be to implement a MySQL cluster with active-active or active-passive replication.

### Servers with All the Same Components:

- **Problem**: Having each server with the same components (database, web server, application server) can complicate management and lead to inefficiencies. It's better to separate roles across dedicated servers (e.g., one for the database, another for applications). This improves performance, maintenance, and scalability.
