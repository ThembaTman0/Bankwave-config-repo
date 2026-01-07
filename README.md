# 📦 Bankwave Config Repository

## Overview

This repository contains **centralized external configuration** for the Bankwave microservices ecosystem.
It is consumed by **Spring Cloud Config Server** to provide environment-specific configuration to multiple services, including:

* **Accounts**
* **Cards**
* **Loans**

The main goal is to **decouple configuration from application code**, enabling safer deployments, easier environment management, and consistent configuration across all services.

---

## 🧱 Architecture

```text
┌─────────────────────┐
│ Config Repository   │
│ (this repo)         │
└─────────▲───────────┘
          │
┌─────────┴───────────┐
│ Config Server       │
│ (Spring Cloud)      │
└─────────▲───────────┘
          │
┌─────────┴───────────┐
│ Microservices       │
│ Accounts / Cards    │
│ Loans               │
└─────────────────────┘
```

Each microservice retrieves its configuration from the Config Server at startup based on:

* **Application name**
* **Active profile** (e.g. `qa`, `prod`)

---

## 📂 Repository Structure

```text
config-repo/
├── accounts.yml
├── accounts-qa.yml
├── accounts-prod.yml
│
├── cards.yml
├── cards-qa.yml
├── cards-prod.yml
│
├── loans.yml
├── loans-qa.yml
├── loans-prod.yml
└── README.md
```

---

## 📝 Naming Convention

Configuration files follow this pattern:

```
<application-name>-<profile>.yml
```

### Examples

* `accounts-prod.yml`
* `cards-qa.yml`
* `loans.yml` (default profile)

---

## 🌍 Environment Profiles

Each service supports multiple environments:

* **default** – local or fallback configuration
* **qa** – quality assurance/testing
* **prod** – production configuration

Profiles are activated using Spring Boot’s profile activation mechanism:

```yaml
spring:
  config:
    activate:
      on-profile: prod
```

---

## ⚙️ Example Configuration

```yaml
accounts:
  message: "Welcome to Bankwave Accounts PROD APIs"
  contact-details:
    name: "Themba Ngobeni"
    email: "support@bankwave.com"
  on-call-support:
    - "(011) 123-4567"
    - "(011) 987-6543"
```

---

## 🔐 Security Considerations

* ❌ **Do NOT commit secrets** (passwords, tokens, API keys) to this repository
* Sensitive data should be managed using:

  * Environment variables
  * Secret management tools (e.g. HashiCorp Vault, AWS Secrets Manager)

This repository is intended for **non-sensitive configuration only**.

---

## 🔄 Configuration Refresh

Configuration changes can be applied to services:

* On **application restart**, or
* Dynamically using **Spring Cloud Bus** and `/actuator/busrefresh` (if enabled)

---

## 🚀 Benefits of This Approach

* Centralized configuration management
* Environment-specific behavior without code changes
* Safer and more controlled production deployments
* Improved scalability across microservices
* Follows industry-standard Spring Cloud practices

---

## 🧑‍💻 Maintainer

**Themba Ngobeni**
Software Engineer – Java & Microservices

* 📧 Email: [thembatman0@gmail.com](mailto:thembatman0@gmail.com)
* 🔗 GitHub: [https://github.com/thembatman0](https://github.com/thembatman0)

---

## 📌 Notes

This repository is designed to evolve alongside the Bankwave microservices platform and follows best practices for cloud-native and distributed systems.

~~~ In real world this repo should be private :)
