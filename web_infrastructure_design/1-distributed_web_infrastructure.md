![Task 1 Diagram](https://github.com/sifir-gun/holbertonschool-system_engineering-devops/blob/main/web_infrastructure_design/diagram_task1.png)

	1.	Server #1:
		•	HAProxy (Load Balancer)
		•	Receives all inbound traffic for www.foobar.com.
	2.	Server #2:
		•	Nginx (Web Server)
		•	Application Server (running your code)
	3.	Server #3:
		•	MySQL Database (could be a standalone DB or the Primary node in a Master-Slave setup)

Why We Add These Components
	1.	Load Balancer (HAProxy)
		•	Purpose: Distribute incoming traffic among multiple servers (in larger setups) or at least decouple the “public entry point” from the web/application layer.
		•	Provides flexibility to add more servers behind it later for scalability and redundancy.
	2.	Dedicated Web/Application Server
		•	Having Nginx + the application code on a separate server makes it easier to scale horizontally later (i.e., you can clone this server behind the load balancer).
	3.	Dedicated Database Server
		•	Separating the database onto its own server offloads query processing from your web/application server.
		•	Allows for easier maintenance, backups, and potential replication in the future.

Load Balancer Details
	•	Distribution Algorithm: Common choices include round-robin, least connections, and IP hash.
	•	Round-robin: Each new incoming connection is sent to the next server in a list, distributing load evenly over time.
	•	Least connections: Sends new requests to the server with the fewest active connections.
	•	Active-Active vs. Active-Passive:
	•	Active-Active: All back-end servers are online and actively receiving traffic at the same time.
	•	Active-Passive: One server actively handles traffic, and the other(s) remain on standby. If the active server fails, a passive server takes over.

	In this minimal diagram, we show only one web/app server (Server #2).

Database Primary-Replica (Master-Slave) Cluster

Although our diagram shows only one database node (Server #3):
	1.	Primary (Master) Node
		•	Handles all write operations (INSERT, UPDATE, DELETE).
		•	Sends data changes (binary logs) to its Replica(s).
	2.	Replica (Slave) Node(s)
		•	Receives changes (binlogs) from the Primary and applies them, keeping data in sync.
		•	Often used for read operations to reduce load on the Primary.

Difference for the Application:
	•	In many setups, application reads can be directed to a Replica, while writes go to the Primary. This improves performance and availability (reads can continue even if the Primary is under heavy load).
	•	If the Primary fails, a Replica can sometimes be promoted to become the new Primary.

Issues / Limitations in This Setup
	1.	Single Points of Failure (SPOF)
		•	The Load Balancer itself can become a SPOF if there is no redundant LB (e.g., a second HAProxy in failover).
		•	The Database server is also a SPOF if we only have one MySQL node.
	2.	Security Concerns
		•	No firewall is mentioned, leaving servers exposed directly to the internet.
		•	No HTTPS (SSL/TLS) offloading means that data could be traveling unencrypted between the user and HAProxy (or HAProxy to Nginx).
	3.	No Monitoring
		•	There is no mention of a monitoring system (e.g., Nagios, Prometheus, etc.). If something fails, it may go unnoticed until major problems arise.
