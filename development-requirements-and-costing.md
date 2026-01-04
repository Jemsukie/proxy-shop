# Minimal Infrastructure Requirements – Japanese Proxy Shopping Platform

**Project:** Japanese Proxy Shopping Platform
**Framework:** RedwoodJS
**Goal:** Simple, scalable, e-commerce proxy shopping platform

---

> 📖 **Navigation:** [← Back to README](./README.md) | [Project Proposal](./japanese-proxy-shopping-platform.md) | [Costing & Support Terms](./development-costing-and-support-terms.md)

---

## 1. Core Decisions (Final)

* Platform is a **proxy shopping web application**, not a marketplace
* **Server-Sent Events (SSE)** for realtime order updates
* **No WebSockets** (no chat, no bidirectional realtime)
* **No polling** (SSE replaces it)
* **Docker-based deployment**
* **No Kubernetes** for MVP
* **DigitalOcean Spaces** used for both **staging and production**

This keeps environments consistent and reduces deployment risk.

---

## 2. Realtime Strategy (What's Needed Only)

### Server-Sent Events (SSE)

Used for:

* Order status updates
* Payment notifications
* Shipping tracking updates
* Background job completion notifications

**Why SSE:**

* One-way (server → client)
* Lightweight
* Scales well for dashboards
* Simple to maintain

---

## 3. Infrastructure Components (Required Only)

### 3.1 Compute

**DigitalOcean Droplets**

| Environment | Size             | Purpose     | Est. Cost |
| ----------- | ---------------- | ----------- | --------- |
| Staging     | 2 vCPU / 4GB RAM | Dev & QA    | ~$12/mo   |
| Production  | 4 vCPU / 8GB RAM | Live system | ~$24/mo   |

---

### 3.2 Containerization

**Docker + Docker Compose**

Services:

* RedwoodJS Web
* RedwoodJS API (GraphQL + SSE)
* Background Worker
* Redis

> Kubernetes is intentionally excluded to reduce complexity.

---

### 3.3 Database

**PostgreSQL**

* **Staging:** Self-hosted Postgres (Docker)
  - Size: 2GB storage (sufficient for development/testing)
  - Cost: Included in droplet
  
* **Production:** DigitalOcean Managed PostgreSQL
  - Size: **db-s-2vcpu-4gb** (2 vCPU, 4GB RAM)
  - Storage: 25GB (expandable)
  - Connection limit: ~200 concurrent connections
  - Automatic daily backups (7-day retention)
  - Standby nodes for high availability (optional)
  - Estimated cost: **~$15–$25/mo**

**Sizing Rationale:**

* Average 10% concurrent usage for e-commerce platforms
* Connection pooling (max 100 connections, shared across users)
* Optimized queries with proper indexing
* Caching layer reduces database load
* Supports growth before scaling needed

---

### 3.4 Cache & Queues

**Redis** (required)

* SSE event broadcasting
* Background job queues
* Caching product data and exchange rates
* Rate limiting
* Session storage

**Setup:**

* **Staging:** Self-hosted Redis container (Docker)
  - Memory: 512MB (sufficient for dev/testing)
  - Cost: Included in droplet
  
* **Production:** Self-hosted Redis container (Docker)
  - Memory: 1GB (expandable to 2GB if needed)
  - Persistence: AOF (Append-Only File) enabled
  - Cost: Included in droplet
  - Future: Consider managed Redis if scaling beyond capacity

**Background Worker Sizing:**

* Worker instances: 2–3 workers per environment
* Resource allocation: 512MB–1GB RAM per worker
* Queue capacity: Handles 100+ concurrent jobs
* Job types: Order processing, shipping updates, currency sync, email sending, notifications

---

### 3.5 Object Storage

**DigitalOcean Spaces (Staging & Production)**

Used for:

* Product images
* Package photos
* User avatars
* Documents (invoices, receipts)
* Media assets

**Why Spaces everywhere:**

* Same S3-compatible API
* Same credentials pattern
* Same upload logic
* No environment drift

Estimated cost: **$5–$10/mo**

---

### 3.6 Load Balancer & Reverse Proxy

**Nginx (Self-hosted) or DigitalOcean Load Balancer**

* **Option 1: Nginx on Droplet (Recommended for MVP)**
  - SSL termination with Let's Encrypt
  - Request routing and load distribution
  - Rate limiting and DDoS protection
  - Cost: Included in droplet
  
* **Option 2: DigitalOcean Load Balancer**
  - Managed load balancer with SSL
  - Automatic health checks
  - Cost: **~$12/mo** (optional, for high availability)

**SSL Certificates:**

* Let's Encrypt (free, auto-renewal)
* Or DigitalOcean SSL certificates
* Cost: **$0–$5/mo**

---

### 3.7 Domain & DNS

**Client Responsibility**

Domain registration and DNS management are **handled by the client**, not included in development or infrastructure costs.

**Client Requirements:**
* Domain registration: Client purchases and manages domain
* DNS provider: Client configures DNS (Cloudflare, DigitalOcean DNS, or other)
* DNS records: Client sets up A/CNAME records pointing to production server
* CDN: Optional - Client may configure Cloudflare or other CDN for static assets

**Developer Support:**
* Developer will provide required DNS record configurations
* Developer will assist with DNS setup guidance
* SSL certificate setup (Let's Encrypt) will be configured by developer once DNS is ready

**Estimated Client Cost:** **~$10–$15/year** (domain registration) + DNS service (often free with Cloudflare)

---

### 3.8 Email & Notifications

**Brevo (Sendinblue)**

Used for:

* Account verification
* Password reset
* Order status notifications
* Payment confirmations
* Shipping updates
* Support ticket notifications

**Pricing Tiers:**

* Free tier: 300 emails/day
* Starter: $25/mo (10,000 emails/month)
* Business: $65/mo (20,000 emails/month)

Estimated cost: **$25–$100/mo** (volume-dependent)

**Expected Volume:**
* Average 5-10 emails per order
* Peak during high order volume: up to 30,000 emails/month

---

## 4. Monitoring & Observability

### 4.1 Application Monitoring

**DigitalOcean Monitoring (Free Tier)**
* CPU, memory, disk usage
* Network metrics
* Basic alerting
* Cost: **Free** (included with droplets)

**Error Tracking (Optional but Recommended)**
* Sentry (self-hosted or cloud)
* Application error tracking and alerting
* Cost: **$0–$26/mo** (free tier: 5,000 events/month)

### 4.2 Database Monitoring

* DigitalOcean Managed PostgreSQL includes monitoring
* Query performance insights
* Connection pool monitoring
* Cost: **Included** with managed database

### 4.3 Log Management

* Application logs: Stored on droplet (rotated)
* Centralized logging: Optional (ELK stack or cloud service)
* Cost: **$0–$20/mo** (if using cloud service)

---

## 5. Security & Compliance

### 5.1 Web Application Firewall (WAF)

**Cloudflare (Free Tier)**
* DDoS protection
* Basic WAF rules
* SSL/TLS encryption
* Cost: **Free** (paid plans available for advanced features)

### 5.2 Security Scanning

* Automated dependency scanning (GitHub Dependabot)
* Container image scanning (optional)
* Cost: **Free** (basic) or **$10–$50/mo** (advanced)

### 5.3 Rate Limiting

* Application-level rate limiting (Redis-based)
* API endpoint protection
* Cost: **Included** (uses Redis)

### 5.4 Payment Security

* PCI DSS compliance considerations
* Secure payment processing
* Tokenization for sensitive data
* Cost: **Included** (payment gateway handles compliance)

---

## 6. Backup & Disaster Recovery

### 6.1 Database Backups

**Production (Managed PostgreSQL)**
* Automatic daily backups
* 7-day retention (configurable)
* Point-in-time recovery available
* Cost: **Included** with managed database

**Staging (Self-hosted)**
* Manual backup scripts
* Weekly backups recommended
* Cost: **Included** (storage on droplet)

### 6.2 Application Data Backups

* DigitalOcean Spaces: Built-in redundancy
* Snapshot backups of droplets (optional)
* Cost: **$0–$5/mo** (for snapshots)

### 6.3 Disaster Recovery Plan

* Database: Automated backups with 7-day retention
* Application: Infrastructure as Code (Docker Compose)
* Recovery Time Objective (RTO): < 4 hours
* Recovery Point Objective (RPO): < 24 hours

---

## 7. Beta Testing Infrastructure

### 7.1 Beta Environment Options

**Option 1: Use Staging Environment (Recommended)**
* Leverage existing staging infrastructure
* No additional cost
* Isolated from production
* Suitable for 50-100 beta users

**Option 2: Separate Beta Environment**
* Additional droplet: 2 vCPU / 4GB RAM
* Shared database (staging) or separate instance
* Cost: **~$24–$40/mo** (if separate)

**Recommendation:** Use staging environment for beta testing to minimize costs while maintaining isolation from production.

### 7.2 Load Testing Infrastructure

* Load testing tools: k6, Apache JMeter, or Artillery
* Run from external machines (not production infrastructure)
* Simulate high concurrent users
* Cost: **Free** (open-source tools) or **$0–$20/mo** (cloud-based)

---

## 8. DevOps & Tooling

| Tool           | Purpose             | Cost                 |
| -------------- | ------------------- | -------------------- |
| GitHub         | Source control & CI | Free / Team          |
| GitHub Actions | CI/CD               | Included             |
| DockerHub      | Image registry (unlimited private repos) | $11/mo           |
| Cloudflare     | CDN + WAF           | Free / Optional paid |
| Let's Encrypt  | SSL certificates    | Free                 |

---

## 9. Detailed Cost Breakdown

### 9.1 Staging Environment

| Component | Details | Monthly Cost |
|-----------|---------|--------------|
| Droplet | 2 vCPU / 4GB RAM | $12 |
| Database | Self-hosted (Docker) | $0 (included) |
| Redis | Self-hosted (Docker) | $0 (included) |
| Object Storage | DigitalOcean Spaces (shared) | $2–$3 |
| Email | Brevo free tier (300/day) | $0 |
| SSL | Let's Encrypt (free) | $0 |
| DockerHub | Unlimited private repos | $11 |
| **Total Staging** | | **~$25–$26/mo** |
| Domain & DNS | Client responsibility | N/A |

### 9.2 Production Environment

| Component | Details | Monthly Cost |
|-----------|---------|--------------|
| Droplet | 4 vCPU / 8GB RAM | $24 |
| Database | Managed PostgreSQL (db-s-2vcpu-4gb) | $15–$25 |
| Redis | Self-hosted (Docker) | $0 (included) |
| Object Storage | DigitalOcean Spaces | $5–$10 |
| Email | Brevo (10K–20K emails/month) | $25–$65 |
| SSL | Let's Encrypt (free) | $0 |
| DockerHub | Unlimited private repos | $11 |
| Load Balancer | Optional DO Load Balancer | $0–$12 |
| Monitoring | DigitalOcean (free) + Optional Sentry | $0–$26 |
| **Total Production** | | **~$80–$174/mo** |
| Domain & DNS | Client responsibility | N/A |

### 9.3 Beta Testing (Using Staging)

| Component | Details | Monthly Cost |
|-----------|---------|--------------|
| Infrastructure | Uses staging environment | $0 (additional) |
| Load Testing Tools | Open-source (k6, JMeter) | $0 |
| **Total Beta** | | **$0** (no additional cost) |

### 9.4 Monthly Cost Summary

| Environment | Low Estimate | High Estimate |
| ----------- | ------------ | ------------- |
| Staging | $25 | $26 |
| Production | $80 | $174 |
| **Total** | **$105** | **$200** |

*Note: High estimate includes optional services (load balancer, advanced monitoring, higher email volume). Base production setup is ~$80–$105/mo.*

---

## 10. Performance & Scaling Considerations

### 10.1 Current Capacity

**Database:**
* Connection pooling: 100 connections (shared)
* Supports high concurrent users with proper configuration
* Query optimization and indexing in place
* Caching layer reduces database load by 60–80%

**Application:**
* 4 vCPU / 8GB RAM handles high traffic comfortably
* Background workers process jobs asynchronously
* Redis caching for frequently accessed data
* CDN for static assets reduces server load

### 10.2 Scaling Path

**Beyond Initial Capacity:**
* Upgrade database: db-s-4vcpu-8gb (~$60/mo)
* Add read replicas for analytics queries
* Scale up droplet: 8 vCPU / 16GB RAM (~$96/mo)
* Consider managed Redis for better performance

**High Traffic Scenarios:**
* Horizontal scaling: Multiple application servers
* Load balancer required
* Database read replicas
* Consider Kubernetes for orchestration

### 10.3 Performance Optimization

* Database query optimization and indexing
* Redis caching for products, exchange rates, and frequently accessed data
* CDN for static assets (Cloudflare)
* Connection pooling for database connections
* Background job processing for heavy operations
* API rate limiting to prevent abuse
* Image optimization and lazy loading

---

## 11. Final Notes

This setup:

* Matches proxy shopping platform requirements
* Supports high concurrent users comfortably
* Keeps staging and production **nearly identical**
* Minimizes operational overhead
* Allows future expansion without re-architecture
* Includes comprehensive monitoring and backup strategies
* Provides clear scaling path for growth

**This is the leanest, safest infrastructure needed to launch while maintaining production-grade reliability and scalability.**

### Key Infrastructure Decisions Summary

1. **Managed PostgreSQL in Production:** Ensures reliability, automated backups, and high availability
2. **Self-hosted Redis:** Cost-effective for MVP, can migrate to managed service later
3. **DigitalOcean Spaces:** Consistent S3-compatible storage across environments
4. **Cloudflare Free Tier:** Provides CDN, WAF, and DDoS protection at no cost
5. **Docker Compose:** Simple deployment without Kubernetes complexity
6. **Beta Testing on Staging:** Minimizes costs while maintaining isolation
7. **Domain & DNS:** Client responsibility - developer provides configuration guidance

### Risk Mitigation

* Automated database backups (7-day retention)
* Infrastructure as Code (Docker Compose) for quick recovery
* Monitoring and alerting for proactive issue detection
* Load testing during beta phase validates scalability
* Clear scaling path prevents architectural bottlenecks
* Payment security and PCI DSS compliance considerations

---

> 📖 **Navigation:** [← Back to README](./README.md) | [Project Proposal](./japanese-proxy-shopping-platform.md) | [Costing & Support Terms](./development-costing-and-support-terms.md)

