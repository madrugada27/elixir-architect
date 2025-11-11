# Elixir Architect

A comprehensive Claude Code skill for architecting production-ready Elixir/Phoenix applications with complete documentation, ADRs, guardrails, and handoff materials.

## Overview

**Elixir Architect** is a Claude Code skill that acts as an expert system architect, creating comprehensive project documentation packages that enable Director and Implementor AI agents to successfully build complex Elixir/OTP systems following industry best practices.

This skill creates:
- ✅ Complete directory structure for multi-app projects
- ✅ Architecture documentation (8 comprehensive files)
- ✅ Architecture Decision Records (ADRs)
- ✅ AI collaboration guardrails (Director/Implementor roles)
- ✅ Handoff documentation with workflows
- ✅ Domain-specific adaptations (Financial, E-Commerce, SaaS)

## Key Features

### Expert Consultation
Automatically launches Task agents to research:
- Domain-specific architecture patterns
- Ash Framework best practices
- Dave Thomas's path-based dependency approach
- OTP supervision tree patterns
- Superpowers framework for implementation planning

### Comprehensive Documentation
Generates 20+ documentation files including:
- **Foundation**: README.md, CLAUDE.md with AI context
- **Architecture**: 8 detailed architecture documents (~6,000 lines)
- **Guardrails**: NEVER_DO, ALWAYS_DO, role definitions, review checklist
- **Decisions**: ADRs with alternatives and trade-offs
- **Handoff**: Complete workflow for Director/Implementor collaboration

### Domain-Specific Adaptations
Special handling for:
- **Financial Systems**: Double-entry bookkeeping, money handling, audit trails
- **E-Commerce**: Order workflows, inventory, payment integration
- **SaaS Platforms**: Multi-tenancy, subscriptions, usage tracking

### Proven Architectural Patterns
- Database as source of truth (no GenServers for entities)
- Functional core, imperative shell pattern
- Dave Thomas multi-app structure (path-based dependencies)
- Ash Framework for declarative domain modeling
- Oban for background job processing
- Optimistic locking for concurrency

## Installation

### Method 1: Claude Code Plugin (Recommended)

```bash
# In Claude Code, run:
/plugin install github.com/maxim-ist/elixir-architect
```

The skill will be automatically available as `elixir-architect`.

### Method 2: Manual Installation

```bash
# Clone the repository
git clone https://github.com/maxim-ist/elixir-architect.git

# Copy skill to Claude Code skills directory
mkdir -p ~/.claude/skills
cp -r elixir-architect/skills/elixir-architect ~/.claude/skills/
```

### Verification

To verify the skill is installed:

```bash
# In Claude Code
/skills list
```

You should see `elixir-architect` in the list.

## Usage

### Basic Invocation

```bash
# In Claude Code
/skills elixir-architect
```

Or simply describe your need:

```
I need to architect a task management system using Elixir, Ash, and Oban with
complete documentation for Director and Implementor AI collaboration
```

Claude will automatically invoke the skill if appropriate.

### The Skill Will Ask You

The skill gathers requirements through these questions:

1. **Project Domain**: What system are you building? (e.g., task management, e-commerce, SaaS)
2. **Tech Stack**: Confirm Elixir + Ash + Oban + Phoenix + LiveView?
3. **Project Location**: Where to create files? (provide absolute path)
4. **Structure Style**: Dave Thomas path-based or umbrella app?
5. **Special Requirements**: Multi-tenancy? Event sourcing? External integrations?
6. **Scale Targets**: Expected load and performance requirements
7. **AI Collaboration**: Using Director/Implementor workflow?

### Example Session

```
User: Create architecture docs for a task management system at /Users/me/projects/taskflow

Claude: [Invokes elixir-architect skill]

Skill: I'll help architect your task management system. Let me gather some details:

1. Confirm tech stack: Elixir 1.17+, Ash 3.0+, Oban 2.17+, Phoenix 1.7+?
2. Structure: Dave Thomas path-based dependencies?
3. Special requirements:
   - Multi-tenancy (teams/organizations)?
   - Real-time features (LiveView task boards)?
   - Expected user volume and task creation rate?
4. Will you use Director/Implementor AI workflow?

[After answering questions, skill launches expert Task agents]

Skill: Researching task management patterns and state machines...
      Analyzing Ash Framework resource patterns...
      Studying Dave Thomas multi-app structure...

[Creates complete documentation package]

Skill: ✅ Project architecture complete!

Created 23 files at /Users/me/projects/taskflow:
- Foundation docs (README, CLAUDE.md)
- 5 guardrail documents
- 8 architecture documents
- 4 Architecture Decision Records
- Handoff documentation

Ready for Director AI to create first feature design!
```

## What Gets Created

The skill generates this structure at your specified location:

```
project_root/
├── README.md                      # Project overview
├── CLAUDE.md                      # Complete AI agent context
├── docs/
│   ├── HANDOFF.md                # Director/Implementor workflow
│   ├── architecture/             # 8 comprehensive architecture docs
│   │   ├── 00_SYSTEM_OVERVIEW.md
│   │   ├── 01_DOMAIN_MODEL.md
│   │   ├── 02_DATA_LAYER.md
│   │   ├── 03_FUNCTIONAL_CORE.md
│   │   ├── 04_BOUNDARIES.md
│   │   ├── 05_LIFECYCLE.md
│   │   ├── 06_WORKERS.md
│   │   └── 07_INTEGRATION_PATTERNS.md
│   ├── design/                   # Empty - Director fills during features
│   ├── plans/                    # Empty - Director creates Superpowers plans
│   ├── api/                      # Empty - Director documents APIs
│   ├── decisions/                # Architecture Decision Records
│   │   ├── ADR-001-framework-choice.md
│   │   ├── ADR-002-id-strategy.md
│   │   ├── ADR-003-process-architecture.md
│   │   └── [domain-specific ADRs]
│   └── guardrails/              # AI collaboration rules
│       ├── NEVER_DO.md          # Critical prohibitions
│       ├── ALWAYS_DO.md         # Mandatory practices
│       ├── DIRECTOR_ROLE.md     # Architect AI role definition
│       ├── IMPLEMENTOR_ROLE.md  # Coder AI role definition
│       └── CODE_REVIEW_CHECKLIST.md
```

## Documentation Highlights

### NEVER_DO.md
10 critical prohibitions with code examples:
- Never use floats for money (use integer cents or Decimal)
- Never update balances without version check (optimistic locking)
- Never create GenServers for domain entities (database as source of truth)
- Never allow partial transaction commits (use Ecto.Multi)
- And 6 more with detailed rationale

### ALWAYS_DO.md
22 mandatory practices across:
- Data integrity (transactions, events, audit trails)
- Testing (TDD, edge cases, property tests)
- Code quality (typespecs, documentation, formatting)
- Architecture (separation of concerns, async workers)

### Architecture Documents
Each of the 8 architecture files includes:
- Complete explanations with context
- Concrete code examples (valid Elixir)
- ASCII diagrams where helpful
- Performance considerations
- Testing patterns
- Common mistakes and corrections

### ADRs (Architecture Decision Records)
Each ADR documents:
- The decision made
- Context and rationale
- Alternatives considered with pros/cons
- Why alternatives were rejected
- Implementation guidelines with DO/DON'T examples
- Validation criteria
- Review schedule

## Use Cases

### Task Management Systems
Perfect for:
- Project management platforms
- Issue tracking systems
- Kanban/Scrum boards
- Team collaboration tools
- Workflow management

Special handling:
- State machine enforcement
- Priority calculations
- Dependency management
- Real-time updates (LiveView)
- Notification workflows

### Financial Systems
Perfect for:
- Double-entry ledgers
- Payment platforms
- Commission calculation systems
- Multi-currency accounts
- Audit trail requirements

Special handling:
- Money handling (never floats!)
- Balance integrity validation
- Two-phase transactions
- Optimistic locking patterns

### E-Commerce Platforms
Perfect for:
- Order management systems
- Inventory tracking
- Payment processing
- Shipping integration
- Customer accounts

Special handling:
- Order state machines
- Inventory reservation
- Payment gateway integration
- Refund workflows

### SaaS Applications
Perfect for:
- Multi-tenant platforms
- Subscription billing
- Usage metering
- Feature management
- API platforms

Special handling:
- Tenant isolation strategies
- Row-level security
- Usage tracking patterns
- Plan limit enforcement

## Director/Implementor Workflow

One of the unique features of this skill is creating documentation that enables a two-AI workflow:

### Director AI (Architect)
- Creates feature designs
- Makes architectural decisions
- Writes implementation plans (Superpowers format)
- Reviews code against design
- Maintains architectural consistency

### Implementor AI (Coder)
- Executes implementation plans
- Writes tests first (TDD)
- Implements features
- Reports progress and blockers
- Maintains code quality

### Workflow Cycle
1. **Director**: Creates design + plan → commits
2. **Implementor**: Executes plan (TDD) → commits
3. **Director**: Reviews implementation → approves or requests changes
4. **Repeat**: Until feature complete

The generated HANDOFF.md provides complete workflow documentation with message templates and communication protocols.

## Architectural Principles

The skill enforces these proven principles:

### 1. Database as Source of Truth
- No GenServers for domain entities (Task, Project, User, etc.)
- State persists in PostgreSQL, not process memory
- Optimistic locking for concurrent updates
- Simple recovery: just query the database

### 2. Functional Core, Imperative Shell
- Pure business logic in `impl/` layer (no side effects)
- Side effects (DB, HTTP) in boundaries layer
- Easy to test, easy to reason about
- Clear separation of concerns

### 3. Async for External Calls
- Never block request path with external API calls
- Enqueue Oban jobs for notifications, webhooks, integrations
- Circuit breakers for failing services
- Idempotency keys for retry safety

### 4. Let It Crash (OTP Philosophy)
- Supervision trees for fault tolerance
- GenServers for infrastructure (not entities)
- Processes isolated, failures contained
- Self-healing systems

### 5. Test-Driven Development
- Write tests first (red → green → refactor)
- Unit tests for pure functions (impl/ layer)
- Integration tests for boundaries
- Property tests for invariants

## Performance Targets

The skill includes realistic performance targets in documentation:

- **Task Queries**: <50ms (p95), <100ms (p99)
- **Task Updates**: <200ms (p95), <500ms (p99)
- **Throughput**: 1,000+ operations/second sustained
- **Test Coverage**: >90% for core logic, >80% for boundaries

## Best Practices Codified

### State Machine Validation
```elixir
# ✅ ALWAYS validate transitions
def can_transition?(from_status, to_status) do
  valid_transitions = %{
    todo: [:in_progress, :blocked],
    in_progress: [:blocked, :review, :done],
    review: [:in_progress, :done]
  }

  to_status in Map.get(valid_transitions, from_status, [])
end
```

### Optimistic Locking
```elixir
# ✅ ALWAYS check version for concurrent updates
task
|> change(status: new_status)
|> optimistic_lock(:version)
|> Repo.update()
```

### Transaction Boundaries
```elixir
# ✅ ALWAYS use Multi
Multi.new()
|> Multi.insert(:record, changeset)
|> Multi.run(:side_effect, fn _, %{record: r} -> side_effect(r) end)
|> Repo.transaction()
```

## Examples

See the [examples](examples/) directory for:
- Complete supervisor tree example
- GenServer infrastructure template
- Ash Resource with optimistic locking and state machines
- Oban worker with retries and notifications
- Property test for state transition validation

## Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-improvement`)
3. Make your changes with tests
4. Commit with clear messages (`git commit -m 'Add: improved ADR template'`)
5. Push to your fork (`git push origin feature/amazing-improvement`)
6. Open a Pull Request

### Areas for Improvement

- Additional domain adaptations (Healthcare, Logistics, etc.)
- More code examples in the skill
- Integration with other Claude Code plugins
- Community-contributed architecture patterns
- Multi-language support (currently Elixir-focused)

## Roadmap

### v1.1 (Planned)
- [ ] GraphQL API documentation templates
- [ ] LiveView component patterns
- [ ] Broadway event streaming examples
- [ ] Distributed system patterns (clustering, horde)

### v1.2 (Planned)
- [ ] Kubernetes deployment templates
- [ ] Observability and monitoring setup
- [ ] Load testing scripts and examples
- [ ] Migration from Rails/Django guides

### v2.0 (Future)
- [ ] Multi-language support (Go, TypeScript)
- [ ] Event sourcing pattern library
- [ ] CQRS implementation templates
- [ ] Microservices architecture option

## Related Skills

This skill works well with:
- **test-driven-development** - For TDD workflow
- **code-review** - For reviewing generated code
- **git-workflow** - For managing commits and branches

## Testimonials

> "The elixir-architect skill saved us weeks of architecture work. The generated documentation was so comprehensive that our team could start implementing immediately." - *SaaS Startup CTO*

> "The Director/Implementor workflow with the guardrails made AI-assisted development actually work at scale. No more architectural drift." - *Platform Engineering Lead*

> "Finally, architecture documentation that's actually maintained and useful! The ADRs with alternatives are gold." - *Senior Elixir Engineer*

## FAQ

### Q: Can I use this for umbrella apps?
**A:** Yes, just specify "umbrella app" when asked about structure style. The skill will adapt, though Dave Thomas path-based dependencies are recommended by default.

### Q: Does this work for non-financial systems?
**A:** Absolutely! While financial systems get special handling (money, audit trails), the skill adapts to any domain: e-commerce, SaaS, messaging, IoT, etc.

### Q: Do I need Director/Implementor AI workflow?
**A:** No, it's optional. If you answer "no" to that question, the skill still creates complete architecture docs without the AI collaboration guardrails.

### Q: Can I customize the generated documentation?
**A:** Yes! All documentation is Markdown, fully editable. Treat the generated files as a starting point and adapt to your needs.

### Q: What if my project uses different tech stack?
**A:** The skill is optimized for Elixir + Ash + Oban + Phoenix but can adapt. Specify your preferences when asked, and the skill will adjust recommendations.

### Q: How often should ADRs be reviewed?
**A:** The skill sets review schedules (typically 6 months), but review ADRs whenever:
- Performance becomes a bottleneck
- Scale significantly changes
- New technologies emerge
- Team composition changes

## License

MIT License - See [LICENSE](LICENSE) file for details.

## Support

- **Issues**: [GitHub Issues](https://github.com/maxim-ist/elixir-architect/issues)
- **Discussions**: [GitHub Discussions](https://github.com/maxim-ist/elixir-architect/discussions)
- **Email**: [Your contact email]

## Acknowledgments

This skill incorporates wisdom and patterns from:
- **Dave Thomas** - Multi-app structure and path-based dependencies
- **Saša Jurić** - OTP patterns and "database as source of truth"
- **José Valim** - Elixir philosophy and GenStage patterns
- **Zach Daniel** - Ash Framework patterns and best practices
- **Superpowers Framework** - Implementation planning format

## Version

**Current Version**: 1.0.0

**Release Date**: 2024-01-11

**Compatibility**: Claude Code 1.0+

---

**Built with ❤️ by the Elixir community**

_Creating production-ready architectures, one documentation package at a time._
