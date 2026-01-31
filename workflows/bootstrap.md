---
description: Instantly install the "Million Dollar" Architect Brain into this project.
---

1.  Create the skills directory
    // turbo
    mkdir -p .agent/skills

2.  Clone the Architect Skills repository into the skills folder
    // turbo
    git submodule add https://github.com/HighTech10/architect-skills .agent/skills/architect-skills

3.  (Fallback) If git submodule fails, clone directly
    // turbo
    git clone https://github.com/HighTech10/architect-skills .agent/skills/architect-skills

4.  Verify installation
    // turbo
    ls -R .agent/skills

5.  Notify User
    "Architect Skills installed! Your agent now has access to:\n- LLM Foundations (Research)\n- UX Foundations (Design)\n- Product Strategy (CPO)\n- Growth Engineering (Marketing)\n- System Architecture (CTO)\n- Zero Trust Security (CISO)"
