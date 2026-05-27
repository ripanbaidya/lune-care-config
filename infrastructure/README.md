## Infrastructure Configuration

### Purpose

- This folder contains config-server-managed settings for core infrastructure components.
- These components support service discovery, routing, and centralized config delivery.

### Folders

- `api-gateway/`:
  - Gateway routing and edge configuration.
  - Files present: `application.yml`, `application-dev.yml`, `application-prod.yml`, `application-docker.yml`.
- `config-server/`:
  - Configuration service settings.
  - Files present: `application.yml`, `application-dev.yml`, `application-prod.yml`.
- `eureka-server/`:
  - Service registry settings.
  - Files present: `application.yml`, `application-dev.yml`, `application-prod.yml`, `application-docker.yml`.

### How to edit

- Use profile files for environment-specific overrides.
- Keep only component-specific values here; shared global values belong at repo root.
