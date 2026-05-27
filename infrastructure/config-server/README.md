## config-server config

### Purpose

- Holds centralized configuration for the Spring Cloud Config Server.

### Files

- `application.yml`: base config-server settings.
- `application-dev.yml`: development overrides.
- `application-prod.yml`: production overrides.

### Notes

- Keep only config-server-specific values in this folder.
- Shared platform defaults belong in root config files.
