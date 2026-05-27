## services configuration

### Purpose

- This folder contains config-server-managed settings for business microservices.
- Each subfolder maps to one Spring Boot service name.

### Services in this repository

- `admin/`
- `appointment/`
- `auth/`
- `doctor/`
- `feedback/`
- `notification/`
- `patient/`
- `payment/`

### File pattern

- Most services follow this structure:
  - `application.yml`
  - `application-dev.yml`
  - `application-prod.yml`
  - `application-docker.yml` (present only where needed)

### How to edit

- Put service defaults in `application.yml`.
- Put environment differences in profile files.
- Keep values local to the owning service folder.
- Move truly shared values to root `application*.yml` files.
