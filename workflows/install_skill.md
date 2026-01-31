---
description: Install a skill from a GitHub URL. Usage: /install_skill <url>
---

1.  Parse the input URL
    The user will provide a GitHub URL (e.g., https://github.com/HiddenGems810/architect-skills).
    Extract the repository name from the URL.

2.  Create the skills directory if it doesn't exist
    // turbo
    mkdir -p .agent/skills

3.  Install the repository as a submodule
    // turbo
    git submodule add ${input_url} .agent/skills/${repo_name}

4.  If submodule fails, try standard clone
    // turbo
    git clone ${input_url} .agent/skills/${repo_name}

5.  Notify User
    "Architect Brain Online. 🧠\n\nI have absorbed the skills for:\n- Security (CISO)\n- Scale (CTO)\n- Growth (Head of Growth)\n- Product (CPO)\n- Research (PhD)\n\nYou don't need to tell me who to be. Just describe the problem, and I will automatically apply the right expert perspective."
