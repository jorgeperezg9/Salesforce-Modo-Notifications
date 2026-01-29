# Salesforce ↔ Modo Event-Driven Notification Integration

This project demonstrates a **real-world Salesforce integration** that sends
**event-driven push notifications** to the Modo platform when appointment data
changes in Salesforce.

The solution is designed for **higher education use cases**, where students
and staff need timely updates without relying on scheduled jobs or polling.

---

## Key Features

- **Event-Driven Architecture**
  - Notifications are triggered immediately on meaningful record changes
  - No polling, batch jobs, or schedulers

- **Bulk-Safe Apex Design**
  - Handles large data volumes safely
  - Prevents duplicate processing in a single transaction

- **Asynchronous Callouts**
  - External REST API calls executed using `@future(callout=true)`
  - Keeps triggers fast and compliant with Salesforce limits

- **Secure Integration**
  - Authentication handled via **Named Credentials**
  - No secrets, tokens, or org-specific endpoints in source control

---

## How It Works

1. An Appointment record is **created or updated** in Salesforce
2. The trigger invokes `AppointmentTriggerHandler`
3. The handler detects **meaningful changes** (status, time, location)
4. A notification payload is built
5. A REST callout sends the message to **Modo**
6. End users receive a near-real-time notification
