---
description: Security and DevOps
---

# Security

## Security in a DevOps world:

Security cannot be an afterthought in DevOps

- DevOps teams need to involve Security team early for smooth deployment of new
  features
- Opportunity for greater collaboration between DevOps and Security teams
- In fact, DevOps requires this collaboration and empathy amongst teams and
  enables them by making success a joint stakeholders game

## Pull Requests provides Segregation of Duties

“Pull requests are the new segregation of duties” - Ed Bellis, Kenna Security

- Pull requests let you tell others about changes you've pushed to a repository
  on GitHub.
- Once a pull request is opened, reviewers can examine the potential changes and
  add follow- up commits before the changes are merged into the repository
- The owner of a Pull Request should never be the person that merges it to
  maintain clear segregation of duties

## DevOps Advantages for Security

- DevOps forces **tighter collaboration** with the security teams, instead of
  last-minute manual audit and reviews which were the norm befor
- Security teams must be **engaged early in the design process** to ensure
  ability to deploy continuously
- DevOps Configuration Management
  - **Standardized configurations** makes it easier to harden them
  - Standardized configurations makes it easier to diagnose when a security
    incident is in progress
  - Easier to ensure policies around secure configuration
- DevOps **Version Control** Tools: Enable easier rollback in case of issues
- DevOps as a **Compliance** Enabler: Automation (Cookbooks / Playbooks) as
  evidence of compliance, as well as documentation of policy

## Types of Security Tests Automatable in a DevOps context

- For security to be truly woven into DevOps, security tests (like all other
  tests) should be automated
- Security tests you can automate:
  - Functional Security Tests
  - Non-functional Security tests against known weaknesses
  - Security scanning of apps and infrastructure
  - Security testing application logic
- Security test automation frameworks: BDD-security, Mittn, GauntIt
- Open-sourced Cookbooks available for common security tools: Nessus, Nmap, SSH,
  openVPN, iptables, Duo 2FA

## Tools for Security in DevOps

Static Analysis, Dynamic Analysis, Fuzzing Manual Code Review, Vulnerability
Testing, Software Component Analysis, Runtime Protection, Continuous Security
Testing

### Static Analysis Tools for Security in DevOps

- Examines all code or runtime binaries to support a thorough search for common
  vulnerabilities
- Static Application Security Testing (SAST)
  - highly effective at finding flaws, even in previously (manually) reviewed
    code
  - some tools have APIs for integration into the DevOps process, and don’t
    require “code complete”
  - may require some time to fully scan code

### Dynamic Application Security Testing (DAST)

- Dynamically crawls through an app’s interface
- Tests how it reacts to various inputs
- Offers insight into how code behaves
- Helps flush out errors that other tests may not see in dynamic code paths
- Typically run against fully built applications
- Can be destructive
- May require some time to fully scan code
- Inline tests that gate a release are often run against new code only
- Full application sweeps are run in parallel to inline tests

### Fuzzing Tools for Security in DevOps

- Throw lots of random garbage at applications, and see whether it causes errors
- Has become essential to identifying misbehaving code which may be exploitable
- Con: running through a large test body of possible malicious inputs takes a
  lot of time

### Manual Code Review for Security in DevOps

- Manual reviews often catch obvious stuff that tests miss, and developers can
  miss on their only pass
- Developers ability to write security unit tests varies
- All new code should be reviewed with every Pull Request

### Vulnerability Analysis for Security in DevOps

- Vulnerability scans based on platform configuration, patch levels, or
  application composition
- Vulnerability scans may even use credentials to query for detailed application
  information
- Should span application, app stack, and the platforms that support it

### Software Component Analysis (SCA) Tools

- Hook these tools into your build or CI/CD pipeline
- Automatically inventory open source dependencies
- Identify out-of-date libraries
- Identify libraries with known security vulnerabilities
- OWASP Dependency Check:
  - Open source scanner that catalogs open source components used in an
    application
  - Works for Java, .Net, Ruby (gem spec), PHP (composer), Node.js, and Python
  - Integrates with common build tools and CI servers like Jenkins
  - Reports on any components with known vulnerabilities reported in the NIST’s
    National Vulnerability Database (NVD)
  - Gets updates from NVD data feeds

### Runtime Protection for Security in DevOps

- Runtime Application Self Protection (RASP)
- Interactive Application Self-Testing (IAST)
- Provide execution path scanning, monitoring, and embedded application white
  listing
- Runtime threat protection: Protect applications by detecting attacks in
  runtime behavior. e.g., In-memory execution monitoring, Virtualized execution
  paths, Embedded runtime libraries

### Continuous Security Testing

- Paid Penetration Testing Service (pen testing aka ethical hacking)
- Open Bug Bounty Program (popularized by Facebook, Yahoo, Google, and
  Microsoft)
- Continuous Infrastructure Scanning

## Security as Code

- Building security into DevOps tools, practices, and workflows
- Uses Continuous Delivery as the control backbone
- Uses automation engine for security and compliance

## Responsibilities of Security Organization in DevOps

Security should be woven into the DevOps framework delivering code: Security

- Security should become part of the operational process of integrating and
- Security needs to fit into DevOps, not the other way around

Security needs to be tailored to work within the automation and orchestration
model to be successful: Reduce security related bottlenecks without losing
effectiveness

### How Security Organization can help DevOps

Educate, Grow your own support, Help DevOps team understand threats, Advise on
remediation practices, Help evaluate security tools, Help with priorities, Write
tests, Advocacy

## Open Web Application Security Project (OWASP)

Top 10 List: a list of what OWASP considers the current top 10 web application
security risks worldwide. The list describes each vulnerability, provides
examples, and offers suggestions on how to avoid it. Based on data from seven
application security firms, spanning over 500,000 vulnerabilities across
hundreds of organizations. Ordering within the top 10 according to their
prevalence and their relative exploitability, detectability, and impact

### OWASP #1: Injection

- Untrusted data sent to an interpreter as part of a command/query
- SQL injection, OS injection, LDAP injection, HTTP command injection
- Works by using hostile data to trick the interpreter into executing unintended
  commands or accessing data without proper authorization
- Prevention:
  - A safe API which avoids the use of the interpreter entirely or provides a
    parameterized interface
  - Escape List or keywords or special characters to be blocked
  - Keyword list needs to be kept updated

#### Types of Injection

There are many types of injection vulnerabilities, some of the most common
include:

- SQL Injection
- Code Injection
- OS Commanding
- LDAP Injection
- XML Injection
- Path Injection
- SSI Injection
- IMAPO/SMTP Injection
- Buffer Overflow

All involve allowing untrusted or manipulated requests, commands, or queries to
be executed by a web application

#### Preventing the Weakness

- Use a vetted Library or framework (e.g., SQLAlchemy for SQL)
- Use an API which avoids the use off interpreter (parameterized)
- Run the application with minimum privileges
- Escape all special characters used by an interpreter
- Input Validation/Sanitization, white list on allowed characters

### OWASP #2: Broken Authentication and Session Management

- Incorrectly/insufficiently implemented Authentication and Session Management
  - User authentication credentials aren’t protected when stored using hashing
    or encryption
  - Credentials can be guessed or overwritten through weak account management
    functions (e.g., account creation, change password, recover password, weak
    session IDs)
  - Session IDs are exposed in the URL
  - Session IDs don’t timeout
  - Passwords, session IDs, and other credentials are sent over unencrypted
    connections
- Allows attackers to user identities by stealing passwords, keys, or session
  tokens
- Can be handled by taking authentication and session management out of the
  application into specialized technologies specifically meant for those
  purposes
- Avoid XSS flaws which can be used to steal session IDs

### OWASP #3: Sensitive Data Exposure

Many apps do not properly protect sensitive data

- Credit cards, tax IDs, authentication credentials, passwords, health records,
  and personal information
- Never send or store sensitive data stored in clear text
- Use of old / weak cryptographic algorithms
- Use of weak crypto keys generated
- Key mismanagement (keys not rotated)
- Missing browser security directives or headers when sensitive data is handled
  by browser?

All sensitive data must be encrypted at rest and in transit: Use Federal
Information Processing Standard (FIPS 140) validated cryptographic modules

#### How to Prevent Sensitive Information Exposure?

Recommendation: Scrub error messages, API calls

- Replace default server error pages with custom error pages
- Do not display file paths, IOs, serve names or stack traces in error messages
- Do not reveal implementation details or version information in error messages
  (e.g., SQL, JQuery, Java)
- Do not pass email addresses, accounts or other sensitive info in path/query of
  request (use POST body)
- Error details go in the log. Your end user doesn't want to see implementation
  details anyhow Do not include private information in logs (passwords, etc.)

### OWASP #4: XML External Entities (XXE)

- Due to older or poorly configured XML processors
- External entity references within XML documents can be used to disclose
  internal files by using
  - File URI handler
  - Remote code execution
  - Denial of Service attacks
- Mitigation
  - Avoid XML and use less complex data formats like JSON
  - Patch or upgrade all XML processors and libraries in use by app or OS
  - Disable XML External Entity processing in all XML parsers in the app

### OWASP #5: Broken Access Control

Due to:

- Lack of controls on what authenticated users are allowed to do
- Poorly implemented controls that can be easily bypassed

Attackers can exploit these flaws to access unauthorized functionality and/or
data

Mitigation to avoid these attacks:

- Access control should be enforced on server-side (not client-side)
- Deny access to functionality and data, by default
- Limit the scope of access, e.g., specific organizations and business units Log
  access control failures and alert admins upon repeated failures
- Include access control as part of unit and integration tests

### OWASP #6: Security Misconfiguration

Default server settings are often insecure or can be exploited

- Admin console is auto-installed but not removed
- Directory listing is not disabled on server
- Stack traces are returned to users, exposing underlying flaws.
- Useful for debugging, but also a gift for attackers! Sample apps (which may
  have flaws) not removed from production server

Mitigation to avoid these attacks:

- Software should be kept up to data with patches, etc.
- Security settings should be defined, implemented, and maintained Harden
  servers prior to service activation
- Run scans and do audits periodically to help detect future misconfigurations
  or missing patches

### OWASP #7: Cross-Site Scripting (XSS)

App takes untrusted data and sends it to web browser without proper validation
or escaping

- XSS allows attackers to execute scripts in the victim’s browser
  - Hijack user sessions
  - Deface web sites
  - Redirect user to malicious sites
- Typically prevented by:
  - Looking for suspicious HTTP requests/keywords that can trigger scripting
    engine: Banned HTML tags and escape sequences
  - Escape List or keywords or special characters to be blocked

### OWASP #8: Insecure Deserialization

- Serialization / Marshalling: converting a data structure into a format that
  can be stored or transmitted
- Deserialization / Unmarshalling: extracting a data structure from a series of
  bytes
- Databases, middleware, web services, network protocols all use
  serialization/deserialization
- Insecure Deserialization occurs when an app or API processes a request to
  deserialize tampered objects provided by attacker
- Mitigation to avoid these attacks:
  - Do not accept serialized objects from untrusted sources
  - Integrity checks such as digital signatures to verify source and prevent
    tampering
  - Enforcing strict type constraints on objects prior to deserialization

### OWASP #9: Using Components with Known Vulnerabilities

- Components: libraries, IDEs, frameworks, etc.
- Vulnerabilities in such components can be exploited for a range of attacks,
  resulting in data loss or server takeover
- Mitigation to avoid these risks:
  - Identify all components and the versions you are using, including all
    dependencies
  - Monitor the security of these components in public databases, project
    mailing lists, and security mailing lists
  - Keep them up to date with patches and fixes

### OWASP #10: Insufficient Logging and Monitoring

Identifying a breach took an average of 191 days [OWASP, 2016]: Plenty of time
for attacker to use a small exploit and launch a full-fledged attack

Due to:

- Lack of logging and monitoring:
  - Logins and login failures are not logged
  - No intrusion detection capabilities
- Poorly implemented logging and monitoring:
  - Logs are collected but stored locally and never aggregated
  - Poorly implemented alerting thresholds
  - Unclear log messages

Mitigation to avoid these attacks:

- Log all auditable events (logins, login failures, high-value transactions)
- Aggregate and analyze log data with Centralized Log Management
- Implement Security Incident Event Management solutions
