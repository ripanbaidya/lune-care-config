## eureka-server config

### Purpose

- Holds centralized configuration for the Eureka service registry.

### Files

- `application.yml`: base eureka settings.
- `application-dev.yml`: development overrides.
- `application-prod.yml`: production overrides.
- `application-docker.yml`: Docker runtime overrides.

### Notes

- Keep service registry behavior in this folder.
- Move shared values to root files when reused by many apps.
