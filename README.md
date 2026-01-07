# Bankwave Configuration Repository

Bankwave Microservices Configuration Repository - Environment-specific properties for Spring Cloud Config Server

## Services
- **Accounts** - Account management service
- **Cards** - Card management service
- **Loans** - Loan management service

## Environments
- `prod` - Production configuration
- `qa` - QA/Testing configuration

## Usage
Configure Config Server to point to this repository:
```yaml
spring:
  cloud:
    config:
      server:
        git:
          uri: https://github.com/yourusername/bankwave-config-repo
```

## File Structure
```
├── accounts.yml
├── accounts-prod.yml
├── accounts-qa.yml
├── cards.yml
├── cards-prod.yml
├── cards-qa.yml
├── loans.yml
├── loans-prod.yml
├── loans-qa.yml
└── application.yml
```
