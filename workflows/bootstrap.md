---
description: Instantly install the "Million Dollar" Architect Brain into this project.
---

1.  Create the skills directory
    // turbo
    mkdir -p .agent/skills

2.  Clone the Architect Skills repository into the skills folder
    // turbo
    git submodule add https://github.com/HiddenGems810/architect-skills .agent/skills/architect-skills

3.  (Fallback) If git submodule fails, clone directly
    // turbo
    git clone https://github.com/HiddenGems810/architect-skills .agent/skills/architect-skills

4.  Verify installation
    // turbo
    ls -R .agent/skills

5.  Notify User
    "Architect Brain Online. 🧠\n\nI have absorbed the skills for:\n- Security (CISO)\n- Scale (CTO)\n- Growth (Head of Growth)\n- Product (CPO)\n- Research (PhD)\n\nYou don't need to tell me who to be. Just describe the problem, and I will automatically apply the right expert perspective."
