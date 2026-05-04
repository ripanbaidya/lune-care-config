# lune-care-config

centralized spring cloud config repository for the lunecare microservices ecosystem.

## repository structure

```
lune-care-config/
├── application.yml               # Shared defaults — ALL services inherit this
├── application-dev.yml           # Shared dev overrides
├── application-prod.yml          # Shared prod overrides
│
├── infrastructure/
│   ├── api-gateway/
│   │   ├── application.yml
│   │   ├── application-dev.yml
│   │   └── application-prod.yml
│   ├── config-server/
│   │   ├── application.yml
│   │   ├── application-dev.yml
│   │   └── application-prod.yml
│   └── eureka-server/
│       ├── application.yml
│       ├── application-dev.yml
│       └── application-prod.yml
│
└── services/
    ├── auth/
    ├── doctor/
    ├── patient/
    ├── appointment/
    ├── payment/
    ├── notification/
    ├── feedback/
    └── admin/
        └── (each with application.yml, application-dev.yml, application-prod.yml)
```

## Config Loading Priority (High → Low)

Spring Cloud Config merges configs in this order:
1. `services/{app}/application-{profile}.yml`  ← highest priority
2. `services/{app}/application.yml`
3. `application-{profile}.yml`                 ← root shared
4. `application.yml`                           ← lowest priority (root shared)

## Secrets Management Strategy

| Environment | Strategy |
|---|---|
| **Dev (local)** | `.env` file (never committed) + `export` in shell |
| **Prod** | Environment variables injected by deployment platform (Docker, K8s, Render, Railway) |

**Never hardcode secrets in YAML files committed to Git.**

### Loading .env locally

```bash
# Option 1: export manually
export CLOUDINARY_API_KEY=your_key

# Option 2: use dotenv-cli
npx dotenv-cli -- java -jar service.jar

# Option 3: IntelliJ → Run Config → Environment Variables
```

## How Each Service Bootstraps

Each service's local `src/main/resources/application.yml` contains only:

```yaml
spring:
  application:
    name: auth             # must match folder name in this repo
  profiles:
    active: dev
  config:
    import: "optional:configserver:http://localhost:8888"

server:
  port: 8081
```

## Triggering Config Refresh at Runtime

```bash
# Refresh single service
curl -X POST http://localhost:{port}/actuator/refresh

# Broadcast refresh to ALL services via Spring Cloud Bus
curl -X POST http://localhost:8888/actuator/busrefresh
```


