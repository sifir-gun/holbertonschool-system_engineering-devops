# Web Infrastructure Design Project

## Description
This project focuses on designing and understanding web infrastructures, ranging from simple architecture to more complex and secured systems. The goal is to master fundamental web infrastructure concepts and be able to explain each component without external help.

## Learning Objectives

By the end of this project, you should be able to:

* Draw and explain a diagram covering the complete web stack
* Explain the role of each component
* Understand system redundancy
* Master the acronyms: LAMP, SPOF, QPS

## Key Concepts

* Network basics
* Servers (Web and Application)
* DNS and record types
* Load balancer
* Monitoring
* Database
* HTTPS
* Firewall

## Project Structure

The project is divided into 4 main tasks:

### 0. Simple Web Stack
* Single server configuration with LAMP stack
* Domain: www.foobar.com
* Components: 
  - 1 server
  - 1 web server (Nginx)
  - 1 application server
  - 1 database (MySQL)

### 1. Distributed Web Infrastructure
* Multi-server configuration
* Components:
  - 2 servers
  - Load-balancer (HAproxy)
  - Primary-Replica database configuration

### 2. Secured and Monitored Web Infrastructure
* Addition of security measures and monitoring
* Additional components:
  - 3 firewalls
  - SSL certificate
  - 3 monitoring clients

### 3. Scale Up
* Component separation
* Load-balancer cluster configuration
* Architecture optimization

## Technical Requirements

* Each task must be documented with diagrams
* Diagrams must be presented and explained
* Explanations must cover:
  - Role of each component
  - Single Points of Failure (SPOF)
  - Security issues
  - Monitoring strategies

## Documentation

For more information on specific concepts, refer to:
* Network basics
* Web server vs application server
* DNS record types
* High availability clusters
* HTTPS and security

## Directory Structure

```
holbertonschool-system_engineering-devops/
├── web_infrastructure_design/
│   ├── 0-simple_web_stack
│   ├── 1-distributed_web_infrastructure
│   ├── 2-secured_and_monitored_web_infrastructure
│   └── 3-scale_up
└── README.md
```

## Important Notes

* All documentation must be in English
* Presentation sessions will be done without computer or notes
* Focus on the requested requirements
* Presentation time is limited to 30 minutes
* Each diagram must be manually reviewed
* Screenshots of completed tasks must be uploaded to an image hosting service

## Repository Information

* GitHub repository: `holbertonschool-system_engineering-devops`
* Directory: `web_infrastructure_design`
* Files: 
  - `0-simple_web_stack`
  - `1-distributed_web_infrastructure`
  - `2-secured_and_monitored_web_infrastructure`
  - `3-scale_up`
