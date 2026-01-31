---
name: consult_zero_trust_security
description: Foundational security theory, Zero Trust architecture, and rigorous quality assurance.
---

# Zero Trust Security & Information Assurance

You have access to the seminal papers and standards that define modern information security. Use these first principles to design unshakeable systems.

## 1. Foundational Theory

### The Protection of Information in Computer Systems (Saltzer & Schroeder, 1975)
*   **Core Contribution**: The 8 Design Principles of Security.
*   **Key Insight**: Security is not a feature; it is an architectural property.
    *   **Least Privilege**: Every program/user should operate using the minimum set of privileges necessary to complete the job.
    *   **Fail-Safe Defaults**: Access decisions should be based on permission rather than exclusion. (Default Deny).
    *   **Economy of Mechanism**: Keep the design as simple and small as possible. Complexity is the enemy of security.

### Reflections on Trusting Trust (Ken Thompson, 1984)
*   **Core Contribution**: Supply Chain Security.
*   **Key Insight**: You cannot trust code just because you reviewed the source. If the compiler (or build tool) is compromised, it can insert invisible backdoors.
*   **Modern Application**: This is why we use **Lockfiles** (`package-lock.json`), **Dependency Pinning**, and **Signed Commits**. Trust no artifact you didn't build yourself.

### Bell-LaPadula vs. Biba Models (1973/1977)
*   **Bell-LaPadula**: Focuses on **Confidentiality**. "No Read Up, No Write Down". (Prevents leaking secrets).
*   **Biba Model**: Focuses on **Integrity**. "No Read Down, No Write Up". (Prevents corrupting high-trust data with low-trust inputs).
*   **Application**: Distinguish whether your system protects *secrets* (Medical DB) or *truth* (Financial Ledger).

## 2. Zero Trust Architecture

### NIST SP 800-207 (Zero Trust Architecture)
*   **Definition**: "Never trust, always verify."
*   **Core Principle**: Access is determined primarily by policy, including the state of the user and device, not solely by network location.
*   **Tenet**: All communication is secured regardless of network location. The internal network is considered hostile.

### BeyondCorp (Google, 2014)
*   **Core Contribution**: The death of the VPN.
*   **Key Insight**: Perimeter security is dead. Move access controls to the application layer.
*   **Implementation**: Identify the User + Identify the Device + Context-Aware Proxy = Access Granted.

## 3. Practical Implementation (The "Zero Mess Up" Standard)

### The "Default Deny" Codebase
*   **Principle**: [Saltzer & Schroeder] Fail-Safe Defaults.
*   **Audit**: Every API route must explicitly define who *can* access it. If no header is present, return 401.

### Supply Chain Hardening
*   **Principle**: [Thompson] Trusting Trust.
*   **Action**:
    *   Run `npm audit` in CI. Fail on High/Critical.
    *   Use `npm ci` (Clean Install) to ensure exact lockfile usage.
    *   Scan for "Typosquatting" packages.

### Input Hygiene (Biba Integrity)
*   **Principle**: Low-integrity inputs (User) must not corrupt High-integrity state (Database).
*   **Action**:
    *   **OWASP A03 (Injection)**: Use Parameterized Queries (Prisma/TypeORM) exclusively.
    *   **Validation**: Parse EVERYTHING with Zod/Yup schemas at the boundary. `matches(schema)` is the only way to trust data.

### Linting & Static Analysis
*   **Rule**: `no-explicit-any`. (Types are the contract).
*   **Rule**: `react-hooks/exhaustive-deps`. (Correctness).
*   **Rule**: No `console.log` (Information Leakage).
