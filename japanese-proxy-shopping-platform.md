# Project Proposal: Japanese Proxy Shopping Platform

**Prepared by:** Jemuel Lupo
**Role:** Technical Lead / Architect
**Reference Inspiration:** irasshaimase.co.kr (Japanese Proxy Shopping Service)

---

> 📖 **Navigation:** [← Back to README](./README.md) | [Infrastructure Requirements](./development-requirements-and-costing.md) | [Costing & Support Terms](./development-costing-and-support-terms.md)

---

## 1. Executive Summary

This proposal outlines the design and development of a **Japanese Proxy Shopping Web Application** using RedwoodJS, enabling Korean customers to purchase products from Japanese e-commerce marketplaces.

The platform will support:

* Product browsing from Japanese marketplaces (Mercari, Yahoo Auctions, Rakuten, Amazon Japan)
* Proxy buying services (purchase items on behalf of customers)
* Shipping forwarding services (Japanese address → Korea)
* Wallet and payment management with currency conversion (KRW ↔ JPY)
* Order tracking and management
* Customer support and FAQ system

The system is designed to ensure scalability, security, and long-term maintainability while providing a seamless shopping experience for Korean customers accessing Japanese products.

---

## 2. Project Objectives

* Build a **comprehensive proxy shopping platform** similar to irasshaimase.co.kr
* Enable seamless product discovery from multiple Japanese marketplaces
* Provide reliable proxy buying and shipping forwarding services
* Support secure payment processing with real-time currency conversion
* Deliver transparent order tracking and customer support
* Design a scalable foundation that supports future marketplace integrations
* Ensure compliance with international shipping and customs regulations

---

## 3. Scope of Work

### 3.1 User Features

#### Authentication & Profile Management
* **Secure Login System**
  - Email and password authentication
  - Password reset functionality via email
  - Session management with secure token handling
  - Two-factor authentication (optional, future phase)
  
* **User Profile**
  - Personal information management (name, email, phone, address)
  - Shipping address management (Korean delivery address)
  - Profile picture upload and management
  - Account settings and preferences
  - Notification preferences

#### Product Search & Browsing
* **Marketplace Integration**
  - Browse products from Mercari
  - Browse products from Yahoo Auctions
  - Browse products from Rakuten
  - Browse products from Amazon Japan
  - Browse products from Yahoo Shopping
  - Product search and filtering across marketplaces
  - Product detail view with images and descriptions
  - Price display in both JPY and KRW (with conversion)
  - Product availability checking

* **Product Discovery**
  - Category browsing
  - Search functionality with filters
  - Saved searches and alerts
  - Product comparison
  - Recently viewed products
  - Popular/trending products display

#### Proxy Buying Service
* **Purchase Request System**
  - Submit product links from Japanese marketplaces
  - Product information extraction and validation
  - Price verification and confirmation
  - Quantity and variant selection
  - Special instructions/notes for purchase
  - Request submission and tracking
  - Request modification/cancellation (before processing)

* **Order Management**
  - View all purchase requests
  - Order status tracking (Pending, Processing, Purchased, Shipped, Delivered)
  - Order history and archive
  - Order details and receipts
  - Order cancellation requests
  - Reorder functionality

#### Shipping Forwarding Service
* **Forwarding Address**
  - Japanese forwarding address assignment
  - Address management and verification
  - Multiple package consolidation options
  - Package storage duration settings

* **Shipping Management**
  - Package received notifications
  - Package photos and verification
  - Shipping method selection (EMS, DHL, FedEx, etc.)
  - Shipping cost calculation
  - Customs declaration assistance
  - International shipping tracking
  - Delivery confirmation

#### Wallet & Payment System
* **Wallet Management**
  - KRW deposit functionality
  - Wallet balance display
  - Transaction history
  - Deposit/withdrawal requests
  - Payment method management (bank transfer, credit card)

* **Currency Conversion**
  - Real-time JPY/KRW exchange rate display
  - Automatic currency conversion for purchases
  - Conversion fee transparency
  - Exchange rate history
  - Currency conversion calculator

* **Payment Processing**
  - Secure payment processing
  - Multiple payment methods
  - Payment confirmation and receipts
  - Refund processing
  - Payment history and invoices

#### Order Tracking & History
* **Order Status Tracking**
  - Real-time order status updates
  - Status change notifications (email, SMS, in-app)
  - Order timeline and activity log
  - Estimated delivery dates
  - Shipping tracking numbers and links

* **Order History**
  - Complete order history
  - Order filtering and search
  - Order export functionality
  - Order receipts and invoices
  - Return/refund request history

#### Customer Support & FAQ
* **Support System**
  - Contact support form
  - Support ticket creation and tracking
  - Live chat (optional, future phase)
  - Support history and responses
  - File attachments for support requests

* **FAQ & Help Center**
  - Comprehensive FAQ section
  - Help articles and guides
  - Video tutorials (optional)
  - Service terms and conditions
  - Privacy policy and legal information

### 3.2 Admin Features

#### Authentication & Access Control
* **Admin Authentication**
  - Secure admin login system
  - Role-based access control (RBAC)
  - Multi-level admin permissions (Super Admin, Order Manager, Support Staff, Finance)
  - Admin activity logging
  - Session management and security

#### Order Management & Processing
* **Order Processing Workflow**
  - View all purchase requests
  - Order queue and prioritization
  - Product verification and validation
  - Purchase execution on Japanese marketplaces
  - Order status updates
  - Order notes and internal comments
  - Bulk order operations
  - Order search and filtering

* **Purchase Management**
  - Marketplace account management
  - Purchase execution tracking
  - Payment processing for purchases
  - Purchase confirmation and receipts
  - Failed purchase handling and retry
  - Purchase cost tracking

#### Shipping & Logistics Management
* **Package Management**
  - Package received notifications
  - Package verification and photos
  - Package consolidation management
  - Shipping label generation
  - Shipping method selection
  - Shipping cost calculation
  - Customs documentation
  - International shipping tracking
  - Delivery confirmation

* **Shipping Settings**
  - Shipping method configuration
  - Shipping rate tables
  - Shipping zone management
  - Delivery time estimates
  - Shipping carrier integration

#### User Management
* **User Administration**
  - View all user accounts
  - User search and filtering (by name, email, status)
  - User profile editing capabilities
  - User account activation/deactivation
  - User verification status management
  - User activity monitoring
  - User communication tools
  - Bulk user operations

#### Payment & Wallet Management
* **Wallet Administration**
  - View all user wallets
  - Wallet balance management
  - Deposit processing and approval
  - Withdrawal processing and approval
  - Transaction history and audit logs
  - Refund processing
  - Payment reconciliation

* **Currency Management**
  - Exchange rate configuration
  - Exchange rate update scheduling
  - Conversion fee settings
  - Currency conversion history
  - Exchange rate alerts

#### Financial Reporting
* **Financial Analytics**
  - Revenue reports (daily, weekly, monthly, custom)
  - Order statistics and trends
  - Payment processing reports
  - Currency conversion reports
  - Service fee reports
  - Shipping cost analysis
  - Profit margin analysis
  - Export reports (CSV, PDF, Excel)

* **Financial Management**
  - Invoice generation
  - Payment reconciliation
  - Financial dashboard
  - Cash flow tracking
  - Tax reporting support

#### Product Verification
* **Product Management**
  - Product information verification
  - Product image validation
  - Price verification
  - Availability checking
  - Product quality assessment
  - Restricted item checking
  - Product approval/rejection workflow

#### Customer Support Tools
* **Support Management**
  - View all support tickets
  - Ticket assignment and prioritization
  - Ticket response and resolution
  - Support ticket search and filtering
  - Support analytics and reporting
  - Knowledge base management
  - FAQ content management

#### System Administration
* **System Settings**
  - Platform configuration management
  - Email template customization
  - Notification settings
  - System maintenance mode
  - Backup and restore management
  - System health monitoring
  - Marketplace API configuration
  - Payment gateway configuration

### 3.3 System & Infrastructure Features

#### Background Processing
* **Automated Job System**
  - Order status synchronization
  - Shipping tracking updates
  - Currency exchange rate updates
  - Email notification queue processing
  - Data cleanup and maintenance tasks
  - Job status monitoring and error handling
  - Retry mechanisms for failed jobs

#### API Integrations
* **Marketplace API Connections**
  - Mercari API integration (web scraping or API if available)
  - Yahoo Auctions API integration
  - Rakuten API integration
  - Amazon Japan API integration
  - Yahoo Shopping API integration
  - API rate limit management
  - API error handling and fallback mechanisms
  - API credential management and rotation
  - Data synchronization scheduling

* **Shipping Carrier Integrations**
  - EMS/Japan Post API
  - DHL API integration
  - FedEx API integration
  - UPS API integration (optional)
  - Shipping label generation
  - Tracking number retrieval

* **Payment Gateway Integrations**
  - Payment processor API integration
  - Bank transfer processing
  - Credit card processing
  - Refund processing
  - Payment webhook handling

#### Data Management
* **Storage & Media Handling**
  - Secure file upload and storage system
  - Product image storage and optimization
  - Package photo storage
  - Document storage (invoices, receipts)
  - CDN integration for media delivery
  - File access control and permissions
  - Storage quota management
  - Backup and disaster recovery

#### Security & Compliance
* **Security Features**
  - Data encryption at rest and in transit
  - Secure authentication mechanisms
  - API security and rate limiting
  - DDoS protection
  - Security audit logging
  - Regular security updates and patches
  - Compliance with data protection regulations (GDPR, Korean privacy laws)
  - PCI DSS compliance for payment processing

#### Audit & Logging
* **Comprehensive Logging**
  - User activity logs
  - Admin action logs
  - Order change history
  - Payment transaction logs
  - System error logs
  - API call logs
  - Log search and filtering capabilities
  - Log retention policies

#### Performance & Scalability
* **System Optimization**
  - Database query optimization
  - Caching strategies for improved performance
  - Load balancing capabilities
  - Scalable architecture for high concurrent users
  - Performance monitoring and alerting
  - Database backup and replication

---

## 4. Platform Pricing Structure

### 4.1 Service Fees

* **Proxy Buying Service Fee**
  - Fixed fee per order: ¥500 JPY (~$3.50 USD)
  - OR Percentage-based: 5% of product price (minimum ¥300 JPY)
  - Fee calculation and transparency
  - Fee display before order confirmation

* **Shipping Forwarding Fees**
  - Domestic Japan shipping: Included in product price or separate fee
  - International shipping to Korea: Based on weight and shipping method
  - Package consolidation fee: ¥300 JPY per additional package
  - Storage fee: Free for first 30 days, ¥100 JPY/day after

* **Currency Conversion Fees**
  - Exchange rate markup: 2-3% above market rate
  - Conversion fee transparency
  - Real-time rate display
  - Rate lock option for orders (optional)

### 4.2 Shipping Costs

* **Shipping Method Options**
  - EMS (Express Mail Service): Fast, tracked, insured
  - DHL Express: Fastest, premium service
  - FedEx International: Reliable, tracked
  - Standard Air Mail: Economical option
  - Shipping cost calculator based on weight and dimensions

* **Customs & Duties**
  - Customs declaration assistance
  - Duty estimation (customer responsibility)
  - Customs documentation preparation

### 4.3 Payment Processing Fees

* **Payment Method Fees**
  - Bank transfer: No additional fee
  - Credit card: 2.5% processing fee
  - Digital wallet: 1.5% processing fee

### 4.4 Minimum Order Requirements

* **Minimum Order Value**
  - Minimum order: ¥1,000 JPY (~$7 USD)
  - Minimum wallet deposit: ¥5,000 JPY (~$35 USD)
  - Minimum withdrawal: ¥10,000 JPY (~$70 USD)

### 4.5 Fee Calculation Examples

* **Example 1: Small Item Purchase**
  - Product price: ¥2,000 JPY
  - Service fee (5%): ¥100 JPY
  - Domestic shipping: ¥500 JPY
  - International shipping: ¥1,500 JPY
  - **Total: ¥4,100 JPY (~$29 USD)**

* **Example 2: Multiple Items with Consolidation**
  - Product 1: ¥3,000 JPY
  - Product 2: ¥2,500 JPY
  - Service fee (5%): ¥275 JPY
  - Consolidation fee: ¥300 JPY
  - International shipping: ¥2,000 JPY
  - **Total: ¥8,075 JPY (~$57 USD)**

---

## 5. Phased Delivery Plan

### Phase 1 – Discovery & Core Development (2 weeks)
* Requirements gathering and analysis
* Feature scoping (MVP focus)
* Technical architecture design
* Database schema design
* API integration planning
* Review and implementation of provided design assets
* Authentication system (email/password, JWT)
* Role-based access control (User, Admin roles)
* User profile management
* Product browsing interface
* Marketplace integration (1-2 marketplaces)

### Phase 2 – Order System & Admin Panel (2 weeks)
* Order request system
* Order processing workflow
* Admin order management panel
* Purchase execution system (manual admin process)
* Order status tracking
* Notification system
* Admin dashboard enhancements
* Order history and reporting

### Phase 3 – Payment & Shipping (2 weeks)
* Wallet system implementation
* Currency conversion system
* Payment gateway integration
* Deposit/withdrawal processing
* Shipping forwarding system
* Package management
* Shipping carrier integration
* Shipping cost calculation
* International shipping tracking

### Phase 4 – Integration, QA & Launch (2 weeks)
* Additional marketplace integrations (if needed)
* Complete marketplace API connections
* Functional testing across all features
* Security hardening and vulnerability assessment
* Performance optimization
* Code review and quality assurance
* Payment security audit
* Production environment setup
* Production deployment
* Monitoring and alerting setup
* Post-launch support and monitoring

---

## 6. Gantt Chart (Estimated Timeline – 8 Weeks)

| Phase | Wk 1-2 | Wk 3-4 | Wk 5-6 | Wk 7-8 |
|-------|:------:|:------:|:------:|:------:|
| Discovery & Core Development | ████ | | | |
| Order System & Admin Panel | | ████ | | |
| Payment & Shipping | | | ████ | |
| Integration, QA & Launch | | | | ████ |

*Note: Timeline optimized for 2-month delivery. Each phase is 2 weeks at $1,000 per phase.*

---

## 7. Team Structure

* **Technical Lead / Architect:** Jemuel Lupo
* Frontend Developer (RedwoodJS)
* Backend Developer (RedwoodJS API)
* UI/UX Designer (if not provided by client)
* QA Engineer (phase-based)

*(Team can be scaled depending on timeline urgency)*

---

## 8. Assumptions & Technical Considerations

* **Marketplace Access:** Some Japanese marketplaces may require special access or have API limitations. Web scraping may be necessary for some platforms.
* **Payment Gateway:** Client must provide payment gateway accounts and credentials (Stripe, PayPal, or local Korean payment processors).
* **Shipping Carriers:** Shipping carrier accounts and API access must be provided by client.
* **Currency Exchange:** Real-time exchange rate API access required (client responsibility or third-party service).
* **Legal Compliance:** Client responsible for compliance with Korean import/export regulations and customs requirements.
* **Design Assets:** UI/UX designs must be provided before development begins (or arranged separately).

### Database Scalability

The system is designed to handle high concurrent users efficiently. Modern relational database systems are well-equipped to handle this scale with proper configuration:

* **Connection Pooling:** Efficient connection management to handle concurrent requests
* **Query Optimization:** Indexed queries and optimized database schema for fast read/write operations
* **Caching Layer:** Strategic caching to reduce database load for frequently accessed data
* **Read Replicas:** Database replication capabilities for scaling read operations
* **Horizontal Scaling:** Architecture supports database scaling as user base grows

The beta phase will include comprehensive load testing to validate system performance under realistic load conditions, ensuring all components (database, API, background jobs, payment processing) perform optimally.

---

## 9. Next Steps

To proceed, we recommend confirming:

1. MVP scope (optimized for 2-month delivery)
2. Target marketplaces for initial launch (priority order - recommend starting with 1-2)
3. Payment gateway preference
4. Shipping carrier preferences
5. Launch window confirmation

Once confirmed, we can finalize milestones and begin immediately.

---

**Prepared by:**
Jemuel Lupo
Tech Lead – E-commerce Platforms & Scalable Web Systems

---

> 📖 **Navigation:** [← Back to README](./README.md) | [Infrastructure Requirements](./development-requirements-and-costing.md) | [Costing & Support Terms](./development-costing-and-support-terms.md)

