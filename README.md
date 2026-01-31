# Architect Skills Repository

This repository contains utilizing specialized "Brain" skills for your AI agent, transforming it from a general coder into a "Startup in a Box" engineering and product team.

## The "Million Dollar" Stack

### 1. [consult_llm_foundations](./llm_foundations/SKILL.md)
**"The AI Researcher"**
*   **Focus**: LLM Architectures, RAG, Reasoning, MoE.
*   **Use when**: Choosing models, designing AI features, optimizing inference.

### 2. [consult_ux_foundations](./ux_foundations/SKILL.md)
**"The Senior Product Designer"**
*   **Focus**: Visual Design, Accessibility, Atomic Components.
*   **Use when**: Building UIs, ensuring premium feel, fixing usability issues.

### 3. [consult_product_strategy](./product_strategy/SKILL.md)
**"The Founder / CPO"**
*   **Focus**: Product-Market Fit, Pricing Psychology, Lean MVP.
*   **Use when**: Deciding *what* to build, how to price it, and prioritization.

### 4. [consult_growth_engineering](./growth_engineering/SKILL.md)
**"The Head of Growth"**
*   **Focus**: Viral Loops, SEO, User Acquisition, Retention.
*   **Use when**: Building onboarding flows, invite systems, or content engines.

### 5. [consult_system_architecture](./system_architecture/SKILL.md)
**"The CTO"**
*   **Focus**: Scalability, Database Choice, Security, Cloud Infra.
*   **Use when**: Setting up backends, choosing databases, planning for scale.

### 6. [consult_zero_trust_security](./zero_trust_security/SKILL.md)
**"The CISO"**
*   **Focus**: OWASP Top 10, Zero-Mess-Up Linting, Security Headers.
*   **Use when**: Auditing code, setting up auth, configuring CI/CD pipelines.

### 7. [consult_reliability_engineering](./reliability_engineering/SKILL.md)
**"The SRE"**
*   **Focus**: SLOs, Chaos Engineering, Incident Response.
*   **Use when**: Planning for high traffic, setting up monitoring, or debugging outages.

## Installation / Bootstrap

To instantly equip your agent with **ALL** these skills in any project, use the included bootstrap workflow.

### Option A: Manual Install
Run this command in your project root:
```bash
git submodule add https://github.com/HiddenGems810/architect-skills .agent/skills/architect-skills
```

### Option B: Workflow Install
Copy `workflows/bootstrap.md` to your global workflows and run:
`/bootstrap`
