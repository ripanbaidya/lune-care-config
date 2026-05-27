lune-care-config

Purpose
- This repository stores centralized Spring Cloud Config files for the LuneCare microservices system.
- Services and infrastructure components read configuration from this repo through the config server.

What is in this repository
- Shared config files at root:
  - `application.yml` for common defaults.
  - `application-dev.yml` for shared development overrides.
  - `application-prod.yml` for shared production overrides.
  - `application-docker.yml` for shared Docker-specific values.
- Infrastructure-specific config under `infrastructure/`.
- Business service config under `services/`.

Current folder structure
- `infrastructure/`
  - `api-gateway/`
  - `config-server/`
  - `eureka-server/`
- `services/`
  - `admin/`
  - `appointment/`
  - `auth/`
  - `doctor/`
  - `feedback/`
  - `notification/`
  - `patient/`
  - `payment/`

How config is resolved
- Spring Cloud Config merges values from shared files and app-specific files.
- App-specific values override shared defaults.
- Profile files such as `application-dev.yml` or `application-prod.yml` override base `application.yml`.

Naming rules
- Each service folder name should match `spring.application.name` used by that service.
- Profile files should use the format `application-<profile>.yml`.

Environment files in this repo
- `.env.template` is an example file for local setup.
- `.env` may be used locally and should not be shared publicly.

How to maintain this repo
- Put cross-service defaults in root files.
- Put service-only values in that service folder.
- Avoid duplicating the same value in many places.
- Do not store secrets directly in committed YAML files.

Quick navigation
- Start with `infrastructure/README.md` for infra components.
- Start with `services/README.md` for business services.
