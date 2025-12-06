# MenuMap Hardware/Software Mapping
## CEN4010 Software Engineering - Team 9

**Author:** Andre Lewis (Software Architecture & Design Lead)  
**Date:** [Current Date]  
**Version:** 1.0  

---

## 🖥️ Hardware/Software Mapping Overview

This document defines the deployment architecture, technology stack, and mapping of software components to hardware infrastructure for the MenuMap application. The system is designed for cloud-native deployment with microservices architecture.

---

## 🏗️ Deployment Architecture

### **Cloud Infrastructure Provider**
- **Primary**: Amazon Web Services (AWS)
- **Secondary**: Google Cloud Platform (GCP) for disaster recovery
- **CDN**: CloudFront for global content delivery

### **Architecture Pattern**
- **Microservices Architecture** with containerized deployment
- **Event-driven architecture** for real-time features
- **API Gateway pattern** for service orchestration
- **Database per service** pattern for data isolation

---

## 🖥️ Hardware Infrastructure

### **Production Environment**

#### **Web Tier (Load Balancer & API Gateway)**
```
Hardware Specifications:
├── Load Balancer (AWS Application Load Balancer)
│   ├── Type: Network Load Balancer
│   ├── Capacity: 10,000+ concurrent connections
│   ├── SSL Termination: Yes
│   └── Health Checks: HTTP/HTTPS
├── API Gateway (AWS API Gateway)
│   ├── Type: Regional API Gateway
│   ├── Rate Limiting: 10,000 requests/second
│   ├── Caching: 5GB cache
│   └── Monitoring: CloudWatch integration
└── CDN (CloudFront)
    ├── Edge Locations: 200+ globally
    ├── Cache Capacity: 1TB
    └── SSL/TLS: End-to-end encryption
```

#### **Application Tier (Microservices)**
```
Hardware Specifications:
├── Presentation Service
│   ├── Instance Type: t3.large (2 vCPU, 8GB RAM)
│   ├── Auto Scaling: 2-10 instances
│   ├── Load Balancing: Application Load Balancer
│   └── Health Checks: /health endpoint
├── Business Logic Service
│   ├── Instance Type: t3.xlarge (4 vCPU, 16GB RAM)
│   ├── Auto Scaling: 3-15 instances
│   ├── Load Balancing: Application Load Balancer
│   └── Health Checks: /health endpoint
├── Security Service
│   ├── Instance Type: t3.large (2 vCPU, 8GB RAM)
│   ├── Auto Scaling: 2-8 instances
│   ├── Load Balancing: Application Load Balancer
│   └── Health Checks: /health endpoint
├── Menu Management Service
│   ├── Instance Type: t3.xlarge (4 vCPU, 16GB RAM)
│   ├── Auto Scaling: 3-12 instances
│   ├── Load Balancing: Application Load Balancer
│   └── Health Checks: /health endpoint
├── User Management Service
│   ├── Instance Type: t3.large (2 vCPU, 8GB RAM)
│   ├── Auto Scaling: 2-10 instances
│   ├── Load Balancing: Application Load Balancer
│   └── Health Checks: /health endpoint
└── Notification Service
    ├── Instance Type: t3.medium (2 vCPU, 4GB RAM)
    ├── Auto Scaling: 2-6 instances
    ├── Load Balancing: Application Load Balancer
    └── Health Checks: /health endpoint
```

#### **Data Tier (Databases & Storage)**
```
Hardware Specifications:
├── Primary Database (PostgreSQL)
│   ├── Instance Type: db.r5.xlarge (4 vCPU, 32GB RAM)
│   ├── Storage: 1TB SSD (gp3)
│   ├── Multi-AZ: Yes (High Availability)
│   ├── Backup: Automated daily backups
│   └── Encryption: At rest and in transit
├── Cache Layer (Redis)
│   ├── Instance Type: cache.r6g.large (2 vCPU, 13GB RAM)
│   ├── Cluster Mode: Yes (3 nodes)
│   ├── Persistence: RDB + AOF
│   └── Encryption: At rest and in transit
├── Search Engine (Elasticsearch)
│   ├── Instance Type: r6g.large (2 vCPU, 16GB RAM)
│   ├── Cluster: 3 master nodes + 3 data nodes
│   ├── Storage: 500GB SSD per node
│   └── Indexing: Real-time indexing
└── File Storage (S3)
    ├── Storage Class: Standard
    ├── Capacity: Unlimited
    ├── Versioning: Enabled
    └── Encryption: AES-256
```

#### **Message Queue & Event Streaming**
```
Hardware Specifications:
├── Message Queue (RabbitMQ)
│   ├── Instance Type: t3.medium (2 vCPU, 4GB RAM)
│   ├── Cluster: 3 nodes (High Availability)
│   ├── Persistence: Yes
│   └── Monitoring: CloudWatch integration
├── Event Streaming (Apache Kafka)
│   ├── Instance Type: t3.large (2 vCPU, 8GB RAM)
│   ├── Cluster: 3 brokers
│   ├── Storage: 100GB SSD per broker
│   └── Replication: 3x replication factor
└── Real-time Communication (WebSocket)
    ├── Instance Type: t3.medium (2 vCPU, 4GB RAM)
    ├── Auto Scaling: 2-8 instances
    ├── Load Balancing: Application Load Balancer
    └── Sticky Sessions: Yes
```

---

## 💻 Software Technology Stack

### **Frontend Technologies**
```
Web Application:
├── Framework: React 18.x
├── Language: TypeScript 4.x
├── State Management: Redux Toolkit
├── UI Library: Material-UI (MUI)
├── Routing: React Router v6
├── HTTP Client: Axios
├── Build Tool: Vite
└── Testing: Jest + React Testing Library

Mobile Application:
├── Framework: React Native 0.72.x
├── Language: TypeScript 4.x
├── Navigation: React Navigation v6
├── State Management: Redux Toolkit
├── UI Library: NativeBase
├── HTTP Client: Axios
└── Testing: Jest + React Native Testing Library
```

### **Backend Technologies**
```
Application Services:
├── Runtime: Node.js 18.x LTS
├── Framework: Express.js 4.x
├── Language: TypeScript 4.x
├── ORM: Prisma 5.x
├── Validation: Joi
├── Authentication: JWT + Passport.js
├── Logging: Winston
├── Monitoring: Prometheus + Grafana
└── Testing: Jest + Supertest

API Gateway:
├── Service: AWS API Gateway
├── Authentication: AWS Cognito
├── Rate Limiting: AWS WAF
├── Monitoring: AWS CloudWatch
└── Documentation: OpenAPI 3.0
```

### **Database Technologies**
```
Primary Database:
├── Database: PostgreSQL 15.x
├── Connection Pooling: PgBouncer
├── Migrations: Prisma Migrate
├── Backup: AWS RDS Automated Backups
└── Monitoring: AWS CloudWatch

Cache Layer:
├── Cache: Redis 7.x
├── Clustering: Redis Cluster
├── Persistence: RDB + AOF
├── Monitoring: RedisInsight
└── Backup: AWS ElastiCache Snapshots

Search Engine:
├── Search: Elasticsearch 8.x
├── Indexing: Logstash
├── Visualization: Kibana
├── Monitoring: Elastic APM
└── Backup: Elasticsearch Snapshots
```

### **DevOps & Infrastructure**
```
Containerization:
├── Container Runtime: Docker 24.x
├── Orchestration: Kubernetes 1.28.x
├── Service Mesh: Istio 1.19.x
├── Ingress: NGINX Ingress Controller
└── Monitoring: Prometheus + Grafana

CI/CD Pipeline:
├── Version Control: Git (GitHub)
├── CI/CD: GitHub Actions
├── Container Registry: AWS ECR
├── Deployment: ArgoCD
└── Testing: Automated testing pipeline

Monitoring & Logging:
├── Metrics: Prometheus
├── Visualization: Grafana
├── Logging: ELK Stack (Elasticsearch, Logstash, Kibana)
├── APM: New Relic
└── Alerting: PagerDuty
```

---

## 🔄 Software Component Mapping

### **Presentation Layer Mapping**
```
Web Interface:
├── Component: React SPA
├── Deployment: AWS S3 + CloudFront
├── Domain: www.menumap.com
├── SSL: AWS Certificate Manager
└── CDN: CloudFront (Global)

Mobile Interface:
├── Component: React Native App
├── Distribution: App Store + Google Play
├── Updates: Over-the-Air (OTA)
├── Analytics: Firebase Analytics
└── Crash Reporting: Crashlytics
```

### **Business Logic Layer Mapping**
```
Use Case Controllers:
├── Component: Node.js Microservices
├── Deployment: AWS ECS (Fargate)
├── Scaling: Auto Scaling Groups
├── Load Balancing: Application Load Balancer
└── Monitoring: CloudWatch + X-Ray

Business Rules Engine:
├── Component: Rule Engine Service
├── Deployment: AWS Lambda
├── Trigger: API Gateway
├── Scaling: Automatic (0-1000 concurrent)
└── Monitoring: CloudWatch
```

### **Data Access Layer Mapping**
```
Repository Services:
├── Component: Data Access Services
├── Deployment: AWS ECS (Fargate)
├── Database: AWS RDS PostgreSQL
├── Connection Pooling: PgBouncer
└── Monitoring: CloudWatch + RDS Insights

Cache Services:
├── Component: Redis Cache
├── Deployment: AWS ElastiCache
├── Cluster: Redis Cluster Mode
├── Backup: Automated Snapshots
└── Monitoring: CloudWatch
```

### **Security Subsystem Mapping**
```
Authentication Service:
├── Component: Auth Microservice
├── Deployment: AWS ECS (Fargate)
├── Database: AWS RDS PostgreSQL
├── Secrets: AWS Secrets Manager
└── Monitoring: CloudWatch + GuardDuty

Spam Protection Service:
├── Component: ML-based Detection
├── Deployment: AWS SageMaker
├── Model: Custom ML Model
├── Training: Automated retraining
└── Monitoring: CloudWatch + SageMaker
```

### **Menu Management Subsystem Mapping**
```
Menu Service:
├── Component: Menu Microservice
├── Deployment: AWS ECS (Fargate)
├── Database: AWS RDS PostgreSQL
├── Search: AWS OpenSearch
└── Monitoring: CloudWatch

Verification Service:
├── Component: Verification Microservice
├── Deployment: AWS ECS (Fargate)
├── Queue: AWS SQS
├── Processing: AWS Lambda
└── Monitoring: CloudWatch
```

### **User Management Subsystem Mapping**
```
User Service:
├── Component: User Microservice
├── Deployment: AWS ECS (Fargate)
├── Database: AWS RDS PostgreSQL
├── Cache: AWS ElastiCache Redis
└── Monitoring: CloudWatch

Favorites Service:
├── Component: Favorites Microservice
├── Deployment: AWS ECS (Fargate)
├── Database: AWS RDS PostgreSQL
├── Cache: AWS ElastiCache Redis
└── Monitoring: CloudWatch
```

### **Notification Subsystem Mapping**
```
Email Service:
├── Component: Email Microservice
├── Deployment: AWS ECS (Fargate)
├── SMTP: AWS SES
├── Templates: AWS S3
└── Monitoring: CloudWatch

Real-time Service:
├── Component: WebSocket Service
├── Deployment: AWS ECS (Fargate)
├── Load Balancing: Application Load Balancer
├── Sticky Sessions: Yes
└── Monitoring: CloudWatch
```

---

## 🌐 Network Architecture

### **Network Topology**
```
Internet
    ↓
CloudFront CDN (Global)
    ↓
AWS Application Load Balancer
    ↓
VPC (Virtual Private Cloud)
├── Public Subnets (AZ-1, AZ-2, AZ-3)
│   ├── Load Balancers
│   ├── NAT Gateways
│   └── Bastion Hosts
├── Private Subnets (AZ-1, AZ-2, AZ-3)
│   ├── Application Servers
│   ├── Database Servers
│   └── Cache Servers
└── Database Subnets (AZ-1, AZ-2, AZ-3)
    ├── RDS Instances
    ├── ElastiCache Clusters
    └── OpenSearch Clusters
```

### **Security Groups & NACLs**
```
Security Groups:
├── Web Tier SG
│   ├── Inbound: HTTP (80), HTTPS (443)
│   ├── Outbound: All traffic
│   └── Source: 0.0.0.0/0
├── Application Tier SG
│   ├── Inbound: HTTP (8080), HTTPS (8443)
│   ├── Outbound: Database (5432), Cache (6379)
│   └── Source: Web Tier SG
├── Database Tier SG
│   ├── Inbound: PostgreSQL (5432), Redis (6379)
│   ├── Outbound: None
│   └── Source: Application Tier SG
└── Management SG
    ├── Inbound: SSH (22), RDP (3389)
    ├── Outbound: All traffic
    └── Source: Corporate IP ranges
```

---

## 📊 Performance & Scalability

### **Auto Scaling Configuration**
```
Application Tier:
├── Min Instances: 2
├── Max Instances: 50
├── Target CPU: 70%
├── Target Memory: 80%
├── Scale Out Cooldown: 300s
└── Scale In Cooldown: 600s

Database Tier:
├── Min Instances: 1
├── Max Instances: 5
├── Target CPU: 80%
├── Target Memory: 85%
├── Scale Out Cooldown: 600s
└── Scale In Cooldown: 900s
```

### **Load Balancing Strategy**
```
Application Load Balancer:
├── Algorithm: Round Robin
├── Health Check: /health endpoint
├── Health Check Interval: 30s
├── Healthy Threshold: 2
├── Unhealthy Threshold: 5
└── Timeout: 5s

Database Load Balancing:
├── Primary: Read/Write
├── Replicas: Read-only
├── Connection Pooling: PgBouncer
├── Failover: Automatic
└── Monitoring: RDS Insights
```

---

## 🔒 Security Architecture

### **Network Security**
```
Firewall Rules:
├── Web Application Firewall (WAF)
│   ├── OWASP Top 10 Protection
│   ├── Rate Limiting: 10,000 req/min
│   ├── Geo-blocking: Configurable
│   └── DDoS Protection: AWS Shield
├── Network ACLs
│   ├── Subnet-level filtering
│   ├── Allow/Deny rules
│   └── Logging: VPC Flow Logs
└── Security Groups
    ├── Instance-level filtering
    ├── Stateful rules
    └── Least privilege access
```

### **Data Security**
```
Encryption:
├── Data at Rest: AES-256
├── Data in Transit: TLS 1.3
├── Database: RDS Encryption
├── Cache: ElastiCache Encryption
└── Storage: S3 Server-side Encryption

Key Management:
├── Key Store: AWS KMS
├── Key Rotation: Automatic
├── Access Control: IAM policies
└── Audit: CloudTrail logging
```

---

## 📈 Monitoring & Observability

### **Application Monitoring**
```
Metrics Collection:
├── Application Metrics: Prometheus
├── Infrastructure Metrics: CloudWatch
├── Custom Metrics: CloudWatch Custom
└── Log Metrics: CloudWatch Logs

Visualization:
├── Dashboards: Grafana
├── Alerts: CloudWatch Alarms
├── Notifications: SNS + PagerDuty
└── Reports: CloudWatch Insights
```

### **Log Management**
```
Log Aggregation:
├── Application Logs: ELK Stack
├── System Logs: CloudWatch Logs
├── Access Logs: ALB Access Logs
└── Security Logs: GuardDuty

Log Analysis:
├── Search: Elasticsearch
├── Visualization: Kibana
├── Alerting: Watcher
└── Retention: 90 days
```

---

## 🚀 Deployment Strategy

### **Deployment Pipeline**
```
CI/CD Pipeline:
├── Source Control: GitHub
├── Build: GitHub Actions
├── Test: Automated testing
├── Security Scan: SAST/DAST
├── Container Build: Docker
├── Registry: AWS ECR
├── Deployment: ArgoCD
└── Rollback: Automated rollback

Deployment Strategy:
├── Blue-Green Deployment
├── Canary Releases
├── Feature Flags
├── Database Migrations
└── Health Checks
```

### **Disaster Recovery**
```
Backup Strategy:
├── Database: Automated daily backups
├── Application: Container images
├── Configuration: Infrastructure as Code
└── Data: Cross-region replication

Recovery Plan:
├── RTO: 4 hours
├── RPO: 1 hour
├── Failover: Automated
└── Testing: Quarterly DR drills
```

---

*This hardware/software mapping provides the complete infrastructure foundation for MenuMap's scalable and secure deployment.*
