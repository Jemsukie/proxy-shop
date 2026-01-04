# Japanese Proxy Shopping Platform - Project Documentation

**Welcome!** This folder contains all the documentation for the Japanese Proxy Shopping Platform project. This README provides an overview and navigation guide for non-technical stakeholders.

---

## 📋 Quick Summary

This project will build a **Japanese Proxy Shopping Web Application** using RedwoodJS, similar to irasshaimase.co.kr.

The platform will enable Korean customers to:

- Browse and purchase products from Japanese marketplaces (Mercari, Yahoo Auctions, Rakuten, Amazon Japan)
- Request proxy buying services for items from Japanese e-commerce sites
- Use shipping forwarding services (Japanese address → Korea)
- Manage wallet deposits and currency conversion (KRW ↔ JPY)
- Track orders from request to delivery
- Access customer support and FAQ

**Admins** will have tools to:

- Process proxy buying requests and manage orders
- Handle shipping and logistics
- Manage user accounts and wallets
- Process payments and currency conversions
- Generate financial reports
- Provide customer support

---

## 📚 Document Overview

This project documentation is organized into four main documents:

### 1. [Project Proposal](./japanese-proxy-shopping-platform.md)

**What it covers:** Complete feature list, project phases, timeline, platform pricing structure, and team structure

**Key Information:**

- Detailed breakdown of all features for users and admins
- 4-phase development plan (8 weeks / 2 months)
- Gantt chart showing project timeline
- Platform pricing structure (service fees, shipping, currency conversion)
- Team structure and responsibilities

**Best for:** Understanding what will be built and when

---

### 2. [Development Requirements & Costing](./development-requirements-and-costing.md)

**What it covers:** Technical infrastructure, hosting requirements, and monthly costs

**Key Information:**

- Server and database requirements
- Monthly hosting costs breakdown
- Infrastructure components (storage, email, monitoring)
- Scaling considerations for future growth
- Beta testing infrastructure

**Best for:** Understanding infrastructure needs and ongoing costs

**Monthly Cost Summary:**

- **Staging Environment:** ~$25–$26/month
- **Production Environment:** ~$80–$174/month
- **Total:** ~$105–$200/month (depending on optional services)

---

### 3. [Development Costing & Support Terms](./development-costing-and-support-terms.md)

**What it covers:** Development costs, payment structure, support terms, and project terms

**Key Information:**

- **Total Development Cost:** $4,000 (based on $1,000 per 2-week phase)
- Payment structure aligned with 2-week phases
- 90-day warranty period
- 25 hours of free post-launch support (60-day expiry)
- Ongoing support rates ($25/hour)
- Single retainer package details
- What's included vs. what's not included
- Project timeline and acceptance criteria

**Best for:** Understanding costs, payment schedule, and support terms

---

### 4. [System Flowcharts](./system-flowcharts.md)

**What it covers:** Visual process diagrams with embedded PlantUML code

**Key Information:**

- User registration and authentication flow
- Proxy buying request workflow
- Shipping forwarding process
- Payment and wallet management
- Order tracking system
- Admin order processing
- System architecture overview
- Currency conversion flow

**Best for:** Understanding system processes and workflows

---

## 💰 Cost Summary

### One-Time Development Cost

- **Total:** $4,000 USD (4 phases × $1,000 per 2-week phase)
- **Payment Structure:**
  - $1,000 per 2-week phase (aligned with deliverables)
  - OR Custom payment schedule upon agreement

### Ongoing Monthly Costs (After Launch)

- **Infrastructure/Hosting:** ~$80–$174/month
- **Email Service:** ~$25–$65/month (depending on volume)
- **Support:** $25/hour (after free 25 hours)

### What's NOT Included in Development Cost

- ❌ UI/UX design work (must be provided separately)
- ❌ Infrastructure and hosting costs
- ❌ Domain registration and DNS (client responsibility)
- ❌ Third-party service fees (email, APIs, payment processing, etc.)
- ❌ Content creation and design assets

---

## ⏱️ Project Timeline

**Total Duration:** 8 Weeks (2 Months)

| Phase                                     | Duration | Key Deliverables                                                            |
| ----------------------------------------- | -------- | --------------------------------------------------------------------------- |
| **Phase 1:** Discovery & Core Development | 2 weeks  | Requirements, architecture, authentication, user profiles, product browsing |
| **Phase 2:** Order System & Admin Panel   | 2 weeks  | Order requests, admin processing, purchase workflow, notifications          |
| **Phase 3:** Payment & Shipping           | 2 weeks  | Wallet, currency conversion, shipping forwarding, package management        |
| **Phase 4:** Integration, QA & Launch     | 2 weeks  | Testing, security, marketplace integration, deployment, monitoring          |

See the [Project Detailed Proposal](./japanese-proxy-shopping-platform.md) for detailed Gantt chart.

---

## ✅ What You'll Get

### For Users

- Secure login and profile management
- Product browsing from Japanese marketplaces
- Proxy buying request system
- Shipping forwarding service
- Wallet and payment management
- Order tracking and history
- Currency conversion display
- Customer support access

### For Admins

- Order management and processing tools
- User account management
- Payment and wallet administration
- Shipping and logistics management
- Product verification system
- Financial reporting and analytics
- Customer support tools

### Technical Deliverables

- Complete source code (RedwoodJS)
- Production-ready application
- Deployment scripts and configuration
- Technical documentation
- User and admin guides
- Knowledge transfer session

---

## 🔧 Infrastructure Requirements

The platform will run on:

- **Framework:** RedwoodJS (full-stack JavaScript)
- **Servers:** DigitalOcean (cloud hosting)
- **Database:** PostgreSQL (managed database)
- **Storage:** DigitalOcean Spaces (for media files)
- **Email:** Brevo/Sendinblue (for notifications)
- **CDN:** Cloudflare (for fast content delivery)

**Client Responsibilities:**

- Domain registration and DNS management
- Providing UI/UX designs before development starts
- Infrastructure and hosting costs (monthly)
- Payment gateway setup and credentials

See [Development Requirements & Costing](./development-requirements-and-costing.md) for detailed infrastructure breakdown.

---

## 🛡️ Support & Warranty

### Warranty Period

- **90 days** post-launch
- Covers critical bugs and security issues
- Automatic fixes at no additional cost

### Free Post-Launch Support

- **25 hours** of free revisions/adjustments
- Must be used within **60 days** of launch
- For minor fixes and refinements

### Ongoing Support

- **$25/hour** after free hours
- Response times: 4-48 hours (depending on priority)
- Standard support: Monday-Friday, 9 AM-6 PM

### Retainer Package

- Single retainer package available
- Includes 25 free hours (60-day expiry from launch)
- After free hours: $25/hour ongoing support
- Priority support included

See [Development Costing & Support Terms](./development-costing-and-support-terms.md) for complete support details.

---

## 📋 Important Notes

### Design Requirement

**UI/UX design work is NOT included** in the development scope. Design assets (wireframes, mockups, design system) must be provided by the client or a separate designer **before development begins**.

### Domain & DNS

**Domain registration and DNS management are client responsibilities.** The developer will provide configuration guidance and assist with setup, but the client must purchase and manage the domain.

### Payment Gateway

**Payment gateway setup and credentials are client responsibilities.** The developer will integrate the payment system, but the client must provide payment gateway accounts and credentials.

### Scope Changes

Any changes to the original project scope will be handled through a formal change request process with updated timeline and cost estimates.

---

## 📞 Next Steps

To proceed with this project:

1. **Review all documentation** in this folder
2. **Confirm project scope** and timeline
3. **Provide UI/UX designs** (or arrange for designer)
4. **Set up infrastructure accounts** (DigitalOcean, email service, payment gateway, etc.)
5. **Finalize payment structure** (phase-based payments)
6. **Sign agreement** and begin Phase 1

---

## 📄 Document Links

- **[Project Proposal](./japanese-proxy-shopping-platform.md)** - Complete feature list and project plan
- **[Development Requirements & Costing](./development-requirements-and-costing.md)** - Infrastructure and hosting details
- **[Development Costing & Support Terms](./development-costing-and-support-terms.md)** - Costs, payment, and support terms
- **[System Flowcharts](./system-flowcharts.md)** - Visual process diagrams with embedded PlantUML code

---
