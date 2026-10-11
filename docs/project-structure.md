# OluBitsFinOps — Project Structure and Namespace Conventions

## Purpose

This document defines the initial internal organization of the OluBitsFinOps solution.

The objective is to maintain clear responsibilities, consistent namespaces, and a structure that can evolve as business features are implemented.

## Solution Structure

```text
OluBitsFinOps/
├── docs/
│   ├── git-workflow.md
│   └── project-structure.md
├── src/
│   ├── OluBitsFinOps.Domain/
│   │   └── Entities/              (planned)
│   ├── OluBitsFinOps.Application/
│   │   ├── Interfaces/            (planned)
│   │   └── Services/              (planned)
│   ├── OluBitsFinOps.Infrastructure/
│   │   └── Persistence/           (planned)
│   └── OlubitsFinOps.Api/
│       └── Controllers/           (existing)
└── OluBitsFinOps.slnx
```

Planned folders will be introduced when their first meaningful implementation files are created.

## Project Responsibilities

### Domain

Contains core business entities, business rules, and domain behaviour.

Domain must remain independent of the other solution projects.

### Application

Contains application use cases, orchestration logic, and abstractions required by application workflows.

Application may reference Domain but must not reference Infrastructure.

### Infrastructure

Contains technical implementations such as database persistence and external service integrations.

Infrastructure may reference Application and Domain.

### API

Contains HTTP endpoints, request handling, and dependency injection configuration.

API references Application and Infrastructure.

## Namespace Conventions

Namespaces should follow the project name and logical folder structure.

Examples:

- `OluBitsFinOps.Domain.Entities`
- `OluBitsFinOps.Application.Interfaces`
- `OluBitsFinOps.Application.Services`
- `OluBitsFinOps.Infrastructure.Persistence`
- `OlubitsFinOps.Api.Controllers`

Namespaces are logical identifiers and are not required by C# to match physical folders. We follow this convention for consistency and maintainability.

## Design Guidelines

1. Avoid creating folders or abstractions without a clear responsibility.
2. Keep core business rules inside Domain.
3. Keep application use-case coordination inside Application.
4. Keep persistence and external technology implementations inside Infrastructure.
5. Keep controllers focused on HTTP concerns and delegation to Application.
6. Avoid introducing unnecessary complexity before it is justified by actual requirements.
7. Revisit the structure as the application grows, including the possibility of feature-based organization.

## Architectural Boundaries

The intended project reference relationships are:

- Domain → No project references
- Application → Domain
- Infrastructure → Application and Domain
- API → Application and Infrastructure

These boundaries were established in Task 15.

Automated architectural enforcement may be introduced as part of the testing and quality strategy.