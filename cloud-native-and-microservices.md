---
description: Cloud Native Applications and Microservices Architecture
---

# Cloud Native and Microservices

## Goal of Microservice is Agility

- Smart experimentation
- Moving in-market with maximum velocity and minimum risk
- Gaining quick valuable insight to continuously change the value proposition
  and quality

## Agility: The Three Pillars

DevOps:

- Cultural Change
- Automated Pipeline
- Everything as Code
- Immutable Infrastructure

Microservices:

- Loose Coupling/Binding
- RESTful APIs
- Designed to resist failures
- Test by break / fail fast

Containers:

- Portability
- Developer Centric
- Ecosystem enabler
- Fast startup

## What is Cloud Native?

Cloud-native is an approach to building and running applications that exploits
the advantages of the cloud computing delivery model that are built using
multiple, independent microservices.

DevOps drives the patterns of high performing organizations delivering software
faster, consistently and reliably at scale

Leveraging automation to improve human performance in a high trust culture,
moving faster and safer with confidence and operational excellence

### Cloud Native Applications

- **The Twelve-Factor App** describes patterns for cloudnative architectures
  which leverage microservices.
- Applications are designed as a collection of stateless microservices.
- State is maintained in separate databases and persistent object stores.
- Resilience and horizontal scaling is achieved through deploying multiple
  instances.
- Failing instances are killed and re-spawned, not debugged and patched.
- DevOps pipelines help manage continuous delivery of services

## What are Microservices?

"…the microservice architectural style is an approach to developing a single
application as a **suite of small services**, each **running in its own
process** and communicating with lightweight mechanisms, often an HTTP resource
API. These services are **built around business capabilities** and
**independently deployable** by fully automated deployment machinery."

by Martin Fowler and James Lewis

### Microservice Architecture

An architecture style aimed to achieve flexibility, resiliency and control,
based on the following principles:

- Single purpose Loose Coupling bounded context
- Independent life cycle: developed, deployed and scaled... and hopefully, fail
  independently
- Design for resiliency and owns it’s own data
- Polyglot — independent code base
- Built by autonomous teams with end-to-end responsibility, doing Continuous
  Delivery
- Communicates with other services over a well defined API

### Advantages of Microservices

- Developed by a single team
- Developed independently
- Developed on its own timetable
- Each can be developed in a different language
- Manages its own data
- Scales and fails independently

### Microservice Challenges

- Developers must have significant operational and development skills (DevOps /
  Multiple languages)
- Service interfaces and versions
- Duplication of effort across service implementations
- Extra complexity of creating a distributed system with these issues, among
  others:
  - Network latency
  - Fault tolerance
  - Serialization
- Designing decoupled non transactional systems is difficult
- Avoiding latency of large numbers of small service invocations
- Locating service instances
- Maintaining availability and consistency with partitioned data
- End-to-end automated testing

## Monolithic vs Microservice

### Monolithic Application Deployment

- Loosely coupled
- Minimal responsibility per service
- Small Deployment units
- Easy to Scale
- Short release cycles
- Fast on-boarding for new developers
- Develop quickly with fast feedback

### Microservice Application Deployment

- Cloud Native Model
  - Multiple microservices
  - Configuration: Automated and consistent
  - Changes: Performed in DevOps Pipeline
  - Deployment: Only what changes
- Advantages for operations
  - Resiliency through redundant services
  - Consistent configuration
  - Automated massive deployment

### Example Microservice Stereotypes

- **Data services**: Responsible solely for the storage and retrieval of data
  associated with a single microservice
- **Orchestration services**: Communicate with multiple data services, either to
  store data associated with multiple microservice, or to read that data back
  and compose it into larger data structures
- **Backends-for-frontends** (**API Gateway**): Single entry point for all
  clients. May simply proxy/route to the appropriate service, or fan out to
  multiple services
- **Message bus consumers**: Consume and process messages from message buses
  such as Kafka

### Microservice Design Enables Horizontal Scaling

**Vertical Scaling**: Get bigger servers

**Horizontal Scaling**: Get bigger servers

### Monolithic vs Microservices Architectures

| Category        | Monolithic Architecture                                                                      | Microservices architecture                                                                        |
| --------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Architecture    | Built as a single logical executable                                                         | Built as a suite of small services                                                                |
| Modularity      | Based on language features                                                                   | Based on business capabilities                                                                    |
| Agility         | Changes to the system involve building and deploying a new version of the entire application | Changes can be applied to each service independently                                              |
| Scaling         | Entire application scaled when only one part is the bottleneck                               | Each service scaled independently when needed                                                     |
| Implementation  | Typically entirely developed in one programming language                                     | Each service can be developed in a different programming language                                 |
| Maintainability | Large code base is intimidating to new developers                                            | Smaller code bases easier to manage                                                               |
| Deployment      | Complex deployments with maintenance windows and scheduled downtimes                         | Simple deployment as each service can be deployed individually, with minimal if not zero downtime |

## What Does A Microservice Should Have?

- **High Cohesion** (Bounded Context around a Business Domain): Does stuff that
  needs to change together occur together?
- **Low Coupling** (Shared Nothing with Technology Agnostic API): Do you avoid
  making otherwise independent concerns dependent?
- **Low Time to Comprehension** (Small and Single Responsibility): Small enough
  for one person to understand quickly

## What Does A GOOD Microservice Should Have?

- Microservices should have minimal outside dependancies
- Business Domains usually have well established boundaries
- Microservices should be broken up by Business Domains
  - With well defined interface
  - Limiting dependancies as much as possible

## Domain Driven Design

- DDD is about designing software based on models of the underlying domain
- **Bounded Context** is a central pattern in Domain-Driven Design
- DDD deals with large models by dividing them into different Bounded Contexts
  and being explicit about their interrelationships.
