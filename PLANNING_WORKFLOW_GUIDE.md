# Planning Agent Usage Guide and Workflow Reference
## How to Effectively Use the Autonomous Architecture Planning System

---

## QUICK START: Understanding the Three-Phase Workflow

The planning agent operates in a strictly enforced three-phase workflow designed to maximize stakeholder alignment and architectural quality.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    USER SUBMITS SOFTWARE IDEA                           │
└──────────────────────────┬──────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────────────────┐
│ PHASE 1: INTAKE & GAP ANALYSIS (5-10 minutes)                          │
│                                                                          │
│ Agent Action:                                                            │
│ • Performs immediate gap analysis of user request                       │
│ • Identifies missing constraints (traffic, data, compliance, etc.)      │
│ • Asks only MINIMUM clarifying questions (max 7)                        │
│ • OR explicitly defines baseline assumptions for user approval          │
│                                                                          │
│ User Responsibility:                                                     │
│ • Answer clarifying questions if possible                               │
│ • Approve or modify documented assumptions                              │
│                                                                          │
│ Deliverable: Gap analysis document + assumption list ready for approval │
└──────────────────────────┬──────────────────────────────────────────────┘
                           │
                           ▼
        ┌──────────────────────────────────┐
        │ User Approves Assumptions/Answers │
        │         Clarifying Questions     │
        └──────────────┬───────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────────────────────┐
│ PHASE 2: HIGH-LEVEL BLUEPRINT PROPOSAL (15-20 minutes)                 │
│                                                                          │
│ Agent Action:                                                            │
│ • Proposes three-block architecture (Frontend, Backend, Infrastructure) │
│ • Explains rationale for each technology choice                         │
│ • Identifies architectural patterns addressing constraints              │
│ • Sketches SOLID principle alignment                                    │
│ • Presents reliability and communication patterns                       │
│                                                                          │
│ User Responsibility:                                                     │
│ • Review blueprint critically                                           │
│ • Ask questions about any aspect                                        │
│ • Request modifications or alternatives                                 │
│ • Explicitly approve or request revisions                               │
│                                                                          │
│ Deliverable: High-level blueprint document with explicit approval gate  │
└──────────────────────────┬──────────────────────────────────────────────┘
                           │
                           ▼
        ┌──────────────────────────────────┐
        │ User Explicitly Approves Blueprint│
        │     (Critical Gate - No Bypass)   │
        └──────────────────────────┬───────┘
                                   │
                                   ▼
┌─────────────────────────────────────────────────────────────────────────┐
│ PHASE 3: EXHAUSTIVE SDD GENERATION (30-60 minutes)                      │
│                                                                          │
│ Agent Action:                                                            │
│ • Generates comprehensive 15-20 markdown documents                      │
│ • Details every component and communication interface                   │
│ • Specifies exact technologies, not categories                          │
│ • Provides file-by-file responsibility matrix                           │
│ • Details testing hierarchy with SLA timing                             │
│ • Specifies deployment strategy (Canary or Blue-Green)                  │
│ • Documents error handling and security architecture                    │
│ • Justifies SOLID principles across all layers                          │
│                                                                          │
│ Deliverable: Production-ready System Design Document (SDD) package      │
└──────────────────────────┬──────────────────────────────────────────────┘
                           │
                           ▼
                    READY FOR IMPLEMENTATION
                  (No architectural ambiguity)
```

---

## PHASE 1 DETAILS: INTAKE & GAP ANALYSIS

### What the Agent Will Ask

When you provide a vague software idea, expect the agent to perform a **gap analysis** looking for:

1. **Scale and Performance**
   - "What's your anticipated peak traffic (requests per second)?"
   - "Are you planning for global distribution or single-region?"
   - "What are your target latency requirements (e.g., p99 < 100ms)?"

2. **Data Requirements**
   - "What's the estimated data volume you'll manage (GB, TB, PB)?"
   - "Do you need real-time consistency or eventual consistency acceptable?"
   - "What's your data retention requirement?"

3. **Deployment and Operations**
   - "Do you have preference for cloud provider (AWS, GCP, Azure, etc.)?"
   - "Will you manage this in-house or use managed services?"
   - "What's your maximum acceptable downtime (RTO/RPO requirements)?"

4. **Security and Compliance**
   - "Are there regulatory requirements (GDPR, HIPAA, PCI-DSS)?"
   - "What's your security posture (internal tool vs. customer-facing)?"
   - "Do you have data residency requirements?"

5. **Integration Requirements**
   - "Do you need to integrate with existing systems?"
   - "Are there third-party service dependencies?"
   - "What APIs or external services will you depend on?"

6. **Team Constraints**
   - "What's your team size and technical expertise?"
   - "Do you have constraints on technology stacks?"
   - "What's your deployment frequency target?"

7. **Business Constraints**
   - "What's your timeline from planning to MVP?"
   - "What's your cost sensitivity?"
   - "What are your non-negotiable success criteria?"

### How to Respond

**Best Practice:** Answer as many questions as possible with specific numbers, not vague answers.

❌ **Vague Response:**
> "Lots of users, high traffic, needs to be secure"

✅ **Specific Response:**
> "We expect 10,000 concurrent users at peak, processing 5,000 requests per second, with p99 latency requirement of 200ms. We need GDPR compliance and AWS deployment."

### What If You Can't Answer?

If you can't provide specific answers, tell the agent something like:

> "I'm not sure about the exact traffic numbers yet. Can you proceed with reasonable baseline assumptions? I'd rather move forward with assumptions than spend more time guessing."

The agent will then **explicitly define** baseline assumptions like:

> **Assumption 1:** Assuming 10,000 requests per second at peak (enterprise SaaS scale)  
> **Assumption 2:** Assuming multi-region AWS deployment for high availability  
> **Assumption 3:** Assuming GDPR compliance required (EU user base)

You then approve or modify these assumptions before proceeding.

---

## PHASE 2 DETAILS: BLUEPRINT PROPOSAL

### What You'll Receive

The agent will present a structured blueprint containing:

1. **Three-Block Architecture Diagram**
   ```
   [Frontend Block]     [Backend Block]     [Infrastructure]
   - React + Next.js    - Go microservices  - AWS + Kubernetes
   - Tailwind CSS       - PostgreSQL        - Terraform IaC
   - Redux state mgmt   - Redis cache       - Istio service mesh
                        - Kafka events      - ELB + WAF
   ```

2. **Technology Rationale**
   - Why Go for backend: "High concurrency via Goroutines, strong type safety, native binary deployment"
   - Why PostgreSQL: "ACID compliance, JSONB support, proven at scale, rich ecosystem"
   - Why React: "Largest ecosystem, extensive third-party support, strong TypeScript integration"

3. **Pattern Justification**
   - Architectural Pattern: "Microservices architecture selected to support independent scaling of payment processing and user service"
   - Reliability Patterns: "Circuit Breaker on all external API calls, Saga pattern for distributed transactions, Bulkheads for resource isolation"

4. **SOLID Alignment (High-Level)**
   - SRP: "Payment service handles only payment logic, User service handles only user identity"
   - DIP: "Backend depends on repository abstractions, not direct database calls"

### How to Review the Blueprint

**Critical Questions to Ask:**

1. **Do the technologies make sense for YOUR constraints?**
   - "Why Kubernetes if we're a 3-person startup?"
   - "Why PostgreSQL specifically vs. other relational databases?"

2. **Are there tradeoffs you don't understand?**
   - "What's the operational burden of Kubernetes?"
   - "Could we start simpler and evolve?"

3. **Does this match your team's expertise?**
   - "Our team knows Python, not Go. What if we use Python instead?"
   - "Can you justify why this is better than simpler alternatives?"

4. **Are there missing pieces?**
   - "What about authentication? Mobile apps? Real-time notifications?"

### Requesting Modifications

You can ask for alternatives:

> "I like most of this, but I'm concerned about the operational complexity of Kubernetes. Could you propose a simplified infrastructure approach using managed services instead?"

The agent will revise the blueprint and re-present it.

### Approval Gate (CRITICAL)

**Do not let the agent proceed without your explicit approval.** Say something like:

> "I approve the blueprint with these modifications: [list any changes]. Please proceed to the detailed SDD generation."

---

## PHASE 3 DETAILS: EXHAUSTIVE SDD GENERATION

### What You'll Receive

A complete documentation package (~15-20 markdown files) containing:

#### 1. **Executive Summary**
   - What the software does
   - Scale and performance targets
   - Key business drivers
   - Documented assumptions

#### 2. **Architecture Overview**
   - High-level system diagram (Mermaid or ASCII)
   - Architectural pattern explanation
   - Component interactions

#### 3. **Frontend Block Specification**
   - Rendering framework (Next.js, Vue, etc.)
   - State management solution
   - Component hierarchy
   - Build and deployment pipeline
   - Example file structure

#### 4. **Backend Block Specification**
   - Microservice definitions (bounded contexts)
   - API contracts (OpenAPI/Swagger)
   - Database schema and models
   - Service-to-service communication
   - Error handling patterns

#### 5. **Database Strategy**
   - Primary relational database (PostgreSQL config)
   - Document store for unstructured data (MongoDB schema)
   - Vector database for AI features (Pinecone setup)
   - Caching strategy (Redis patterns)
   - Data ownership matrix

#### 6. **Infrastructure and Networking**
   - Cloud provider choice (AWS, GCP, Azure)
   - Network topology (VPC, subnets, routing)
   - Infrastructure as Code (Terraform modules)
   - Load balancing strategy
   - CDN configuration

#### 7. **Security and Compliance**
   - Authentication/authorization (OAuth2, JWT, etc.)
   - API security (rate limiting, WAF rules)
   - Data encryption (TLS, at-rest encryption)
   - Compliance checklist (GDPR, HIPAA, etc.)
   - Vulnerability scanning integration

#### 8. **API Contracts**
   - REST endpoint specifications
   - Request/response schemas
   - Error codes and handling
   - Authentication headers

#### 9. **Testing Strategy**
   - Unit testing framework and patterns
   - Integration test pyramid
   - E2E testing tools (Playwright, Cypress)
   - Load testing approach
   - Coverage targets

#### 10. **CI/CD Pipeline**
   - Commit triggers (unit tests, <30 seconds)
   - PR validation (integration tests, 5-10 min)
   - Release process (canary deployment, health checks)
   - Rollback procedures

#### 11. **Deployment Strategy**
   - **Canary Deployment** (example):
     - Deploy to 1% of traffic initially
     - Monitor error rate and latency
     - Automatically roll back if error rate > 1%
     - Gradually increase to 100% over 30 minutes

#### 12. **SOLID Principles Analysis**
   - How each principle is enforced
   - Service boundary justifications
   - Component responsibility mappings

#### 13. **Monitoring and Observability**
   - Error tracking (Sentry, etc.)
   - Application performance monitoring (Datadog, etc.)
   - Log aggregation (ELK stack)
   - Alerting thresholds and runbooks

#### 14. **Assumptions and Decisions Log**
   - Every assumption documented
   - Rationale for key decisions
   - Constraints that shaped choices

#### 15. **Open Questions and Risks**
   - Unresolved technical questions
   - Known risks and mitigations
   - Performance unknowns requiring validation

### Using the SDD

The SDD is **implementation-ready**. It should contain:

✅ Specific technology names (not "a message queue" but "Apache Kafka")  
✅ Example file structures  
✅ API contract specifications  
✅ Deployment scripts or templates  
✅ Security policies and compliance checklists  
✅ Testing requirements with coverage targets  

❌ It should NOT contain actual implementation code (unless you asked for it)

---

## COMMON INTERACTION PATTERNS

### Pattern 1: "I Don't Know the Answer"

**You say:**
> "I don't know what our peak traffic will be. Can you just assume something reasonable and move forward?"

**Agent responds:**
> "Absolutely. I'll proceed with this assumption:
> 
> **Assumption:** Assuming 5,000 requests per second at peak, scaling to 50,000 during flash sales.
> 
> Does this feel reasonable for your use case, or should I adjust it?"

### Pattern 2: "I Want a Different Technology"

**You say:**
> "I like the architecture, but we're a Python shop. Can you redo the backend using Python instead of Go?"

**Agent responds:**
> "I can absolutely revise this. Python with FastAPI will work well for your I/O-heavy microservices. The tradeoff is slightly higher operational overhead for the autoscaling thresholds since Python GIL limits true parallelism, but with async/await patterns, it's very viable.
> 
> Here's the revised blueprint..."

### Pattern 3: "I Need Clarification on a Technology Choice"

**You say:**
> "Why Kubernetes instead of AWS ECS or Heroku? What's the benefit? We're a small team."

**Agent responds:**
> "Great question. For a small team, Kubernetes would indeed be **over-engineered**. Let me revise to recommend AWS ECS (simpler, managed by AWS) or Render (even simpler, PaaS platform). This reduces your operational burden substantially.
> 
> Here's the updated blueprint with the simpler infrastructure approach..."

### Pattern 4: "This Seems Too Complex"

**You say:**
> "This blueprint seems really complex for what we're trying to do. Can you propose something simpler?"

**Agent responds:**
> "Absolutely. I was designing for enterprise-scale requirements. Let me re-baseline:
> 
> **Revised Constraints:**
> - Monolithic architecture instead of microservices (simpler deployment, easier debugging)
> - Single AWS region instead of multi-region
> - PostgreSQL only (no need for vector DB or separate cache initially)
> - Heroku or Render for hosting (managed, no Kubernetes)
> 
> This reduces operational complexity by ~70% while maintaining the ability to scale later.
> 
> Does this feel more appropriate?"

---

## BEST PRACTICES FOR EFFECTIVE PLANNING

### ✅ DO:

1. **Be Specific About Constraints**
   - Specific traffic numbers, not "lots of users"
   - Concrete compliance requirements, not "secure"
   - Real team size, not "small team"

2. **Ask Why, Not Just What**
   - "Why this technology?" (get the reasoning)
   - "What's the tradeoff?" (understand the cost)
   - "Could we do it simpler?" (challenge assumptions)

3. **Iterate Deliberately**
   - Don't approve the blueprint if you have doubts
   - Ask for revisions before proceeding
   - Use Phase 2 as your approval checkpoint

4. **Document Your Constraints**
   - Budget limitations
   - Team expertise gaps
   - Timeline pressures
   - Risk aversions

### ❌ DON'T:

1. **Skip Phase 1 Completely**
   - You lose the chance to clarify constraints
   - Assumptions get documented regardless

2. **Approve Phase 2 Hastily**
   - This is your last checkpoint before detailed design
   - Ask questions before signing off

3. **Request Major Changes in Phase 3**
   - Major pivots should happen in Phase 2
   - Phase 3 is for detailed specification, not fundamental redesign

4. **Ignore Documentation**
   - The SDD is your source of truth for implementation
   - Keep it updated as you learn more

---

## WHEN TO ENGAGE THE PLANNING AGENT

### Perfect Use Cases:

✅ **New greenfield project:** "I want to build a real-time collaborative editor"  
✅ **Major rewrite:** "We're moving from monolith to microservices"  
✅ **Complex integration:** "We need to architect a data pipeline integrating 10 third-party services"  
✅ **High-scale migration:** "We expect 100x traffic growth and need to plan for it"  
✅ **Team transition:** "New team taking over a legacy system, need architecture clarity"  

### When to Use Sparingly:

⚠️ **Simple CRUD app:** Monolithic architecture is usually fine, don't over-architect  
⚠️ **Internal tool:** Complexity should match the use case  
⚠️ **Prototype phase:** Plan, but stay flexible  

---

## SECURITY CONSIDERATIONS

The planning agent will ALWAYS include comprehensive security planning:

- **Authentication & Authorization:** Specific framework choices (OAuth2, JWT, etc.)
- **API Security:** Rate limiting, DDoS protection, WAF configuration
- **Data Protection:** Encryption at rest and in transit, database-level security
- **Compliance:** Specific regulatory mappings (GDPR article references, etc.)
- **Vulnerability Management:** Security scanning in CI/CD, dependency updates

You must explicitly review and approve the security architecture.

---

## DOCUMENTATION AND HANDOFF

After Phase 3, you'll have a complete markdown documentation package ready for:

1. **Implementation teams** to reference during coding
2. **Code reviews** to verify architectural compliance
3. **Onboarding** new team members
4. **Future refactoring** decisions
5. **Knowledge base** for the organization

The documentation is versioned and should be updated as the architecture evolves.

---

## TROUBLESHOOTING

### "The Agent Seems Stuck Asking Questions"
- Provide specific answers or explicitly request assumptions
- The agent can't proceed without clarity

### "The Blueprint Feels Misaligned"
- This is what Phase 2 is for—request revisions
- Don't approve if you have doubts

### "The SDD is Too Long/Complex"
- The agent will create appropriate documentation depth
- More detail = fewer surprises during implementation

### "I Want to Change Course Midway"
- Phase 2 approved the direction
- If you fundamentally disagree, request a revised blueprint
- Don't push forward with architectural doubt

---

## SUCCESS METRICS

Your planning engagement is successful when:

1. ✅ **Explicit stakeholder alignment** on every architectural decision
2. ✅ **Zero ambiguity** about which technologies to use and why
3. ✅ **Complete documentation** ready for implementation
4. ✅ **Documented assumptions** that can be revisited later
5. ✅ **Testing and deployment strategies** defined before coding
6. ✅ **Risk acknowledgment** with explicit mitigations
7. ✅ **SOLID principles** enforced throughout the design

---

**Framework Version:** 2026 Production-Grade  
**Last Updated:** April 2026  
**Purpose:** Enable effective collaboration between human stakeholders and autonomous architecture planning agents
