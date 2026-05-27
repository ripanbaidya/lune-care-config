## api-gateway config

## Purpose

- Holds centralized configuration for the API Gateway.

### Files

- `application.yml`: base gateway configuration.
- `application-dev.yml`: development overrides.
- `application-prod.yml`: production overrides.
- `application-docker.yml`: Docker runtime overrides.

### Notes

- Keep route and gateway-specific settings here.
- Shared values should stay in root-level shared config files.
