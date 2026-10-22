# DriverDen — Driver Hiring & Management System

A web platform connecting car owners, businesses, and private individuals with licensed, verified drivers for flexible hiring contracts.

DriverDen focuses on hiring drivers—not booking passenger seats. Clients can find suitable drivers for hourly engagements, full-day errands, outstation trips, and recurring monthly chauffeur contracts.

> Development status: This README describes the planned product scope and architecture. Feature availability and setup instructions will be updated as implementation progresses.

## Table of Contents

- [Overview](#overview)
- [Technology Stack](#technology-stack)
- [User Roles](#user-roles)
- [Core Features](#core-features)
- [Foundation Modules](#foundation-modules)
- [Database Design](#database-design)
- [Booking Lifecycle](#booking-lifecycle)
- [Getting Started](#getting-started)
- [Development Roadmap](#development-roadmap)
- [Contributing](#contributing)
- [License](#license)

## Overview

Finding a reliable driver involves more than checking availability. Clients need confidence in a driver's credentials, vehicle-handling skills, route familiarity, and professional conduct. Drivers also need clear contract terms, fair expense settlement, and accountability from clients.

DriverDen brings these needs into a single platform through:

- Verified driver profiles and credential tracking
- Search and matching based on skills, experience, rates, and availability
- Flexible booking and contract management
- Mutual reviews and formal dispute handling
- Expense records, financial summaries, and notifications
- Administrative oversight and safety intervention

## Technology Stack

| Layer | Technology / Approach |
|-------|------------------------|
| Backend | HTML |
| Database | MySQL |
| Architecture | Custom Model–View–Controller (MVC) |
| Access control | Role-based authentication |
| Version control | Git and GitHub |

Frontend tooling, supported runtime versions, and deployment requirements will be documented as the implementation is finalized.

## User Roles

### Client

- Browse and filter driver profiles.
- Review skills, experience, ratings, and availability.
- Create and manage hiring requests.
- Bookmark trusted drivers in a personal “My Fleet” roster.
- Review expenses and hiring history.
- Rate drivers and report booking-related issues.

### Driver

- Create a profile with license details, experience, and specialist skills.
- Manage availability and duty status.
- Accept, decline, or counter hiring requests.
- Track completed work, earnings, and reimbursable expenses.
- Review clients and report safety or payment concerns.
- Request an emergency substitute when necessary.

### Administrator

- Verify driver profiles and credentials.
- Moderate accounts and address misconduct.
- Review complaints and arbitrate disputes.
- Oversee platform activity and safety interventions.

## Core Features

The following 12 features define the planned core product.

| # | Feature | Description |
|---|---------|-------------|
| 1 | Flexible Booking Scopes | Support hourly, full-day, multi-day outstation, and recurring monthly driver contracts. |
| 2 | Transmission & Vehicle Skills | Record manual and automatic transmission expertise, luxury vehicle handling, armored vehicle clearance, and commercial             transport capabilities. |
| 3 | “My Fleet” Bookmarks | Let clients save trusted drivers and prioritize their private shortlist for future hiring requests. |
| 4 | Disputes & Escalation | Link complaints to specific bookings for issues such as route deviations, vehicle damage, payment withholding, or safety concerns. |
| 5 | Credential Tracking | Track license expiry and verification status, provide advance reminders, and restrict drivers with expired credentials. |
| 6 | Detailed Driver Ratings | Evaluate punctuality, vehicle care, route efficiency, and professional conduct rather than relying only on a single overall score.|
| 7 | Mutual Reviews | Allow drivers to review client conduct, payment timeliness, workplace safety, and vehicle reliability. |
| 8 | Expense Settlement | Record itemized fuel, toll, parking, and authorized overtime expenses alongside base compensation. |
| 9 | Booking Status Notifications | Notify users when requests are sent, accepted, activated, disputed, or completed. |
| 10 | Availability Calendar | Track available dates and duty states such as active shift, outstation assignment, and off-duty. |
| 11 | Emergency Substitute Handoff | Support reassignment during an emergency while preserving relevant contract terms. |
| 12 | Route & Terrain Expertise | Tag familiarity with urban traffic, highways, mountainous routes, and border-related requirements. |

## Foundation Modules

### Authentication & Access Control

Role-based access for clients, drivers, and administrators, with secure password hashing, session management, and account recovery.

### Driver Onboarding

Structured profile creation covering contact information, a profile photo, license details, and years of service.

### Driver Directory

A searchable directory with filters for rates, experience, ratings, and current availability.

### Booking & Response Management

A booking workflow covering pickup and drop-off points, scheduling, contract terms, and driver responses.

### Notification Center

A centralized inbox for booking updates, system notices, and verification-related alerts.

### Dashboards & Financial Summaries

- Client dashboard for active engagements, upcoming bookings, pending requests, and quick rehiring.
- Driver dashboard for shift history, completed trips, earnings, tips, and reimbursable expenses.
- Administrative dashboard for verification, moderation, and dispute resolution.

## Database Design

The specification identifies the following principal entities and supporting relationship table:

| Table | Purpose |
|-------|---------|
| `users` | Account information and user roles |
| `driver_profiles` | Driver credentials, skills, experience, verification, and availability |
| `hiring_requests` | Booking details, contract status, expenses, and substitute handoffs |
| `reviews` | Role-aware ratings and feedback |
| `reports` | Complaints, disputes, and escalation records |
| `notifications` | User alerts, event types, and read status |
| `saved_drivers` | Relationships between clients and their bookmarked drivers |

The specification describes six core relational entities and separately references `saved_drivers` for “My Fleet” bookmarking. The final schema should reconcile this distinction during database design.

### Planned Data Integrity Approach

- Use foreign keys to maintain valid relationships between records.
- Use transactions for related multi-step updates.
- Link reviews and reports to the relevant users and bookings.
- Link substitute assignments to their original hiring request.
- Keep expense information associated with its booking.

The final schema, migrations, indexes, and deletion rules will be documented alongside the implementation.

## Booking Lifecycle

The primary booking flow is:

```text
Request Sent → Accepted → Active Transit → Completed
```

Additional workflows include:

- Declining or countering a request before acceptance
- Opening a dispute associated with a booking
- Reassigning a contract through an emergency substitute handoff

Status changes are intended to generate notifications for the relevant users.

## Getting Started

### Clone the Repository

```bash
git clone [https://github.com/raisa0411/fall-26-27-DriversDen-management-system.git](https://github.com/raisa0411/fall-26-27-DriversDen-management-system.git)
cd fall-26-27-DriversDen-management-system
```

### Local Setup

The application is planned for HTML and MySQL using a custom MVC architecture.

Detailed setup instructions will be added when the project structure is available, including:

1. Required HTML and MySQL versions
2. Required HTML extensions
3. Web server and document-root configuration
4. Database creation and schema import or migrations
5. Local configuration and environment variables
6. Development startup commands
7. Test execution instructions

Do not commit database passwords, API keys, or other private credentials to the repository.

## Development Roadmap

### Phase 1 — MVP

- [ ] Establish the custom MVC application structure.
- [ ] Finalize the relational database schema.
- [ ] Implement authentication and role-based access.
- [ ] Build driver onboarding and verification.
- [ ] Implement the searchable driver directory.
- [ ] Develop booking and driver-response workflows.
- [ ] Implement the 12 core features.
- [ ] Add dashboards and administrative moderation.
- [ ] Configure email notifications.
- [ ] Test booking, review, expense, and dispute workflows.

### Phase 2 — Growth

- [ ] Integrate digital escrow payments.
- [ ] Add in-app calling or phone-number masking.

Potential payment integrations identified in the specification include Stripe, SSLCommerz, and bKash. Provider selection and integration details remain to be finalized.

### Phase 3 — Enterprise

- [ ] Add corporate accounts and multi-driver hiring.
- [ ] Support pooled corporate billing.
- [ ] Introduce live GPS tracking for active contracts.

### Additional Proposed Enhancements

- [ ] Driver health and vision verification badges
- [ ] Rate estimates based on duration, terrain, demand, night driving, and vehicle class

## Contributing

1. Fork the repository.
2. Create a feature branch:

   ```bash
   git checkout -b feature/your-feature-name
   ```

3. Implement and test your changes.
4. Commit with a clear message:

   ```bash
   git commit -m "Describe your changes"
   ```

5. Push to your fork:

   ```bash
   git push origin feature/your-feature-name
   ```

6. Open a pull request explaining the changes and referencing any related issue.

For major changes, open an issue first to discuss the scope and approach.

## License

A project license has not yet been specified in this README. Add the selected license and a corresponding `LICENSE` file before distributing the project under explicit license terms.
