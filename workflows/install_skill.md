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
    "Successfully installed skill: ${repo_name}. You can now use the skills defined in that repository."
