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

This project documentation is organized into five main documents:

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
- **Production Environment:** ~$55–$149/month (with self-hosted BillionMail)
- **Total:** ~$80–$175/month (depending on optional services)
- *Note: Using self-hosted BillionMail (free). Brevo available as optional alternative ($25–$65/month)*

---

### 3. [Development Costing & Support Terms](./development-costing-and-support-terms.md)

**What it covers:** Development costs, payment structure, support terms, and project terms

**Key Information:**

- **Total Development Cost:** $4,000
- Payment structure: 50-50 split (50% before start, 50% upon completion)
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

### 5. [UI Design Samples](./ui-design-samples.md)

**What it covers:** Preliminary UI/UX mockups, design direction, and visual references

**Key Information:**

- 6 UI/UX sample screens (dashboard, product search, order forms, wallet, tracking, admin)
- Design principles and color schemes
- ShadCN component integration approach
- Layout patterns and responsive design notes
- Design process and next steps

**Important Note:** These are preliminary mockups for visualization, not final designs. Final implementation will use ShadCN components.

**Best for:** Understanding the visual direction and UI/UX approach

---

## 💰 Cost Summary

### One-Time Development Cost

- **Total:** $4,000 USD
- **Payment Structure:**
  - 50% ($2,000) before project start
  - 50% ($2,000) upon project completion and acceptance

### Ongoing Monthly Costs (After Launch)

- **Infrastructure/Hosting:** ~$55–$149/month (with self-hosted BillionMail, or ~$80–$174/month if using Brevo)
- **Email Service:** $0/month (self-hosted BillionMail) or ~$25–$65/month (if using Brevo)
- **Support:** $25/hour (after free 25 hours)

### What's NOT Included in Development Cost

- ❌ Branding and visual identity (logo, brand colors, brand guidelines)
- ❌ Infrastructure and hosting costs
- ❌ Domain registration and DNS (client responsibility)
- ❌ Third-party service fees (email, APIs, payment processing, etc.)
- ❌ Content creation (copywriting, marketing materials)

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
- UI/UX design files and wireframes (ShadCN-based, included)
- Design system documentation
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
- **Email:** Self-hosted BillionMail (free, or Brevo if client prefers)
- **CDN:** Cloudflare (for fast content delivery)

**Client Responsibilities:**

- Domain registration and DNS management (we recommend Namecheap for domain purchase)
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

### Design Included

**UI/UX design work using ShadCN is INCLUDED in the development cost at no additional charge.** The developer will create wireframes, mockups, design system, and implement all UI/UX designs using ShadCN components as part of the development process.

### Domain & DNS

**Domain registration and DNS management are client responsibilities.** We recommend purchasing the domain through **Namecheap** (~$10–$15/year). The developer will provide configuration guidance and assist with DNS setup, but the client must purchase and manage the domain.

### Payment Gateway

**Payment gateway setup and credentials are client responsibilities.** The developer will integrate the payment system, but the client must provide payment gateway accounts and credentials.

### Scope Changes

Any changes to the original project scope will be handled through a formal change request process with updated timeline and cost estimates.

---

## 📞 Next Steps

To proceed with this project:

1. **Review all documentation** in this folder
2. **Confirm project scope** and timeline
3. **Purchase domain** through Namecheap (recommended, ~$10–$15/year)
4. **Set up infrastructure accounts** (DigitalOcean, payment gateway, etc.) - Note: Email service will be self-hosted BillionMail (no account needed), or Brevo if preferred
5. **Finalize payment structure** (50-50 split: 50% before start, 50% upon completion)
6. **Sign agreement** and begin development

---

## 📄 Document Links

- **[Project Proposal](./japanese-proxy-shopping-platform.md)** - Complete feature list and project plan
- **[Development Requirements & Costing](./development-requirements-and-costing.md)** - Infrastructure and hosting details
- **[Development Costing & Support Terms](./development-costing-and-support-terms.md)** - Costs, payment, and support terms
- **[System Flowcharts](./system-flowcharts.md)** - Visual process diagrams with embedded PlantUML code
- **[UI Design Samples](./ui-design-samples.md)** - Preliminary UI/UX mockups and design direction

---
