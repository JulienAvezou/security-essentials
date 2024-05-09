# security-essentials-and-role-of-devsecops
Notes from DevSecOps ch.1 Security Essentials & ch.2 Why DevSecOps

Security = prevent hijacking of online systems from attacks

Many entities require security, in particular those handling sensitive data (online banks,  government regulated medical companies, big companies like Meta, cloud providers like AWS etc)

Security measures can be enforced by Audits - compliance

The potential cost of not implementing security measures > Actual cost of implementing those security measures

Importance of securing at multiple levels

## Types of Attacks

### Phishing Attack
- targeting human vulnerability ie. fake link hiding malicious code sent in email, redirect to fake website that looks like the real one

### XSS - Cross Site Scripting
- frontend of application allows for external javascript execution as part of the application ie. send malicious code via user input field

### CSRF - Client Side Request Forgery
- make requests by pretending to be someone else ie. stealing a leaked session token
- important to properly handle revoking of credentials, tokens

### SSRF - Server Side Request Forgery
- send requests to internal resources or external systems that the server can access
- more dangerous as access to all users & admin access

### SQL Injection
- injects malicious SQL code into a database query
- risk of access to complete data, complete data deletion or updating

### Vulnerabilities in 3rd Party Libraries
- validating the vendor or library is crucial
- keep track of vulnerabilities and upgrade to versions free of vulnerabilities
- CVE = reference publicly known vulnerabilities

### Brute force
- caused by weak passwords

### DoS - Denial-of-Service
- flooding server with automatic requests to exhaust the server's resources
- mitigated via firewalls, traffic filtering for eg.

-----

## OWASP (Open Web Application Security Project) Top 10
- up-to-date industry standards & guidelines for mitigating security risks

1. Broken Access Control
- control user's permissions
- exposed by phishing, CSRF, bypassing control checks via query url params

2. Cryptographic Failures
- lack or weak cryptography (protect data at rest)
- using insecure protocols (encrypt data in transit)

3. Injection
- XSS & SQL injection types
- always validate & sanitize user input
- avoid creating templates from user input (via template engine for eg.)

4. Insecure Design
- threat modeling
- think ahead of implementation

5. Security Misconfiguration
- can happen on application config level, network config level, storage config level
- unnecessary features enabled
- unnecessary ports open
- sensitive data in error logs
- forgetting to update default passwords
- check access permission s3 bucket (public vs private)

6. Vulnerable & Outdated components

7. Identification & Authentication Failures
- can be caused by weak auth of user identity
- weak passwords
- missing MFA
- improper invalidation of user sessions or auth token

8. Software & Data Integrity Failures
- verification of components
- lack or weak digital signature

9. Security Logging & Monitoring Failures
- allows attackers to brute force and probe system without detection

10. SSRF
- need url validation
- attacker can scan for open ports and try to access sensitive files

## Layered Security
- multiple layers will make the attack more time consuming, giving more time to react to the attack and mitigate
- use variety of different tools making it more complicated for attacker
- access management to limit permissions for users - principle of least privilege

-----

## How does DevSecOps work
- reduces risk that deployment process is delayed due to security audit findings getting piled up
- integrates security within DevOps process - continuous scanning
- security as advisor (rather than police) to teach developers how to fix security issues throughout development process by leveraging automated tooling
- automated tests for application security config security etc.
  -> Static Application Security Testing (SAST)
  -> Software Composition Analysis (SCA) - goes through dependencies and checks for vulnerabilities 
  -> Dynamic Application Security Testing (DAST) - analyzing behavior and responses in real-time by simulating attacks
  -> Manual testing/Penetration testing
- to not slow down pipeline: only run basic checks, run further tests only on affected areas, only run SCA when dependencies change. Can also run comprehensive check scheduled once per day, at night time for instance when development activity is lower
- continuous Logging and Monitoring
- role to educate and build security knowledge with the help of the tooling
- take business requirements & translate into applicable security process




