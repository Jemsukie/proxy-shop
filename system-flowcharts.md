# System Flowcharts

This document contains visual flowcharts for the Japanese Proxy Shopping Platform system. All diagrams use embedded PlantUML code that can be rendered using VS Code extensions or online tools.

> 📖 **Navigation:** [← Back to README](./README.md) | [Project Proposal](./japanese-proxy-shopping-platform.md) | [Infrastructure Requirements](./development-requirements-and-costing.md) | [Costing & Support Terms](./development-costing-and-support-terms.md)

---

## 1. User Registration & Authentication Flow

**User Registration & Authentication Process**

This flowchart shows the complete user registration and authentication process for customers.

**Key Elements:**

- Email/password registration
- Email verification
- Login authentication
- JWT token generation
- Session management
- Password reset functionality
- Error handling and retry options

**Use Cases:**

- Understanding registration and login security flow
- Explaining authentication to stakeholders
- Development reference for authentication implementation
- User onboarding process documentation

**PlantUML Code:**

```plantuml
@startuml User Registration & Authentication
start
:User visits registration page;
:User enters email and password;
:Validate email format;
if (Email valid?) then (no)
  :Show error message;
  stop
endif
:Check if email exists;
if (Email exists?) then (yes)
  :Show "Email already registered" error;
  stop
endif
:Validate password strength;
if (Password valid?) then (no)
  :Show password requirements;
  stop
endif
:Create user account;
:Generate verification token;
:Send verification email;
:Show "Check email" message;
:User clicks verification link;
:Verify token;
if (Token valid?) then (no)
  :Show "Invalid link" error;
  stop
endif
:Activate user account;
:Redirect to login;
:User enters credentials;
:Validate credentials;
if (Credentials valid?) then (no)
  :Show "Invalid credentials" error;
  stop
endif
:Generate JWT token;
:Store session;
:Redirect to dashboard;
stop
@enduml
```

---

## 2. Proxy Buying Request Flow

**Proxy Buying Request Workflow**

This flowchart visualizes the complete workflow from product link submission to purchase completion.

**Key Elements:**

- User submits product link
- Product information extraction
- Price verification
- Order request creation
- Admin review and processing
- Purchase execution
- Order status updates
- Notification system

**Use Cases:**

- Explaining order process to customers
- Training admin staff on order processing
- Development reference for order system
- Stakeholder understanding of proxy buying workflow

**PlantUML Code:**

```plantuml
@startuml Proxy Buying Request Flow
start
:User browses Japanese marketplace;
:User finds product;
:User copies product link;
:User submits link on platform;
:Extract product information;
if (Product info valid?) then (no)
  :Show error message;
  :Request manual entry;
endif
:Display product details;
:Show price in JPY and KRW;
:User confirms order;
:Calculate total cost;
:Check wallet balance;
if (Balance sufficient?) then (no)
  :Prompt for deposit;
  stop
endif
:Create order request;
:Set status: Pending;
:Notify admin;
:Admin reviews order;
if (Order approved?) then (no)
  :Set status: Rejected;
  :Notify user with reason;
  stop
endif
:Set status: Processing;
:Admin executes purchase;
if (Purchase successful?) then (no)
  :Set status: Failed;
  :Notify user;
  :Refund wallet;
  stop
endif
:Set status: Purchased;
:Update order with purchase details;
:Notify user;
:Wait for package arrival;
stop
@enduml
```

---

## 3. Shipping Forwarding Flow

**Shipping Forwarding Process**

This flowchart shows how packages are received, consolidated, and shipped internationally to Korea.

**Key Elements:**

- Package received at Japanese address
- Package verification
- Photo capture
- Consolidation options
- Shipping method selection
- Cost calculation
- Customs documentation
- International shipping
- Delivery tracking

**Use Cases:**

- Understanding shipping workflow
- Training shipping staff
- Development reference for shipping system
- Customer communication about shipping process

**PlantUML Code:**

```plantuml
@startuml Shipping Forwarding Flow
start
:Package arrives at Japanese address;
:Receive package notification;
:Admin verifies package;
:Capture package photos;
:Update order status: Package Received;
:Notify user;
if (Multiple packages?) then (yes)
  :Check consolidation request;
  if (Consolidate?) then (yes)
    :Wait for all packages;
    :Consolidate packages;
  endif
endif
:Calculate package weight/dimensions;
:Calculate shipping costs;
:User selects shipping method;
:Generate shipping label;
:Prepare customs documentation;
:Update order status: Shipping;
:Send package via carrier;
:Update tracking number;
:Notify user with tracking;
:Monitor shipping status;
if (Package delivered?) then (yes)
  :Update status: Delivered;
  :Notify user;
  :Request delivery confirmation;
  stop
endif
if (Customs issue?) then (yes)
  :Notify user;
  :Assist with customs;
endif
stop
@enduml
```

---

## 4. Payment & Wallet Flow

**Payment & Wallet Management**

This flowchart illustrates the wallet deposit, currency conversion, and payment processing workflow.

**Key Elements:**

- Wallet deposit process
- Currency conversion (KRW to JPY)
- Exchange rate updates
- Payment processing
- Transaction history
- Withdrawal requests

**Use Cases:**

- Understanding payment workflow
- Explaining currency conversion to users
- Development reference for payment system
- Financial reconciliation process

**PlantUML Code:**

```plantuml
@startuml Payment & Wallet Flow
start
:User navigates to wallet;
:View current balance;
if (User wants to deposit?) then (yes)
  :Select deposit amount (KRW);
  :Choose payment method;
  if (Bank transfer?) then (yes)
    :Show bank details;
    :User makes transfer;
    :Admin verifies payment;
    :Credit wallet;
  else (Credit card)
    :Process payment;
    if (Payment successful?) then (yes)
      :Credit wallet;
    else (no)
      :Show error;
      stop
    endif
  endif
  :Update transaction history;
  :Notify user;
endif
if (User makes purchase?) then (yes)
  :Calculate order total (JPY);
  :Get current exchange rate;
  :Convert JPY to KRW;
  :Add service fees;
  :Check wallet balance;
  if (Balance sufficient?) then (no)
    :Prompt for deposit;
    stop
  endif
  :Deduct from wallet;
  :Create payment transaction;
  :Update order with payment;
  :Notify user;
endif
if (User requests withdrawal?) then (yes)
  :Check minimum withdrawal;
  if (Amount valid?) then (no)
    :Show error;
    stop
  endif
  :Create withdrawal request;
  :Admin processes withdrawal;
  :Transfer funds;
  :Update transaction history;
  :Notify user;
endif
stop
@enduml
```

---

## 5. Order Tracking Flow

**Order Status Tracking System**

This flowchart shows how order status is tracked and updated throughout the entire order lifecycle.

**Key Elements:**

- Order status updates
- Real-time notifications
- Status change triggers
- Timeline display
- Activity logging

**Use Cases:**

- Understanding order lifecycle
- Customer support reference
- Development reference for tracking system
- User communication about order status

**PlantUML Code:**

```plantuml
@startuml Order Tracking Flow
start
:Order created;
:Status: Pending;
:Notify user;
:Admin reviews order;
if (Order approved?) then (yes)
  :Status: Processing;
  :Notify user;
  :Admin executes purchase;
  if (Purchase successful?) then (yes)
    :Status: Purchased;
    :Notify user;
    :Wait for package;
    if (Package received?) then (yes)
      :Status: Package Received;
      :Notify user;
      :Admin prepares shipping;
      :Status: Shipping;
      :Notify user with tracking;
      :Monitor shipping;
      if (Delivered?) then (yes)
        :Status: Delivered;
        :Notify user;
        :Request confirmation;
        stop
      endif
    endif
  else (no)
    :Status: Purchase Failed;
    :Notify user;
    :Process refund;
    stop
  endif
else (no)
  :Status: Rejected;
  :Notify user with reason;
  stop
endif
stop
@enduml
```

---

## 6. Admin Order Processing Flow

**Admin Order Processing Workflow**

This flowchart illustrates how admins process orders from review to purchase execution.

**Key Elements:**

- Order queue management
- Product verification
- Purchase execution
- Status updates
- Error handling
- Communication with users

**Use Cases:**

- Admin training and onboarding
- Understanding order processing workflow
- Development reference for admin panel
- Process optimization

**PlantUML Code:**

```plantuml
@startuml Admin Order Processing
start
:Admin views order queue;
:Filter orders by status;
:Select order to process;
:Review order details;
:Verify product information;
if (Product info valid?) then (no)
  :Request clarification from user;
  :Set status: Needs Info;
  stop
endif
:Check product availability;
if (Product available?) then (no)
  :Set status: Out of Stock;
  :Notify user;
  :Process refund;
  stop
endif
:Verify price;
if (Price changed?) then (yes)
  :Notify user of price change;
  :Request confirmation;
  if (User confirms?) then (no)
    :Cancel order;
    :Refund wallet;
    stop
  endif
endif
:Approve order;
:Set status: Processing;
:Execute purchase on marketplace;
if (Purchase successful?) then (yes)
  :Set status: Purchased;
  :Record purchase details;
  :Update order with receipt;
  :Notify user;
  :Wait for package;
else (no)
  :Set status: Purchase Failed;
  :Log error;
  :Notify user;
  :Process refund;
  :Investigate issue;
endif
stop
@enduml
```

---

## 7. System Architecture Flow

**High-Level System Architecture**

This flowchart provides a high-level overview of system components and their interactions.

**Key Elements:**

- Client-server architecture
- Application layer components (Web, API, SSE, Workers)
- Data layer structure (PostgreSQL, Redis, Storage)
- External service integrations (Marketplaces, Shipping, Payment, Email)

**Use Cases:**

- Technical architecture overview
- Infrastructure planning
- Explaining system design to stakeholders
- Onboarding new developers

**PlantUML Code:**

```plantuml
@startuml System Architecture
package "Client Layer" {
  [Web Browser] as Web
  [Mobile Browser] as Mobile
}

package "Application Layer" {
  [RedwoodJS Web] as WebApp
  [RedwoodJS API] as API
  [GraphQL] as GraphQL
  [SSE Server] as SSE
  [Background Workers] as Workers
}

package "Data Layer" {
  database "PostgreSQL" as DB
  database "Redis" as Redis
  cloud "DigitalOcean Spaces" as Storage
}

package "External Services" {
  [Mercari API] as Mercari
  [Yahoo Auctions] as Yahoo
  [Rakuten API] as Rakuten
  [Amazon Japan] as Amazon
  [Shipping Carriers] as Shipping
  [Payment Gateway] as Payment
  [Email Service] as Email
  [Exchange Rate API] as Exchange
}

Web --> WebApp
Mobile --> WebApp
WebApp --> API
API --> GraphQL
API --> SSE
GraphQL --> DB
GraphQL --> Redis
Workers --> DB
Workers --> Redis
Workers --> Storage
API --> Mercari
API --> Yahoo
API --> Rakuten
API --> Amazon
Workers --> Shipping
API --> Payment
Workers --> Email
Workers --> Exchange
SSE --> Web
SSE --> Mobile
@enduml
```

---

## 8. Currency Conversion Flow

**Currency Conversion Process**

This flowchart shows how exchange rates are updated and currency conversions are performed.

**Key Elements:**

- Exchange rate updates
- Rate caching
- Conversion calculation
- Fee application
- Transaction logging

**Use Cases:**

- Understanding currency conversion
- Explaining exchange rates to users
- Development reference for conversion system
- Financial reconciliation

**PlantUML Code:**

```plantuml
@startuml Currency Conversion Flow
start
:Scheduled job runs (every hour);
:Fetch exchange rate from API;
if (API call successful?) then (no)
  :Use cached rate;
  :Log error;
  :Retry in 15 minutes;
  stop
endif
:Parse JPY/KRW rate;
:Apply markup (2-3%);
:Store rate in database;
:Update Redis cache;
:Set rate expiry (1 hour);
if (User requests conversion?) then (yes)
  :Get current rate from cache;
  if (Rate expired?) then (yes)
    :Fetch fresh rate;
    :Update cache;
  endif
  :User enters JPY amount;
  :Calculate KRW equivalent;
  :Apply conversion fee;
  :Display total cost;
  :User confirms;
  :Log conversion transaction;
  :Update wallet;
  :Notify user;
endif
stop
@enduml
```
