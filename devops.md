---
description: Culture,  Agile Development, &  Cloud Native Technologies
---

# DevOps

DevOps is a recognition that Development and Operations needs to stop working alone in their "siloed" towers and start working together.

To do this we need:

* A **culture** of collaboration valuing openness, trust, and transparency
* An **application design** that does not require entire systems to be redeployed just to add a single function
* An **application design** that does not require entire systems to be redeployed just to add a single function
* A dynamic software-defined, **programmable platform** to continuously deploy onto

## Traditional Waterfall Development

Requirements -> Design -> Code -> Integration -> Test -> Deploy

In traditional waterfall development: 1. Each step ended when the next begins; 2. Mistakes found in the later stages are more expensive to fix; 3. No provisions for changing requirements

**Problem with this approa**c**h:**

* No provisions for changing requirements
* Because all of the teams worked separately, the development team was not always aware of operational roadblocks that might prevent the program from working as anticipated
* The people the furthest from the code who knew the least about it were deploying it into production

## Extreme Programming

In 1996, Kent Beck introduced Extreme Programming based on an interactive approach to software development. It was intended to improve software quality and responsiveness to changing customer requirements. It was one of the first agile methods.

## Agile Manifesto

In 2001, seventeen software developers met at a resort in Snowbird, Utah to discuss these lightweight development methods. Together, they published the Manifesto for Agile Software Development.

* **Individuals and interactions** over processes and tools
* **Working software** over comprehensive documentation
* **Customer collaboration** over contract negotiation
* **Responding to change** over following a plan

That is, while there is value in the items on the right, we value the items on the left more.

## Agile Development

Cycle: ... -> Requirements -> Plan -> Design -> Develop -> Release -> Track & Monitor -> ...

* Requirements and solutions evolve through the collaborative effort of **self-organizing** and **cross-functional** teams and their customers
* It advocates **adaptive planning**, evolutionary development, early delivery, and **continual improvement**
* It encourages rapid and flexible **response to change**

### **Agile Dilemma / Why Agile alone not good enough?**

While Agile improved the speed and accuracy of software for developers, it did nothing for operations. Many development team just got frustrated by ops not being able to deliver at the speed of development.

### How Agile are your teams?

* [x] Small team: 5 ± 2
* [x] Dedicated
* [x] Co-located
* [x] Cross-functional
* [x] Self managing

### Working as an Agile Team

* Iterative Sprints
* Groomed Backlogs
* Customer Stories
* 2 Week Deliverables

### Agile Antipatterns

You will fail if you...

* Lack of real Product Owner
* If your teams are too large
* If your teams and not dedicated
* If your teams are geographically distributed
* If your teams siloed
* If your teams are not self managing

## The history reminds us that DevOps is:

* From the practitioners, by practitioners
* Not a product, specification, job title
* An experience-based movement
* Decentralized and open to all

## Goal of DevOps is Agility

* Smart experimentation
* Moving in-market with maximum velocity and minimum risk
* Gaining quick valuable insight to continuously change the value proposition and quality

## DevOps Thinking / Tenets

* Social Coding
* Behavior and Test Driven Development
* Working in small batches
* Build **Minimum Viable Products** for gaining insights
* Failure leads to understanding

### Think Cloud Native

* The Twelve-Factor App describes patterns for cloud-native architectures which leverage microservices
* Applications are design as a collection of stateless microservices
* State is maintained in separate databases and persistent object stores
* Resilience and horizontal scaling is achieved through deploying multiple instances
* Failing instances are killed and re-spawned, not debugged and patched (cattle not pets)
* DevOps pipelines help manage continuous delivery of services

### Think Microservices

The microservice architectural style is an approach to developing a single application as a **suite of small services**, each **running in its own process** and communicating with lightweight mechanisms, often an HTTP resource API. These services are **built around business capabilities** and **independently deployable** by fully automated deployment machinery.

### Design for Failure

* Embrace failures: they will happen! Move from "How to avoid" —> "How to identify & what to do about it". Move from "Pure operational concern" —> "developer concern".
* External calls to other services that you don’t control are especially prone to problems:
  * Use separate thread pools
  * Time out quickly
* Circuit breaker pattern: identify problem and do something about it to avoid cascading failures
* Bulkhead pattern: Isolation from start to limit scope of failure (separate thread pools)
* Monkey testing: test by breaking (yes, on purpose! see: Netflix Chaos Monkey and Simian Army)

### Think Continuous Automation

Automation is speed + repeatability.

* Continuous Integration (CI)
* Continuous Delivery (CD)
* Build Automation
* Canary Rollouts / Blue-Green
* Failing Forward
* Application Release Automation

## Working DevOps

* Facilitate a culture of **teaming and collaboration**
* Establish **agile development** as a shared discipline
* **Automate relentlessly** to enable rapid DevOps response
* Push **smaller releases faster**, measure and remediate impact

## Taylorism

Named after the US industrial engineer Frederick Winslow Taylor (1856-1915) who in his 1911 book 'Principles Of Scientific Management' laid down the fundamental principles of large-scale manufacturing through **assembly-line** factories.

* Adoption of **Command and Control Management**: the dominant method of management in the Western world
* Organizations divided into (ostensibly) independent **functional silos**: organizations divided into (ostensibly) independent functional silos
* **Decision-making** is separated from work: managers do the planning and decide what workers should do; workers mindlessly do the tasks they are ask to accomplish

#### Taylorism is not appropriate for Craft Work:

* Taylorism may have been good during the industrial revolution, but not so much in the technology revolution
* Taylorism may have been good during the industrial revolution, but not so much in the technology revolution
* The people power requirements have been lowered
* Taylorism is not appropriate for "knowledge" work like software development

### Required DevOps behaviors

| Traditional IT practices               | DevOps                                   |
| -------------------------------------- | ---------------------------------------- |
| Organizational silos and hand-offs     | Shared ownership and high collaboration  |
| Fear of change                         | Risk management by embracing change      |
| Build once, hand crafted "snow flakes" | Ephemeral infrastructure as code         |
| Manual fulfillment                     | Automated Self Service                   |
| Alarms, call-backs, and escalations    | Feedback loops and data driven responses |

### How DevOps Manages Risk

* Deployment is king
  * Deployment must be painless
  * You have deployed the same thing several times before it gets to production
* Deployment is decoupled from activation
  * Risk is managed via activation controls (blue-green deploys with canary testing)
  * 10% of the user base, waves of activation, etc.
* Deployment is not “one size fits all”
  * It is a rail yard of interconnecting steps and microprocesses

### Ephemeral Infrastructure

* Cattle, not Pets
  * Servers are built on demand via automation
  * Logging into the server is seen as failure
* Release through parallel infrastructure
  * Build the new version on new infrastructure; stage transition between environments (zero downtime)
* Transient Infrastructure
  * Throw away when it is no longer needed
  * This eliminates entropy - a major source of failure

### Immutable Delivery

* Applications are packaged in containers
* Same container that developer runs on their laptop runs in production
* Rolling updates with immediate roll-back
* No variance limits side-effects
* Dependencies are contained

### Zero-Downtime Deployments

* Blue-green deployment is a zero-downtime deployment technique that consists of two nearly identical production environments, called Blue and Green.
* They differ by the artifacts that the developer has intentionally changed, typically by the version of the application. At any given time, at least one of the environments is active.
* Using the blue-green deployment technique, you can realize the following benefits:
  * Take software quickly from the final stage of testing to live production.
  * Deploy a new version of an application without disrupting traffic to the application.
  * Rollback rapidly. If there is something wrong with one of your environments, you can quickly switch to the other environment.

### Spotify Case Study

#### Organizational Structure

* **Squads** are grouped into Tribes (light-weight matrix)
* **Chapters** of competency areas are formed across Squads
* **Guilds** are informal light-weight community of interests across the company

#### Autonomous Squads

* Each Squad has its own mission aligned with the business
  * Feels like a "mini-startup"
  * Self Organizing / Cross-functional
  * 5-7 engineers, less than 10
* Squads have end-to-end responsibility for what they build
  * Build, commit, deploy, maintenance, operations, EVERYTHING!
  * With a long term mission usually around a single business domain

### DevOps Organizational Objective

Shared Consciousness with Distributed (local) Control

### Actions v.s. Consequences: Functional Silos Breed Bad Behavior

* Bad behavior arises when you abstract people away from the consequences of their actions.
* Functional silos abstract people away from the consequences of their actions.
* For example: By adding a QA Team, developers are abstracted away from the consequences of writing buggy code.

#### Actions have Consequences

* Make people aware of the consequences of their actions
  * Create cross-functional teams - or -
  * Have developers rotate through operations teams
  * Have operations people attend developer standups and showcases
* Make people responsible for the consequences of their actions
  * Having developers on Pager Duty, or own the SLA for the products and services they build

### DevOps Measurement / Metrics

DevOps changes the objective of the measurement from Mean Time To Failure (MTTF, make sure you never go down) -> Mean Time To Recovery (MTTR, you will go down, make sure you can recover quickly)

Metrics:

* A **BASELINE** provides a concrete number for comparison as you implement your DevOps changes:
  * It currently requires six team members 10 hours to deploy a new release of our product.
  * This costs us $X for every release
* Metric **GOALS** allow you to reason about these numbers and judge the success of your transition process:
  * Reduce deployment time from 10 hours to 2 hours.
  * Increase percentage of defects detected in testing from 25% to 50%

#### Actionable Metric Examples

* Reduce time-to-market for new features.
* Increase overall availability of the product.
* Reduce the time it takes to deploy a software release.
* Increase the percentage of defects detected in testing before production release.
* Make more efficient use of hardware infrastructure.
* Provide performance and user feedback to the product manager in a more timely manner

#### Top 4 Actionable Metric

1. Mean Lead Time: How long does it take from idea to production?
2. Release Frequency: How often can you deliver changes?
3. Change Failure Rate: How often to changes fail?
4. Mean Time to Recovery (MTTR): How quickly can you recover from failure?

#### Culture Measurements

* On my team information is actively sought
* On my team failures are learning opportunities and messengers of them are not punished
* On my team responsibilities are shared
* On my team cross functional collaboration is encouraged and rewarded
* On my team failure causes inquiry
* On my team new ideas are welcomed

#### Key metric: Cycle Time

* Cycle time is a key metric for Agile kanban teams.
* Cycle time is the amount of time it takes for a unit of work to travel through the team’s workflow–from the moment work starts to the moment it ships.
* By optimizing cycle time, the team can confidently forecast the delivery of future work.

#### Keys to High Performance

You MUST do all three:

1. Technical Practices
2. Lean Processes (Agile)
3. Culture

### Busted DevOps Myths

* You cannot buy DevOps In-A-Box
* You cannot order 20 units of DevOps for this quarter
* You cannot sprinkle DevOps on something to make it better
* You cannot become DevOps without changing your culture
* You can’t change your companies culture just by adopting new tools …but they can help reinforce it
* Using Containers won't fix your broken culture
* You cannot maintain your current organizational structure and become DevOps

### DevOps Summary

* A Cultural Movement
* Emphasizing Collaboration, Sharing, and Transparency
* Promoting Automation and Infrastructure as Code
* Achieving Continuous Integration and Delivery of Changes
* Immutable Delivery
* With One set of Metrics to rule them all

#### DevOps Maturity Matrix

| Maturity Level                    | People                                                                                                                     | Process                                                                                                                                    | Technology                                                                                                                                                             |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>Level 1: </p><p>Ad Hoc</p>     | <ul><li>Silo based</li><li>Blame and finger-pointing</li><li>Dependent on experts</li><li>Lack of accountability</li></ul> | <ul><li>Manual processes</li><li>Tribal knowledge the norm</li><li>Unpredictable and reactive</li></ul>                                    | <ul><li>Manual builds and deployments</li><li>Manual testing</li><li>Environmental inconsistencies</li></ul>                                                           |
| <p>Level 2: </p><p>Repeatable</p> | <ul><li>Manual builds and deployments</li><li>Manual testing</li><li>Environmental inconsistencies</li></ul>               | <ul><li>Processes established within silos</li><li>No standards </li><li>Can repeat what is known, but can’t react to unknowns</li></ul>   | <ul><li>Automated builds</li><li>Automated tests written as part of story development</li><li>Painful but repeatable releases</li></ul>                                |
| <p>Level 3:</p><p>Defined</p>     | <ul><li>Collaboration exists</li><li>Shared decision making</li><li>Shared accountability</li></ul>                        | <ul><li>Process automated across the software life cycle</li><li>Standards across organization</li></ul>                                   | <ul><li>Automated build and test cycle for every commit</li><li>Push button deployments</li><li>Automated user and acceptance testing</li></ul>                        |
| <p>Level 4:</p><p>Measured</p>    | Collaboration based on shared metrics with a focus on removing bottlenecks                                                 | <ul><li>Proactive monitoring</li><li>Metrics collected and analyzed against business goals</li><li>Visibility and predictability</li></ul> | <ul><li>Build metrics visible and acted on</li><li>Orchestrated deployments with automatic rollbacks</li><li>Nonfunctional requirements defined and measured</li></ul> |
| <p>Level 5:</p><p>Optimized</p>   | A culture of continuous improvement permeates through the organization                                                     | <ul><li>Self-service automation</li><li>Risk and cost optimization</li><li>High degree of experimentation</li></ul>                        | <ul><li>Zero downtime deployments</li><li>Immutable infrastructure</li><li>Actively enforce resiliency by forcing failures</li></ul>                                   |

#### Key Takeaways

* DevOps is about breaking down the silos and working as a Single Agile Team
* Culture is the #1 success factor in DevOps. Building a culture of shared responsibility, transparency and faster feedback is the foundation of every high performing DevOps team
* DevOps starts with learning how to work differently. It embraces cross-functional teams with openness, transparency, and respect as pillars
* Being able to recover quickly from failure is more important than having failures less often
* Measurements should encourage innovation and collaboration, and not punish failure (blameless culture)
