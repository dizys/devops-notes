---
description: Agile Development and Planning
---

# Agile Planning

## Problem with Tradintional Waterfall Development

{% hint style="info" %}
Requirements -> Design -> Code -> Intergration -> Test -> Deploy

* Each step ended when the next begins
* Mistakes found in the later stages are more expensive to fix
* No provisions for changing requirements
* No idea if it works until the end
{% endhint %}

* There was usually a long time between software releases
* Because all of the teams worked separately, the development team was not always aware of operational roadblocks that might prevent the program from working as anticipated
* The people the furthest from the code who knew the least about it were deploying it into production

## 12 Principles Behind the Agile Manifesto

1. Our highest priority is to satisfy the customer through early and **continuous delivery** of valuable software.
2. **Welcome changing requirements**, even late in development. Agile processes harness change for the customer's competitive advantage.
3. Deliver working software frequently, from a couple of weeks to a couple of months, with a preference to the **shorter timescale**.
4. Business people and developers must **work together** daily throughout the project.
5. Build projects around **motivated individuals**. Give them the environment and support they need, and **trust** them to get the job done.
6. The most efficient and effective method of conveying information to and within a development team is **face-to-face** conversation.
7. **Working software** is the primary measure of progress.
8. Agile processes promote **sustainable development**. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
9. Continuous attention to **technical excellence** and good design enhances agility.
10. Simplicity: the art of maximizing the amount of work not done is essential.
11. The best architectures, requirements, and designs emerge from **self-organizing teams**.
12. At regular intervals, the **team reflects** on how to become more effective, then tunes and adjusts its behavior accordingly.

## What Agile is not...

* Agile is not a new version of a waterfall SDLC, where you do legacy development in sprints
* Agile is not just the development team in each sprint, like you do in waterfall development.
* The Agile Manifesto does not include the term “agile project management” (and so there are no "project managers" in Agile)

## Agile Development

Cycle: ... -> Requirements -> Plan -> Design -> Develop -> Release -> Track & Monitor -> ...

* Requirements and solutions evolve through the collaborative effort of **self-organizing** and **cross-functional** teams and their customers
* It advocates **adaptive planning**, evolutionary development, early delivery, and **continual improvement**
* It encourages rapid and flexible **response to change**

## Agile and Scrum

**Scrum** is the most popular Agile development **framework**.

* **Agile** is a PHILOSOPHY for doing work, not prescriptive.
* **Scrum** is a METHODOLOGY for doing work that adds PROCESS to Agile thinking

### Scrum

* A management **framework** for incremental product development using one or more small cross-functional, self-organizing teams
* Provides a **structure** of roles, meetings, rules, and artifacts
* Uses fixed-length **iterations**, called Sprints, which are typically two weeks long: Scrum teams attempt to build a potentially shippable (properly tested) product increment every iteration

### Ingredients of Scrum

* Roles: Product Owner + Development Team + Scrum Master
* Artifacts: Product Backlog + Sprint Backlog + Done Increment
* Events: Sprint Planning + Daily Scrum + Sprint Review + Sprint Retrospective + Sprint

### Benefits of Scrum

Organizations that have adopted agile Scrum have experienced:

* Higher productivity
* Better-quality products
* Reduced time to market
* Improved stakeholder satisfaction
* Better team dynamics
* Happier employees

### Organization of Scrum Teams

* Small team (7 ± 2)
* Dedicated
* Co-located
* Cross-functional
* Self managing

### Scrum Roles: Product Owner, Scrum Master...

#### Product Owner

* Represents the stakeholder interests
* Responsible for **product vision**
* Final arbiter of requirements questions
* Constantly **re-prioritizes** the Product Backlog, adjusting any expectations such as release plans
* Accepts or rejects each product increment
* Decides whether to ship
* Decides whether to continue development
* May contribute as a team member

#### Scrum Master (Agile Coach)

* Facilitates the Scrum process
* Creates an environment conducive to team self-organization
* **Shields the team** from external interference and distractions to keep it "in the zone"
* Helps **resolve impediments**
* Enforces Sprint timeboxes
* Captures empirical data to adjust forecasts
* Has no management authority over the team (anyone with authority over the team is by definition not its ScrumMaster)

#### Scrum Team

* **Cross-functional** (e.g., includes members with testing skills, and often others not traditionally called developers: business analysts, domain experts, etc.)
* Self-organizing / **self-managing**, without externally assigned roles
* Consists of 5 ± 2 **dedicated co-located** collaborative members
  * Most successful when located in one team room, particularly for the first few Sprints
  * Most successful with long-term, full-time membership. Scrum moves work to a flexible learning team and avoids moving people or splitting them between teams.
* **Negotiates commitments** with the Product Owner — **one Sprint at a time**
* Has **autonomy** regarding how to reach commitments

### The Agile Dilemma

While Agile improved the speed and accuracy of software for developers, it did nothing for operations. Many development teams just got frustrated by ops not being able to deliver at the speed of development.

### Goal of Agile and DevOps are Aligned

| The Goal of Agile             | The Goals of DevOps                                                                      |
| ----------------------------- | ---------------------------------------------------------------------------------------- |
| Develop software faster       | Accelerate time to market                                                                |
| Be responsive to changes      | Improve IT’s value by more closely aligning development, IT operations, and the business |
| Obtain higher quality results | Increase IT productivity                                                                 |

### Agile Antipatterns

You will fail if you...

* Lack of real Product Owner
* If your teams are too large
* If your teams and not dedicated
* If your teams are geographically distributed
* If you teams siloed
* If your teams are not self managing

