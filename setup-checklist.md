# Terminal AI Agent: Zero-to-Commit Setup & Security Checklist

Use this checklist before granting any AI agent read/write/execute access to your system.

## Phase 1: Installation & Auth
- [ ] **Use Native Installers:** Install via official curl/irm scripts (e.g., `curl https://claude.ai/install.sh`) or package managers (e.g., `npx @google/gemini-cli`), avoiding deprecated 3rd-party npm wrappers.
- [ ] **Headless Authentication:** Export API keys to environment variables (`export ANTHROPIC_API_KEY=...`) in `~/.bashrc` or `~/.zshrc` rather than storing them in project files.
- [ ] **Verify Permissions:** Ensure the terminal instance running the agent is NOT operating as `root` or `Administrator`.

## Phase 2: Repository Guardrails
- [ ] **Initialize Config:** Run the agent's initialization command (e.g., `/init`) in the project root to generate the instruction manual (e.g., `CLAUDE.md`).
- [ ] **Define Build/Test Rules:** Inside the config file, explicitly write the commands to run your linter and test suite (e.g., `npm run test`).
- [ ] **Check `.gitignore`:** Verify `.gitignore` is up to date. (Agents ingesting `node_modules` or build artifacts will instantly max out token limits and crash).
- [ ] **Disable Dangerous Bypasses:** Do not use override flags like `--dangerously-skip-permissions` unless working on a fully clean, easily revertible git branch.

## Phase 3: FinOps & Execution
- [ ] **Prompt Explicitly:** Provide exact file paths and reference your `SPEC.md` file rather than using vague, conversational prompts.
- [ ] **Monitor Spend:** Frequently run cost-tracking commands (e.g., `/cost`) to monitor the token burn of automated retry loops.
- [ ] **Truncate Memory:** Run context-clearing commands (e.g., `/compact` or `/clear`) periodically to prevent the agent from infinitely passing outdated conversation history to the LLM.
- [ ] **Commit:** Allow the agent to run the test suite, then use its native commit tool (e.g., `claude commit`) to generate an atomic, descriptive git log.
