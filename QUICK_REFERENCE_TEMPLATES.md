# Planning Agent Quick Reference
## Templates, Checklists, and Decision Trees

---

## SECTION 1: RAPID ASSESSMENT TEMPLATES

### Initial Request Template (Agent Use)

When receiving a user request, immediately fill out this template:

```markdown
## Initial Request Analysis

### What the User Is Asking For
- [ONE-SENTENCE SUMMARY]

### Explicitly Stated Constraints
- Traffic/Scale: [if mentioned]
- Data Requirements: [if mentioned]
- Deployment: [if mentioned]
- Compliance/Security: [if mentioned]
- Timeline: [if mentioned]
- Budget: [if mentioned]
- Team: [if mentioned]

### Critical Information Gaps
1. [GAP] - Priority: BLOCKING / HIGH / MEDIUM
2. [GAP] - Priority: BLOCKING / HIGH / MEDIUM
3. [GAP] - Priority: BLOCKING / HIGH / MEDIUM

### Recommended Next Action
☐ Proceed with clarifying questions (max 7)
☐ Request explicit assumption approval
☐ Move directly to blueprint (sufficient info)

### Clarifying Questions (if needed)
1. [QUESTION] - (critical for architecture)
2. [QUESTION] - (critical for architecture)
[... max 7 total ...]
```

---

## SECTION 2: ASSUMPTION DOCUMENTATION TEMPLATE

Use this to formally document baseline assumptions:

```markdown
## Documented Baseline Assumptions

### Scale and Performance
**Assumption 1:** Peak traffic of [X] requests per second
- **Rationale:** [Why this number]
- **User Approval:** ☐ Approved ☐ Modify to: ___

**Assumption 2:** [X] concurrent users at peak
- **Rationale:** [Why this number]
- **User Approval:** ☐ Approved ☐ Modify to: ___

**Assumption 3:** Response latency requirement: p99 < [X]ms
- **Rationale:** [Why this target]
- **User Approval:** ☐ Approved ☐ Modify to: ___

### Data Requirements
**Assumption 4:** Data volume: [X] GB initially, scaling to [Y] TB
- **Rationale:** [Estimation basis]
- **User Approval:** ☐ Approved ☐ Modify to: ___

**Assumption 5:** Consistency model: [ACID / Eventual / Hybrid]
- **Rationale:** [Why this choice]
- **User Approval:** ☐ Approved ☐ Modify to: ___

### Deployment and Operations
**Assumption 6:** Cloud provider: [AWS / GCP / Azure / Multi-cloud]
- **Rationale:** [Cost, capability, team expertise]
- **User Approval:** ☐ Approved ☐ Modify to: ___

**Assumption 7:** Target availability: [X nines] (99%, 99.9%, 99.99%)
- **Rationale:** [Business requirement]
- **User Approval:** ☐ Approved ☐ Modify to: ___

### Security and Compliance
**Assumption 8:** Compliance framework: [GDPR / HIPAA / PCI-DSS / None]
- **Rationale:** [User base location, data sensitivity]
- **User Approval:** ☐ Approved ☐ Modify to: ___

**Assumption 9:** Authentication: [OAuth2 / JWT / SAML / Internal]
- **Rationale:** [Integration requirements]
- **User Approval:** ☐ Approved ☐ Modify to: ___

### Team and Operations
**Assumption 10:** Team size: [X] engineers (expected at MVp)
- **Rationale:** [Affects operational complexity tolerance]
- **User Approval:** ☐ Approved ☐ Modify to: ___

---

## USER APPROVAL GATE

**All assumptions must be explicitly approved before proceeding to Phase 2:**

☐ I have reviewed all assumptions above
☐ The assumptions accurately reflect my project constraints
☐ I approve proceeding with these assumptions to the blueprint phase

**Signature:** _________________________ **Date:** _____________
```

---

## SECTION 3: BLUEPRINT APPROVAL CHECKLIST

Use this checklist before approving Phase 2 blueprint:

```markdown
## Blueprint Review Checklist

### Architecture Pattern Review
☐ Recommended architectural pattern is clear (Microservices / Monolithic / Event-Driven / etc.)
☐ Rationale for this pattern directly addresses my constraints
☐ I understand the tradeoffs of this pattern
☐ I have considered alternatives and understand why they were rejected

### Frontend Technology Review
☐ Rendering framework choice is justified (React / Vue / Svelte / etc.)
☐ State management approach is appropriate for my requirements
☐ Styling methodology makes sense (Tailwind / etc.)
☐ Build tool selection is explained (Vite / etc.)
☐ I'm comfortable with the frontend team expertise level required

### Backend Technology Review
☐ Primary language choice is justified (Go / Python / TypeScript / etc.)
☐ Framework selection aligns with project scale
☐ I understand the operational implications
☐ My team has or can acquire necessary expertise
☐ Migration path from current tech (if applicable) is clear

### Database Strategy Review
☐ Primary database selection is justified (PostgreSQL / MySQL / etc.)
☐ Polyglot persistence strategy makes sense (Redis, Vector DB, etc.)
☐ Data consistency model is appropriate
☐ Scaling strategy for data is feasible
☐ Backup and disaster recovery approach is acceptable

### Infrastructure Review
☐ Cloud provider choice is justified (AWS / GCP / Azure)
☐ Infrastructure as Code tool selection makes sense (Terraform / etc.)
☐ Network topology is appropriate for my constraints
☐ Security model (VPC, WAF, etc.) addresses my compliance needs
☐ Cost implications are acceptable

### Reliability and Operations
☐ Reliability patterns (Circuit Breaker, Bulkheads, etc.) are appropriate
☐ Deployment strategy (Canary / Blue-Green) is acceptable
☐ Observability approach (Sentry, DataDog, etc.) is suitable
☐ Incident response plan is adequate
☐ RTO/RPO targets are achievable

### SOLID Principles Alignment
☐ I understand how each SOLID principle applies to this architecture
☐ Service boundaries enforce Single Responsibility
☐ Components are open for extension, closed for modification
☐ Interface segregation prevents unnecessary dependencies
☐ Dependency injection enables testability and flexibility

### Testing and Quality
☐ Testing pyramid is appropriate for project scope
☐ CI/CD pipeline complexity is manageable for team size
☐ Deployment frequency target is realistic
☐ Observability and alerting strategy is sufficient
☐ Rollback procedures are clear

### Risk and Unknowns
☐ I understand the identified risks
☐ Mitigation strategies for key risks are in place
☐ Open questions are documented
☐ I'm comfortable with assumptions made

### Timeline and Resources
☐ Implementation timeline is realistic
☐ Team size can support this architecture
☐ Operational overhead is manageable
☐ Cost implications are within budget
☐ Technology licensing (if any) is accounted for

---

## APPROVAL DECISION

### Recommendation: APPROVE
**I have reviewed the blueprint and it adequately addresses my project constraints.**

### Minor Modifications Requested
**I approve the blueprint with these specific changes:**
1. [MODIFICATION]
2. [MODIFICATION]
3. [MODIFICATION]

### Major Revisions Needed
**I have significant concerns and request a revised blueprint:**
1. [CONCERN WITH REQUESTED CHANGE]
2. [CONCERN WITH REQUESTED CHANGE]
3. [CONCERN WITH REQUESTED CHANGE]

**Specific Request:** [What would you like the agent to revise?]

---

## FINAL SIGN-OFF

Approved by: _________________________ Title: _____________

Date: _________________________ 

Approval Status: ☐ APPROVED ☐ APPROVED WITH MODIFICATIONS ☐ REJECTED - REVISE
```

---

## SECTION 4: TECHNOLOGY SELECTION DECISION TREE

Use this to guide technology choices:

```
START: Choosing Technology for Component

├─ FRONTEND RENDERING
│  ├─ SEO-critical content site?
│  │  ├─ YES → Next.js (SSR/ISG excellent)
│  │  └─ NO → Continue
│  ├─ Complex interactive UI?
│  │  ├─ YES → React + Next.js (largest ecosystem)
│  │  └─ NO → Vue.js (simpler learning curve)
│  ├─ Minimal JavaScript output critical?
│  │  ├─ YES → Svelte + SvelteKit (lowest footprint)
│  │  └─ NO → Any framework acceptable
│  └─ Server-driven UI acceptable?
│     ├─ YES → HTMX (minimal JavaScript)
│     └─ NO → Framework approach required
│
├─ BACKEND LANGUAGE
│  ├─ Heavy I/O workload (APIs, WebSockets)?
│  │  ├─ YES → TypeScript/Node.js or Go
│  │  │  ├─ Full-stack TypeScript needed?
│  │  │  │  ├─ YES → TypeScript/Node.js or Bun
│  │  │  │  └─ NO → Go (better performance)
│  │  │  └─ Continue
│  │  └─ NO → Continue
│  ├─ CPU-intensive workload?
│  │  ├─ YES → Go (Goroutines) or Rust (memory safety)
│  │  └─ NO → Continue
│  ├─ AI/ML pipeline?
│  │  ├─ YES → Python (FastAPI, Django)
│  │  └─ NO → Continue
│  ├─ Enterprise Java ecosystem required?
│  │  ├─ YES → Java Spring Boot
│  │  └─ NO → Continue
│  ├─ Microsoft ecosystem locked in?
│  │  ├─ YES → C# ASP.NET Core
│  │  └─ NO → Any language acceptable
│  └─ No clear winner?
│     └─ DEFAULT: TypeScript/Node.js (fastest team velocity)
│
├─ PRIMARY DATABASE
│  ├─ Structured data with strict consistency?
│  │  ├─ YES → PostgreSQL (ACID, JSONB, features)
│  │  │  ├─ Oracle ecosystem required?
│  │  │  │  ├─ YES → Oracle Database
│  │  │  │  └─ NO → PostgreSQL (better for startups)
│  │  │  └─ Continue
│  │  └─ NO → Continue
│  ├─ Unstructured, rapidly evolving schema?
│  │  ├─ YES → MongoDB Atlas (flexibility)
│  │  └─ NO → Continue
│  ├─ Key-value, serverless preferred?
│  │  ├─ YES → DynamoDB (AWS) or Cloud Firestore
│  │  └─ NO → Continue
│  ├─ No clear winner?
│  │  └─ DEFAULT: PostgreSQL (battle-tested, feature-rich)
│  └─ Final decision: [DATABASE CHOICE]
│
├─ CACHING LAYER
│  ├─ Session management needed?
│  │  ├─ YES → Redis
│  │  └─ NO → May not need caching
│  ├─ Database query caching?
│  │  ├─ YES → Redis
│  │  └─ NO → May not need caching
│  ├─ Real-time features?
│  │  ├─ YES → Redis (pub/sub)
│  │  └─ NO → May not need caching
│  └─ Caching needed? 
│     ├─ YES → Redis (industry standard)
│     └─ NO → Skip caching layer initially
│
├─ MESSAGE BROKER / ASYNC
│  ├─ Complex event routing?
│  │  ├─ YES → RabbitMQ
│  │  └─ NO → Continue
│  ├─ Massive data pipeline?
│  │  ├─ YES → Apache Kafka (durability, scale)
│  │  └─ NO → Continue
│  ├─ Simple queue-based async?
│  │  ├─ YES → Can start with database queues, upgrade to Kafka
│  │  └─ NO → May not need async initially
│  └─ Async messaging needed?
│     ├─ YES → Kafka (if scale) or RabbitMQ (if complexity)
│     └─ NO → Skip initially, add if needed
│
├─ VECTOR DATABASE (AI/LLM)
│  ├─ LLM integrations or RAG needed?
│  │  ├─ YES → Pinecone (fully managed) or Weaviate (self-hosted)
│  │  └─ NO → Skip, not needed yet
│  └─ Vector DB decision: [YES / NO]
│
├─ CLOUD PROVIDER
│  ├─ Already invested in AWS?
│  │  ├─ YES → AWS (maximize existing investment)
│  │  └─ NO → Continue
│  ├─ AI/ML heavy, prefer GCP?
│  │  ├─ YES → GCP (VertexAI, data analytics)
│  │  └─ NO → Continue
│  ├─ Microsoft ecosystem?
│  │  ├─ YES → Azure (tight Windows integration)
│  │  └─ NO → Continue
│  ├─ Want simpler PaaS?
│  │  ├─ Frontend → Vercel (Next.js optimized)
│  │  ├─ Backend → Render, Fly.io, Supabase
│  │  └─ Continue
│  └─ No clear winner?
│     └─ DEFAULT: AWS (most comprehensive service depth)
│
└─ DECISION SUMMARY
   
   FRONTEND: [TECHNOLOGY] because [REASON]
   BACKEND: [TECHNOLOGY] because [REASON]
   DATABASE: [TECHNOLOGY] because [REASON]
   CACHE: [TECHNOLOGY] because [REASON]
   ASYNC: [TECHNOLOGY] because [REASON]
   CLOUD: [PROVIDER] because [REASON]
```

---

## SECTION 5: RAPID ARCHITECTURE PATTERN SELECTOR

Quick reference for choosing architectural pattern:

```
PATTERN SELECTION FLOW

Q: Are you a startup or established company with stable requirements?
├─ STARTUP → Consider MONOLITHIC first (simpler is better)
└─ ESTABLISHED → Continue to Q2

Q2: Do you have multiple independent teams who need autonomy?
├─ YES → MICROSERVICES (teams own services)
└─ NO → Continue to Q3

Q3: Is your system highly event-driven (lots of async workflows)?
├─ YES → EVENT-DRIVEN ARCHITECTURE
└─ NO → Continue to Q4

Q4: Do you need extreme customization or plugins?
├─ YES → MICROKERNEL (Plugin Architecture)
└─ NO → Continue to Q5

Q5: Is this a traditional web application with layers?
├─ YES → LAYERED ARCHITECTURE
└─ NO → Continue to Q6

Q6: Do you need independent scaling of different components?
├─ YES → MICROSERVICES (if you have ops maturity)
└─ NO → MONOLITHIC (simplest to operate)

---

RECOMMENDATION MATRIX:

Team Size: 1-5 people
├─ Monolithic + Layered Architecture
└─ Single cloud region, managed services

Team Size: 5-20 people
├─ Monolithic if stable requirements
├─ Microservices if independent teams
└─ Event-driven if highly async workflows

Team Size: 20+ people
├─ Microservices (team per service)
├─ Event-driven (if complex workflows)
└─ Multi-region, complex infrastructure

Startup Phase:
├─ START with Monolithic (MVP speed)
├─ ADD Microservices (if scaling needed)
└─ ADD Event-Driven (if workflow complexity)

Enterprise Rewrite:
├─ Consider Microservices (team autonomy)
├─ Consider Event-Driven (existing system complexity)
└─ Plan incremental migration (big-bang = high risk)
```

---

## SECTION 6: SOLID PRINCIPLES QUICK REFERENCE

```markdown
## Quick SOLID Verification Checklist

### Single Responsibility Principle (SRP)
For each service/component:
☐ Can I describe its responsibility in one sentence?
☐ Does it have only one reason to change?
☐ Are related concerns grouped together?
☐ Are unrelated concerns separated?

**Example Check:**
- Bad: "UserService" (handles auth, profile, permissions, billing) ❌
- Good: "UserService" (handles user identity only) ✅

### Open/Closed Principle (OCP)
☐ Can I add new features without modifying existing code?
☐ Are extensions possible via plugins or events?
☐ Would a new requirement force code changes?
☐ Are base classes/interfaces stable?

**Example Check:**
- Bad: Hardcode new notification type to OrderService ❌
- Good: New notification types subscribe to events ✅

### Liskov Substitution Principle (LSP)
☐ Can I swap implementations without breaking code?
☐ Do all subclasses honor the parent contract?
☐ Can I use v2 API where v1 was expected?
☐ Does the behavior remain predictable?

**Example Check:**
- Bad: PaymentServiceV2 returns different error codes ❌
- Good: PaymentServiceV2 is drop-in replacement ✅

### Interface Segregation Principle (ISP)
☐ Do clients depend only on methods they use?
☐ Are interfaces focused and small?
☐ Am I forcing unused dependencies?
☐ Can I split large interfaces?

**Example Check:**
- Bad: Mobile gets full 500-field User object ❌
- Good: Mobile gets only 10 required fields via BFF ✅

### Dependency Inversion Principle (DIP)
☐ Do high-level modules depend on abstractions?
☐ Is low-level code abstracted away?
☐ Can I swap implementations (DB, cache, etc.)?
☐ Am I using constructor injection for dependencies?

**Example Check:**
- Bad: OrderService contains PostgreSQL queries ❌
- Good: OrderService uses repository interface ✅
```

---

## SECTION 7: RISK ASSESSMENT MATRIX

Use this to identify and assess risks:

```markdown
## Architectural Risk Assessment

### Technology Risks
| Risk | Impact | Likelihood | Mitigation |
|------|--------|-----------|-----------|
| [TECH] not proven at our scale | HIGH | MEDIUM | Spike testing, load test plan |
| Team lacks expertise in [TECH] | MEDIUM | MEDIUM | Training plan, hiring |
| [TECH] has licensing lock-in | MEDIUM | LOW | Evaluate open alternatives |
| [TECH] community support declining | MEDIUM | LOW | Alternative language selection |

### Operational Risks
| Risk | Impact | Likelihood | Mitigation |
|------|--------|-----------|-----------|
| Kubernetes operational overhead too high | HIGH | MEDIUM | Start with simpler PaaS |
| Multi-region failover complexity | HIGH | LOW | Detailed runbook, disaster drill |
| Database migration complexity | MEDIUM | MEDIUM | Backwards-compat strategy |
| Infrastructure cost at scale | MEDIUM | MEDIUM | Regular cost review, optimization |

### Data/Security Risks
| Risk | Impact | Likelihood | Mitigation |
|------|--------|-----------|-----------|
| Data consistency issues in distributed DB | MEDIUM | MEDIUM | Saga pattern, compensation logic |
| GDPR compliance gaps | HIGH | LOW | Compliance checklist, audit |
| API security vulnerabilities | HIGH | LOW | WAF, security testing in CI/CD |
| Data loss from backup failure | HIGH | LOW | Regular backup tests, DR plan |

### Team/Delivery Risks
| Risk | Impact | Likelihood | Mitigation |
|------|--------|-----------|-----------|
| Architecture too complex for team | MEDIUM | MEDIUM | Start simpler, evolve later |
| [TECH] skill gaps | MEDIUM | MEDIUM | Hiring, training, coaching |
| Scope creep adds complexity | MEDIUM | HIGH | Strict requirements gate, design reviews |
| Timeline pressure forces bad decisions | MEDIUM | HIGH | Buffer time, phase-gate approach |

---

## RISK PRIORITY MATRIX

**Plot each risk by Impact x Likelihood:**

```
HIGH IMPACT ──────┬────────────────── CRITICAL RISKS
                  │  (Plan mitigations NOW)
                  │
MEDIUM IMPACT ────┼────────────────── MONITOR RISKS
                  │  (Have contingency plan)
                  │
LOW IMPACT ───────┴────────────────── LOW PRIORITY
       LOW    MEDIUM    HIGH
      LIKELIHOOD
```

**Top 5 Risks & Mitigations:**
1. [RISK] → [MITIGATION]
2. [RISK] → [MITIGATION]
3. [RISK] → [MITIGATION]
4. [RISK] → [MITIGATION]
5. [RISK] → [MITIGATION]
```

---

## SECTION 8: TESTING STRATEGY TEMPLATE

Use this to structure your testing pyramid:

```markdown
## Testing Strategy by Phase and SLA

### Level 1: Immediate Feedback (< 30 seconds)
**When:** On every commit  
**Tools:** Jest, pytest, GitHub Actions

- [ ] Unit tests (functions, methods)
- [ ] Static analysis (ESLint, Pylint)
- [ ] Type checking (TypeScript, mypy)
- [ ] Security scanning (SAST, dependency check)
- [ ] Code formatting (Prettier, Black)

**Target:** 80%+ code coverage

### Level 2: Fast Feedback (5-10 minutes)
**When:** On pull request creation  
**Tools:** Postman, Pact, GitHub Actions

- [ ] API contract tests
- [ ] Smoke tests (critical paths)
- [ ] Database connectivity
- [ ] Integration tests

**Target:** All critical paths covered

### Level 3: Standard Validation (15-30 minutes)
**When:** Before merge to main  
**Tools:** Mocha, pytest, GitHub Actions

- [ ] Integration tests (multi-component)
- [ ] Functional tests (business logic)
- [ ] Database transaction tests
- [ ] State consistency tests

**Target:** 60%+ coverage on core logic

### Level 4: Extended Execution (30-60 minutes)
**When:** Pre-release, nightly  
**Tools:** Playwright, Selenium, k6

- [ ] End-to-End tests (user workflows)
- [ ] Cross-browser validation
- [ ] Accessibility testing (WCAG 2.1 AA)
- [ ] Load testing (throughput, latency)
- [ ] Security testing (OWASP Top 10)

**Target:** Critical user paths 100% covered

### Coverage Targets by Component

| Component | Unit | Integration | E2E | Target |
|-----------|------|-------------|-----|--------|
| Business Logic | 90%+ | 80%+ | Critical paths | 85%+ overall |
| API Endpoints | 85%+ | 80%+ | All endpoints | 85%+ overall |
| Database Layer | 80%+ | 90%+ | Data flows | 85%+ overall |
| Frontend | 70%+ | N/A | All pages | 70%+ overall |

### Test Automation Tools

| Phase | Tool | Purpose |
|-------|------|---------|
| Unit | Jest/pytest | Function testing |
| Integration | Testcontainers | Service/database testing |
| E2E | Playwright | Browser automation |
| Load | k6/Locust | Performance testing |
| Security | OWASP ZAP | Vulnerability scanning |
| Coverage | Codecov | Coverage tracking |
```

---

## SECTION 9: DEPLOYMENT CHECKLIST

Use this before every deployment:

```markdown
## Pre-Deployment Verification Checklist

### Code Quality Gates
☐ All tests passing (unit, integration, E2E)
☐ Code coverage targets met (80%+ overall)
☐ Static analysis checks passing
☐ Security scanning clean
☐ No high/critical vulnerabilities
☐ Linting and formatting compliant

### Deployment Preparation
☐ Infrastructure provisioned and healthy
☐ Database migrations tested (forward + rollback)
☐ Environment variables configured
☐ Secrets properly managed (no plaintext)
☐ Configuration appropriate for target environment
☐ Feature flags configured for rollout strategy

### Monitoring and Alerting
☐ Application metrics configured (APM)
☐ Error tracking operational (Sentry, etc.)
☐ Log aggregation working
☐ Alert thresholds set and tested
☐ On-call team briefed on changes
☐ Runbook updated for this release

### Deployment Execution (for Canary)
☐ Deploy to 1% of traffic
☐ Monitor error rate, latency for 5 minutes
☐ Verify no anomalies detected
☐ Proceed to 10%, monitor 5 minutes
☐ Proceed to 50%, monitor 10 minutes
☐ Proceed to 100%, monitor 30 minutes

### Deployment Execution (for Blue-Green)
☐ Deploy to inactive environment (Green)
☐ Run health checks on Green environment
☐ Run smoke tests against Green
☐ Monitor Green metrics for 10 minutes
☐ Switch load balancer to Green
☐ Monitor Blue/Green switch for anomalies

### Post-Deployment
☐ Application metrics look normal
☐ No spike in error rates
☐ No latency degradation
☐ User reports no issues
☐ Database connectivity healthy
☐ External service integrations working

### Rollback Readiness
☐ Rollback procedure documented
☐ Previous version retained and available
☐ Rollback tested and practiced
☐ Command/process for rollback clear
☐ 60-second rollback SLA achievable
☐ Team understands rollback communication plan

---

## INCIDENT RESPONSE (if needed)
☐ Incident declared and severity assigned
☐ War room established (Slack channel, call)
☐ Incident commander assigned
☐ Root cause being investigated
☐ Mitigation options evaluated
☐ Rollback decision made (if applicable)
☐ Timeline and user impact communicated
```

---

## SECTION 10: APPROVAL SIGN-OFF TEMPLATES

### Phase 1 Approval (Assumptions)

```
PHASE 1 SIGN-OFF: ASSUMPTIONS AND CLARIFICATIONS

Date: _______________
Stakeholder: _________________________________

After reviewing the documented assumptions and clarifying questions:

☐ All assumptions accurately reflect my project constraints
☐ Any clarifying questions have been answered to my satisfaction
☐ I am ready to proceed to Phase 2: Blueprint Proposal

Authorized by: _________________________ Signature: ___________
```

### Phase 2 Approval (Blueprint)

```
PHASE 2 SIGN-OFF: HIGH-LEVEL BLUEPRINT

Date: _______________
Stakeholder: _________________________________

I have reviewed the proposed architecture blueprint and confirm:

☐ The architectural pattern is appropriate for my constraints
☐ Technology selections are justified and acceptable
☐ I understand the tradeoffs and implications
☐ SOLID principles alignment is clear
☐ Risk mitigation strategies are adequate
☐ I am ready to proceed to Phase 3: Detailed SDD Generation

Authorized by: _________________________ Signature: ___________

If modifications requested:
Specific requests: ___________________________________________
```

### Phase 3 Approval (Final SDD)

```
PHASE 3 SIGN-OFF: FINAL SYSTEM DESIGN DOCUMENT

Date: _______________
Stakeholder: _________________________________

I have reviewed the complete System Design Document and confirm:

☐ All components are clearly defined and justified
☐ Technology selections are specific and explained
☐ Testing and deployment strategies are comprehensive
☐ Security and compliance requirements are addressed
☐ SOLID principles are enforced throughout
☐ Assumptions and risks are documented
☐ I am ready to begin implementation with this SDD as the source of truth

Authorized by: _________________________ Signature: ___________

Implementation team lead: ____________________________________

Expected start date: __________________________________________
```

---

**Quick Reference Version:** 2026 Production-Grade  
**Last Updated:** April 2026  
**Purpose:** Provide templates and quick lookup tools for efficient planning engagement
