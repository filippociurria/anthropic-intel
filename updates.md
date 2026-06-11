# Anthropic Intel — Updates

Newest entries first. Managed by the intel scraper. Do not edit manually.

---

## Plugin Marketplace Search Bar — 2026-06-10
- **What**: The `/plugin` browse pane now includes a keyword search bar for filtering plugins within a marketplace, replacing scroll-only navigation
- **Situations**: quickly locating a specific plugin in a large or org-curated marketplace, filtering by keyword when browsing third-party plugin catalogs that have grown over time, reducing friction when installing plugins from busy marketplaces
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Sub-agents Spawning Sub-agents (5-Level Nesting) — 2026-06-10
- **What**: Claude Code sub-agents can now themselves spawn sub-agents, up to 5 levels deep, enabling true hierarchical multi-agent architectures within a single `claude agents` session tree
- **Situations**: orchestrating nested parallel research pipelines where each agent fans out its own sub-tasks, building hierarchical coding agents (planner → module agents → file-level agents), decomposing very large tasks across multiple tiers of parallelism beyond a single fan-out layer
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `fallbacks` Parameter for Fable 5 Refusals — 2026-06-09
- **What**: New opt-in `fallbacks` beta parameter (Claude API and Claude Platform on AWS; not supported on Message Batches API) re-runs a Fable 5 request that returned `stop_reason: "refusal"` on a specified fallback model, billed at that model's rates — so apps can continue producing output when Fable 5's safety classifiers decline a request
- **Situations**: production apps that must return a response even when Fable 5 refuses a borderline request, building tiered safety policies (e.g., Fable 5 → Opus 4.8) without custom retry logic, reducing user-visible refusal errors in high-volume consumer applications using Fable 5
- **Tags**: [dev]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Claude Fable 5 & Claude Mythos 5 — 2026-06-09
- **What**: Claude Fable 5 (`claude-fable-5`) is the most capable widely released Claude model — Mythos-class capability with safety guardrails, 1M token context, 128k max output, always-on adaptive thinking, priced at $10/$50 per MTok; Claude Mythos 5 (`claude-mythos-5`) ships simultaneously for Project Glasswing participants with the same specs; `thinking.disabled` and manual `budget_tokens` are not supported on either model (returns 400); 30-day data retention required; new `"reasoning_extraction"` `stop_details.category` fires when a request attempts to extract model weights or outputs
- **Situations**: frontier-intelligence coding, research, and long-horizon agentic tasks at roughly half the original Mythos Preview cost, large-document pipelines benefiting from 1M context and up to 128k output tokens by default, auditing integrations that pass `thinking.disabled` or manual `budget_tokens` before migrating to Fable 5
- **Tags**: [dev, product]
- **Source**: https://www.anthropic.com/news/claude-fable-5-mythos-5

## Managed Agents Scheduled Deployments — 2026-06-09
- **What**: Claude Managed Agents now supports cron-based scheduled sessions, running agent tasks on a defined schedule without requiring you to manage your own scheduler; `session.thread_*` webhook events also gain a `session_thread_id` field for correlating events across multi-agent threads
- **Situations**: running nightly data-processing or compliance-audit agents on a cron without building scheduler infrastructure, replacing cron + custom glue code with a native Managed Agents scheduling feature, routing webhook notifications per multi-agent thread in orchestration pipelines
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Managed Agents Vault Env Var Credentials — 2026-06-09
- **What**: Managed Agents vaults now support environment variable credentials, enabling secure injection of secrets into the agent sandbox for any service that authenticates via env vars (CLIs, SDKs, custom tools)
- **Situations**: giving a Managed Agent secure access to third-party CLIs or SDKs without hardcoding credentials in prompts, rotating secrets centrally in the vault without modifying agent code, extending vault support beyond OAuth to any env-var-authenticated tool
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Apple Foundation Models Framework Swift Package — 2026-06-09
- **What**: New official Swift package makes Claude available as a server-side `LanguageModel` in Apple's Foundation Models framework (iOS/iPadOS/macOS/visionOS/watchOS 27), conforming to the same `LanguageModelSession` API used for Apple's on-device model so the same session code works with either provider
- **Situations**: SwiftUI apps routing complex queries to Claude while keeping simpler ones on-device without changing session code, Apple developers benchmarking on-device vs. Claude quality within the same Swift codebase, swapping between Claude and Apple's on-device model by updating a single SPM dependency
- **Tags**: [dev]
- **Source**: https://platform.claude.com/docs/en/cli-sdks-libraries/libraries/apple-foundation-models

## Self-hosted Runner `post-session` Lifecycle Hook — 2026-06-08
- **What**: Claude Code self-hosted runner sessions gain a `post-session` hook that fires after the session ends but before the workspace is deleted, enabling snapshot of uncommitted work or log export
- **Situations**: capturing uncommitted changes before a self-hosted runner workspace is cleaned up, exporting session logs or build artifacts to an external store at the end of each run, building audit or backup pipelines for self-hosted Claude Code runner environments
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `claude agents --json` `--all` Flag + `id`/`state` Fields — 2026-06-08
- **What**: `claude agents --json` gains `--all` to include completed sessions alongside active ones; each session entry now exposes `id` and `state` fields for scripting
- **Situations**: building dashboards or scripts that query both live and recently completed background sessions, filtering or routing sessions by state in automated pipelines, referencing sessions reliably by `id` instead of parsing display names
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `disableBundledSkills` Setting — 2026-06-08
- **What**: New `disableBundledSkills` setting and `CLAUDE_CODE_DISABLE_BUNDLED_SKILLS` env var hide all bundled skills, workflows, and built-in slash commands from the model
- **Situations**: running Claude Code with only custom or team-specific slash commands visible, reducing system-prompt overhead from bundled commands the team doesn't use, building headless integrations where bundled skills introduce unwanted behavior
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `/cd` Command for Session Directory Change — 2026-06-08
- **What**: New `/cd` command moves a Claude Code session to a different working directory without breaking the prompt cache mid-session
- **Situations**: switching to a subdirectory or sibling repo mid-session without losing the prompt cache prefix, navigating project structure across multiple directories in one long session, avoiding a restart just to change context to a different folder
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## `--safe-mode` Flag — 2026-06-08
- **What**: New `--safe-mode` flag and `CLAUDE_CODE_SAFE_MODE` env var start Claude Code with all customizations disabled — CLAUDE.md, plugins, skills, hooks, and MCP servers — for clean-state troubleshooting
- **Situations**: diagnosing unexpected Claude Code behavior by isolating it from all plugins and hooks, reproducing a support issue without custom configs interfering, testing Claude Code in a clean state without project-level CLAUDE.md or MCP servers
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Hardened Cross-Session Messaging — 2026-06-06
- **What**: Messages relayed via `SendMessage` from other Claude Code sessions no longer carry user authority, preventing privilege escalation in multi-agent setups where one agent instructs another
- **Situations**: security-auditing multi-agent pipelines where agents coordinate via SendMessage but should not inherit each other's elevated permissions, enforcing strict permission boundaries across coordinating Claude Code agents, enterprise multi-agent architectures relying on subagent isolation
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `--thinking disabled` / `MAX_THINKING_TOKENS=0` — 2026-06-06
- **What**: `MAX_THINKING_TOKENS=0`, `--thinking disabled`, and the per-model thinking toggle now disable extended thinking on models that reason by default (e.g., Opus 4.8), overriding the model's default-on reasoning
- **Situations**: disabling reasoning on Opus 4.8 to cut latency and token cost for tasks that don't require deep thinking, testing model behavior with and without extended thinking in the same session, tuning cost vs. capability for high-volume pipelines using thinking-enabled models
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Glob Patterns in Deny Rules — 2026-06-06
- **What**: Glob patterns now work in deny rule tool-name positions; `"*"` denies all tools; unknown tool names in deny rules now warn at startup instead of silently passing; allow rules reject non-MCP globs
- **Situations**: writing a single deny rule that blocks all tool use in a restricted Claude Code context, catching typos in deny rules via startup warnings before they silently fail to block anything, locking down a Claude Code session to only approved MCP tools while blocking everything else
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `fallbackModel` Multi-Model Fallback Setting — 2026-06-06
- **What**: New `fallbackModel` setting in Claude Code configures up to three fallback models tried in order when the primary model is overloaded or unavailable; `--fallback-model` now also applies to interactive sessions (previously CLI-only)
- **Situations**: production Claude Code sessions needing multi-tier failover across multiple model endpoints, ensuring interactive sessions fall back gracefully when the primary model is overloaded, building resilient agentic pipelines with an explicit ordered fallback chain (e.g., Opus 4.8 → Opus 4.7 → Sonnet 4.6)
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Opus 4.1 Deprecation — 2026-06-05
- **What**: Anthropic announced deprecation of `claude-opus-4-1-20250805` with retirement on the Claude API scheduled for August 5, 2026; recommended migration target is Claude Opus 4.8
- **Situations**: auditing codebases and CI/CD pipelines for hardcoded `claude-opus-4-1` model IDs before the August deadline, planning staged migration to Opus 4.8 within the two-month window, monitoring for 400 errors after August 5 if any integration is not updated
- **Tags**: [dev]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Background Agent Sessions Auto-Update — 2026-06-04
- **What**: Background Claude Code agent sessions now automatically update to the latest Claude Code version while running in the background, without interrupting the session
- **Situations**: keeping long-running background agents on the latest version without manual restarts, avoiding version drift in persistent background sessions, ensuring background agents pick up security or bug-fix releases automatically
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `Stop`/`SubagentStop` Hook `additionalContext` Output — 2026-06-04
- **What**: `Stop` and `SubagentStop` hooks can now return `hookSpecificOutput.additionalContext` to inject structured feedback into Claude's next turn without triggering a hook error label
- **Situations**: injecting post-run diagnostics or status back into Claude's context after a session stops, giving Claude structured feedback from a Stop hook without polluting the error channel, building richer stop-event pipelines that inform Claude's next run
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `/plugin list` Command — 2026-06-04
- **What**: New `claude plugin list` command lists all installed plugins with optional `--enabled`/`--disabled` filters to quickly audit active vs. inactive plugins
- **Situations**: auditing which plugins are active across a Claude Code setup, finding disabled plugins that need re-enabling, scripting plugin inventory checks across a team environment
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `requiredMinimumVersion`/`requiredMaximumVersion` Managed Settings — 2026-06-04
- **What**: New Claude Code managed settings that refuse startup if the installed version falls outside an admin-specified min/max range, enforcing version compliance across an organization
- **Situations**: enterprises enforcing a minimum Claude Code version after a security patch, blocking overly new versions pending IT vetting, ensuring consistent Claude Code versions across large developer orgs
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Partner Network Services Track & Partner Hub — 2026-06-03
- **What**: Anthropic launched a formal three-tier Services Track (Select/Preferred/Global Premier) and a Partner Hub portal for consulting and SI firms building on Claude, with daily-refreshed qualification metrics visible to both partners and enterprise buyers
- **Situations**: enterprises finding pre-vetted Claude implementation partners by tier and region via the Partner Hub, consulting firms tracking certification count and deployed customers to qualify for tier promotions, channel partners planning their Claude practice against the January/July annual review cycle
- **Tags**: [product]
- **Source**: https://www.anthropic.com/news/services-track-partner-hub

## AI-Enabled Cyber Threats MITRE ATT&CK Analysis — 2026-06-03
- **What**: Anthropic published findings from 832 banned accounts over 12 months: the share of medium/high-risk actors using AI for cyber ops rose from 33% to 56%, with 67.3% using AI for malware writing; AI is shifting attack activity into post-compromise stages; Anthropic is in talks with MITRE to extend ATT&CK for AI-enabled techniques
- **Situations**: security teams benchmarking AI-assisted threat actor TTPs against the MITRE ATT&CK framework, defenders prioritizing post-compromise controls as AI shifts attacker focus from initial access, enterprise risk teams tracking the evolving AI threat landscape ahead of ATT&CK framework updates
- **Tags**: [research]
- **Source**: https://www.anthropic.com/news/AI-enabled-cyber-threats-mitre-attack

## `waitingFor` Field in `claude agents --json` — 2026-06-03
- **What**: `claude agents --json` now includes a `waitingFor` field indicating what a waiting session is blocked on (e.g., a pending permission prompt), enabling scripts to detect and act on stalled agents
- **Situations**: monitoring scripts that need to detect when a background agent is stuck on a permission prompt, building dashboards that distinguish active from blocked sessions, automating unblocking flows or alert escalations for stalled agentic runs
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Slash Command Autocomplete Fill (No Immediate Run) — 2026-06-03
- **What**: Clicking a slash command in the autocomplete menu now fills it into the prompt input rather than executing immediately; press Enter to run — preventing accidental immediate invocation while browsing commands
- **Situations**: previewing and editing a slash command before running it, adding arguments to a command (e.g., `/code-review high`) before execution, avoiding accidental invocations when exploring available slash commands
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Grep/Glob via `--tools` Provides Dedicated Search Tools — 2026-06-03
- **What**: Explicitly listing `Grep` or `Glob` in `--tools` on native Claude Code builds now surfaces them as dedicated first-class search tools rather than falling back to shell commands
- **Situations**: API/SDK integrations that explicitly enumerate allowed tools and need reliable native search, building restricted tool sets that include structured search without Bash, diagnosing why search behaves differently across tool-explicit vs. default sessions
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## `claude agents` Fanout Progress Display — 2026-06-02
- **What**: `claude agents` rows now show a `done/total` progress counter when work is fanned out across sub-agents; the peek view highlights the longest-running item in the batch
- **Situations**: monitoring real-time progress of parallel Claude Code workflows without opening individual session logs, identifying which sub-task is the bottleneck during a large fanned-out agentic run, tracking completion status at a glance across multi-agent refactors or batch analysis jobs
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Project Glasswing Expansion: 150 New Orgs, 15+ Countries — 2026-06-02
- **What**: Anthropic expanded Project Glasswing to ~150 new organizations across 15+ countries, prioritizing critical infrastructure sectors (power, water, healthcare, communications, hardware) that were under-represented in the initial cohort; Claude Mythos remains the tool powering vulnerability discovery
- **Situations**: critical infrastructure operators in newly added sectors seeking access to Glasswing for defensive security, tracking Anthropic's scaling of AI-assisted vulnerability discovery to ICS/OT environments, benchmarking the program's growing reach before the next application window
- **Tags**: [research, product]
- **Source**: https://www.anthropic.com/news/expanding-project-glasswing

## Advisor Tool `max_tokens` Parameter — 2026-06-02
- **What**: The advisor tool now accepts a `max_tokens` field on the tool definition to cap the advisor model's output per call, reducing latency and output token cost for workloads that don't need full-length advisor responses
- **Situations**: reducing cost and latency in high-volume agentic pipelines that pair a fast executor with an Opus advisor, capping advisor responses for tasks where a short strategic hint suffices, fine-tuning the cost/speed tradeoff when only brief advisor guidance is needed
- **Tags**: [dev, analytics]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## No Billing for Zero-Output Refusals — 2026-06-02
- **What**: The Claude API no longer charges for requests that return `stop_reason: "refusal"` with zero generated output tokens — the request is free if Claude declines before producing any content
- **Situations**: high-volume content moderation pipelines where a fraction of requests are refused before output, production apps tracking refusal rates without accruing cost from blocked requests, reducing unexpected charges when policy guardrails fire early
- **Tags**: [dev, analytics]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## `OTEL_RESOURCE_ATTRIBUTES` as Metric Labels — 2026-06-02
- **What**: `OTEL_RESOURCE_ATTRIBUTES` values are now included as labels on Claude Code metric datapoints, enabling custom dimensions (e.g., `team`, `repo`) to slice and filter usage metrics in OpenTelemetry pipelines
- **Situations**: segmenting Claude Code usage metrics by team or repository in a shared OTEL backend, building per-team cost dashboards without a separate tagging mechanism, correlating Claude Code activity with other OpenTelemetry instrumentation in the same stack
- **Tags**: [dev, analytics]
- **Source**: https://code.claude.com/docs/en/changelog

## Parallel Tool Call Independence — 2026-06-02
- **What**: A failed Bash command in Claude Code no longer cancels other tool calls in the same parallel batch — each tool now returns its own result independently, improving reliability of fanned-out tool use
- **Situations**: agentic workflows that fan out multiple Bash calls in parallel and should continue even if one fails, debugging parallel tool batches where a single bad command previously masked all results, building more resilient multi-tool pipelines that don't fail atomically
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Security Prompts for Shell Startup & Build-Config Writes — 2026-06-02
- **What**: Claude Code now shows a confirmation prompt before writing to shell startup files (`.zshenv`, `.zlogin`, `.bash_login`, `~/.config/git/`) and, in `acceptEdits` mode, before writing build-tool config files that grant code execution (`.npmrc`, `.yarnrc*`, `bunfig.toml`, `.bazelrc`, `.pre-commit-config.yaml`, `.devcontainer/`, etc.)
- **Situations**: preventing silent modification of shell startup scripts that could lead to unintended command execution, auditing what build-tool configs Claude writes in auto-approved sessions, maintaining security awareness when Claude touches files with elevated execution authority
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `ultracode` Replaces `workflow` as Dynamic Workflow Trigger — 2026-06-02
- **What**: The trigger keyword for Claude Code's dynamic multi-agent workflow mode is renamed from `workflow` to `ultracode`; typing "workflow" no longer activates it, but describing a workflow in plain language still works; the keyword is highlighted in violet in the prompt input
- **Situations**: triggering a dynamic workflow run using the new `ultracode` keyword, diagnosing why a previous "workflow" prompt no longer spawns sub-agents after upgrading, discovering the violet highlight as a visual cue that ultracode mode is active
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Edit after Grep — No Pre-Read Required — 2026-06-02
- **What**: Single-file `grep`/`egrep`/`fgrep` commands now satisfy Claude Code's read-before-edit check, so a file viewed via grep no longer requires a separate Read call before it can be edited
- **Situations**: editing a file immediately after grepping for a symbol without an extra round-trip, agentic workflows that grep then patch specific lines in one step, reducing unnecessary read operations in large codebases
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Auto Mode on Bedrock, Vertex, and Foundry — 2026-05-30
- **What**: Claude Code auto mode (background safety checks replacing interactive permission prompts) is now available for Bedrock, Vertex, and Foundry deployments on Opus 4.7 and Opus 4.8; opt in with `CLAUDE_CODE_ENABLE_AUTO_MODE=1`
- **Situations**: enterprise Bedrock/Vertex/Foundry teams enabling auto mode without needing a separate Claude API account, deploying auto mode in cloud-provider Claude Code environments for unattended agentic workflows, testing auto mode on Opus 4.8 across AWS/GCP/Azure-backed endpoints
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `--agent` Flag + `agent` Field in settings.json for Dispatched Sessions — 2026-05-29
- **What**: The `agent` field in `settings.json` is now honored for dispatched background sessions; `--agent <name>` on the CLI overrides the configured agent at launch time
- **Situations**: enforcing a named agent persona per project via settings.json so every background session uses the right config, overriding the default agent for a one-off dispatched task without editing config files, teams managing multiple specialized agent configs across different repos or monorepo subdirectories
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `OTEL_LOG_TOOL_DETAILS` for Tool Decision Telemetry — 2026-05-29
- **What**: Setting `OTEL_LOG_TOOL_DETAILS=1` causes `tool_decision` telemetry events to include full `tool_parameters` (bash commands, MCP/skill names), enabling detailed observability of Claude Code's tool calls in OpenTelemetry pipelines
- **Situations**: tracing which exact shell commands and MCP calls Claude Code executes during a session for audit logging, debugging unexpected tool invocations in long agentic runs via an OTEL backend, building per-tool usage dashboards for enterprise Claude Code observability
- **Tags**: [dev, analytics]
- **Source**: https://code.claude.com/docs/en/changelog

## Anthropic Series H: $65B Round at $965B Valuation — 2026-05-29
- **What**: Anthropic raised a $65B Series H at a $965B valuation (led by Altimeter, Dragoneer, Greenoaks, Sequoia), making it the most valuable AI startup globally and positioning it for an IPO race against OpenAI
- **Situations**: enterprise teams assessing Anthropic's long-term viability before multi-year platform commitments, tracking competitive dynamics between Claude and GPT as both companies race toward an IPO, benchmarking Anthropic's scale and financial runway for strategic planning
- **Tags**: [product]
- **Source**: https://www.thestreet.com/technology/anthropic-drops-new-claude-model-as-openai-ipo-race-heats-up

## Managed Agents Full Stack on Claude Platform on AWS — 2026-05-29
- **What**: Webhooks, multiagent orchestration, and self-hosted sandboxes for Claude Managed Agents are now available on Claude Platform on AWS, with new IAM actions and the `AnthropicSelfHostedEnvironmentAccess` managed policy
- **Situations**: AWS-native teams needing full Managed Agents orchestration (webhooks, sub-agents, custom sandboxes) under AWS billing and IAM, enterprises running self-hosted agent sandboxes on AWS for data-residency compliance, deploying multiagent workflows without a separate Anthropic account
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Auto-loading Local Plugins + `claude plugin init` — 2026-05-29
- **What**: Plugins in `.claude/skills` directories are now automatically loaded without marketplace registration; `claude plugin init <name>` scaffolds a new plugin in that directory; `/plugin` autocomplete now covers subcommands, installed plugin names, and marketplace plugins
- **Situations**: creating and testing a custom team plugin locally without publishing to a marketplace, quickly scaffolding a new skill file in a project's `.claude/skills` folder, improving discoverability of installed and marketplace plugins via autocomplete
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `EnterWorktree` Mid-Session Switch — 2026-05-29
- **What**: The `EnterWorktree` tool can now switch between Claude-managed git worktrees mid-session; worktrees are left unlocked on completion for manual cleanup via `git worktree remove`/`prune`
- **Situations**: switching between feature branches inside a single Claude Code session without restarting, managing parallel work across multiple worktrees from one conversation, cleaning up worktrees after Claude finishes without worrying about locks
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `/plugin` Discover Tab Context Pinning — 2026-05-28
- **What**: The `/plugin` Discover tab now pins plugins relevant to the current working directory at the top, annotated "suggested for this directory," so context-appropriate plugins surface first
- **Situations**: discovering the right plugin for the current project type (e.g., a Rails plugin when in a Rails repo) without browsing the full marketplace, onboarding to a new codebase and getting plugin suggestions automatically, reducing time spent searching for project-relevant tools
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Lean System Prompt as Default — 2026-05-28
- **What**: Claude Code now uses a leaner system prompt by default for all models except Claude Haiku, Sonnet, and Opus 4.7 and earlier (including Opus 4.8 and newer), reducing context overhead per turn
- **Situations**: Opus 4.8 users automatically benefiting from reduced per-turn token overhead, sessions where a smaller system prompt frees context for longer tool results and file content, diagnosing unexpected behavior changes when upgrading to Opus 4.8
- **Tags**: [dev, product]
- **Source**: https://code.claude.com/docs/en/changelog

## Stdio MCP Servers Receive Session Env Vars — 2026-05-28
- **What**: Stdio MCP servers now receive `CLAUDE_CODE_SESSION_ID` and `CLAUDECODE=1` environment variables, enabling MCP servers to identify the calling Claude Code session
- **Situations**: MCP server developers scoping per-session state or logging tied to the current Claude Code session, building session-aware MCP tools that behave differently per session, correlating MCP server logs with specific Claude Code session IDs for debugging
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Security Guidance Plugin for Claude Code — 2026-05-27
- **What**: Free first-party Claude Code plugin that scans for ~25 vulnerability classes (SQL injection, XSS, command injection, hardcoded secrets, etc.) at three levels: instant regex on file save, background model review per Claude turn, and commit-time sweep — with no model calls or cost at level 1
- **Situations**: catching injection flaws and insecure patterns before they reach a PR, running automated security review on every AI-generated code change, reducing security comments in code review (reported 30–40% reduction internally)
- **Tags**: [dev]
- **Source**: https://www.helpnetsecurity.com/2026/05/27/anthropic-claude-code-security-guidance-plugin/

## Claude Opus 4.8 — 2026-05-28
- **What**: New most-capable Claude model with sharper judgment, stronger honesty about progress, 1M token context by default, 128k max output, adaptive thinking (triggers reasoning only when needed), and improved benchmarks across agentic coding (64.3%→69.2%), reasoning, and knowledge work
- **Situations**: long-horizon agentic coding tasks requiring maximum intelligence, large-document analysis pipelines that benefit from the default 1M context window, migrating from Opus 4.7 (same $5/$25 per MTok pricing)
- **Tags**: [dev, product]
- **Source**: https://www.anthropic.com/news/claude-opus-4-8

## Mid-Conversation System Messages — 2026-05-28
- **What**: Opus 4.8 supports `role: "system"` messages at non-first positions in the `messages` array, preserving prompt cache hits when instructions change during a long-running session; no beta header required
- **Situations**: multi-turn agents that need to inject new instructions without invalidating the cache prefix, long sessions where system context evolves over time, agentic pipelines dynamically adjusting Claude's behavior mid-task without losing cached tokens
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Refusal Categories in `stop_details` — 2026-05-28
- **What**: Opus 4.8 returns fine-grained refusal categories in `stop_details` when it declines a request, allowing applications to route different refusal types to different handling logic; no beta header required
- **Situations**: production apps that need to distinguish policy refusals from capability limitations, routing blocked requests to human review vs. fallback logic, showing users context-specific messaging based on the refusal type
- **Tags**: [dev]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Fast Mode for Opus 4.8 (Research Preview) — 2026-05-28
- **What**: Opus 4.8 fast mode delivers 2.5× speed at 2× standard pricing — roughly 3× cheaper than fast mode was for Opus 4.6/4.7; research preview on the Claude API only; Max plan Claude Code users get this as the default
- **Situations**: interactive agentic workflows needing frontier intelligence with reduced latency, high-volume Claude Code sessions on Max plan where fast mode is now on by default, evaluating cost/speed tradeoffs before the fast mode waitlist opens broadly
- **Tags**: [dev, product]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Fast Mode for Opus 4.6 Deprecated — 2026-05-28
- **What**: Fast mode for Claude Opus 4.6 is deprecated with removal approximately 30 days after the May 28 Opus 4.8 launch (~June 28, 2026); migrate to Opus 4.7 or Opus 4.8 fast mode
- **Situations**: applications using `speed: "fast"` + `claude-opus-4-6` that need a migration window, auditing integrations before removal causes errors, planning upgrade timing to Opus 4.7 or 4.8 fast mode
- **Tags**: [dev]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Claude Code Workflows (Research Preview) — 2026-05-28
- **What**: Workflows let you define multi-step agentic plans; Claude can dynamically create a workflow that orchestrates up to 1,000 background sub-agents; view and manage runs with `/workflows`
- **Situations**: automating complex multi-phase coding tasks that exceed what a single agent session can handle, orchestrating parallel sub-agents for large-scale refactors or cross-repo analysis, monitoring long-running agentic pipelines via the `/workflows` dashboard
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Prompt Cache Minimum 1,024 Tokens on Opus 4.8 — 2026-05-28
- **What**: Prompt caching on Opus 4.8 requires a minimum of only 1,024 tokens (lower than on Opus 4.7), making caching accessible for shorter prompts
- **Situations**: Opus 4.8 applications with moderate-length system prompts previously below the cacheable threshold, reducing per-turn cost for multi-turn workflows where the system prompt is 1k–5k tokens, optimizing caching eligibility when migrating from Opus 4.7 to 4.8
- **Tags**: [dev, analytics]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Background Shell Commands via `! <command>` — 2026-05-28
- **What**: Type `! <command>` in a Claude Code session to launch shell commands as a new background session; equivalent to `claude --bg --exec '<command>'` from the CLI
- **Situations**: running a build or test suite in the background without blocking the current chat session, fire-and-forget deployments or scripts triggered from within Claude Code, chaining background shell jobs alongside agentic tasks
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Plugin `defaultEnabled: false` — 2026-05-28
- **What**: Plugins can declare `defaultEnabled: false` in their manifest so they install but stay inactive until a user explicitly enables them via `/plugin` or `claude plugin enable`
- **Situations**: distributing situational plugins to a team that should opt in rather than run for everyone, reducing default context overhead in shared Claude Code environments, marketplace plugins designed for specific workflows that shouldn't activate universally
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Status Line `COLUMNS`/`LINES` Env Vars — 2026-05-28
- **What**: Status line commands now receive `COLUMNS` and `LINES` environment variables so scripts can dynamically size output to the terminal width
- **Situations**: building status line scripts that adapt to narrow vs. wide terminals, displaying truncated or expanded info based on available columns, writing terminal-width-aware Claude Code status plugins
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `skipLfs` Option for Plugin Marketplace Sources — 2026-05-28
- **What**: `github`/`git` plugin marketplace sources now accept a `skipLfs: true` option to skip Git LFS downloads during clone and update operations
- **Situations**: installing plugins from repos with heavy LFS assets on slow or metered networks, speeding up plugin installs in CI/CD environments that don't need LFS content, reducing disk usage when managing plugin sources
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## macOS Background Agent Permission Persistence — 2026-05-28
- **What**: Background agents now appear as "Claude Code" in macOS Privacy & Security settings and retain their permission grants across upgrades instead of losing them on each update
- **Situations**: avoiding repeated macOS permission prompts after each Claude Code upgrade, granting background agents folder/camera/mic access once and keeping it, managing Claude Code permissions clearly in macOS System Settings
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `/code-review --fix` Apply Mode — 2026-05-27
- **What**: `/code-review --fix` now applies review findings (reuse, simplification, efficiency) directly to the working tree after the review; `/simplify` is now an alias for `/code-review --fix`
- **Situations**: automatically applying code quality suggestions from a review without manually implementing each one, using `/simplify` as a one-shot "find and apply improvements" command, pairing code review and auto-fix in a pre-commit or CI workflow
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## `disallowed-tools` Frontmatter for Skills — 2026-05-27
- **What**: Skills and slash commands can declare `disallowed-tools` in their frontmatter to remove specific tools from Claude's toolset while the skill is active
- **Situations**: creating a "read-only audit" skill that disables all write/execute tools, scoping a focused research skill to prevent accidental file modifications, building least-privilege skills for sensitive codebases
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `/reload-skills` Command — 2026-05-27
- **What**: New `/reload-skills` command re-scans skill directories and reloads all skills in the current session without requiring a restart
- **Situations**: developing or editing a custom skill file and picking up changes live, adding a new skill to a shared directory mid-session, iterating quickly on slash command definitions during skill authoring
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## `SessionStart` Hook: Session Title & Skills Reload — 2026-05-27
- **What**: `SessionStart` hooks can now set the session's terminal window title via `hookSpecificOutput.sessionTitle` on startup/resume, and return `reloadSkills: true` to re-scan skill directories so hook-installed skills are immediately available in the same session
- **Situations**: auto-labeling Claude Code sessions by branch or project name in a terminal multiplexer, installing skills from a `SessionStart` hook and making them usable without restarting, displaying context-aware window titles per repo or active task
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `MessageDisplay` Hook Event — 2026-05-27
- **What**: New `MessageDisplay` hook that fires when assistant message text is being rendered, allowing hooks to transform or suppress the displayed output before the user sees it
- **Situations**: filtering sensitive patterns from Claude's terminal output for compliance or privacy, post-processing Claude's response through a custom renderer or formatter, building redaction wrappers for regulated environments
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `pluginSuggestionMarketplaces` Managed Setting — 2026-05-27
- **What**: New enterprise managed setting that lets admins allowlist specific org marketplaces whose plugins may be proactively suggested to users via context-aware tips; plugins outside the allowlist are not suggested
- **Situations**: restricting context-aware plugin suggestions to approved internal marketplaces in enterprise deployments, preventing Claude Code from surfacing third-party plugins the org hasn't vetted, managing plugin discovery across a large developer org
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Auto Mode No Longer Requires Opt-In — 2026-05-27
- **What**: Claude Code's auto mode now activates immediately without an explicit opt-in consent prompt
- **Situations**: onboarding new users to auto mode without a friction gate, deploying auto mode in automated or headless environments where interactive prompts would block, simplifying Claude Code setup for teams rolling out auto mode org-wide
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Fallback Model Automatic Session Switch — 2026-05-27
- **What**: When the configured primary model is not found (e.g. unavailable endpoint), Claude Code now automatically switches to `--fallback-model` for the rest of the session instead of failing every request
- **Situations**: CI/CD pipelines that need resilience when a primary model endpoint is temporarily unavailable, teams with a cheaper fallback for capacity overflow, preventing long interactive sessions from breaking entirely during a model outage
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Project Glasswing: First Quantified Results — 2026-05-22
- **What**: Anthropic's Project Glasswing published its first results: Claude Mythos Preview identified 10,000+ high/critical-severity vulnerabilities across widely-used open-source software (e.g. CVE-2026-5194 in wolfSSL), with 90.6% confirmed as valid true positives by independent security firms
- **Situations**: evaluating Claude Mythos for large-scale defensive security analysis before requesting access, benchmarking AI-assisted vulnerability discovery against human researcher baselines, tracking Anthropic's cybersecurity research progress ahead of a broader Mythos release
- **Tags**: [research, dev]
- **Source**: https://www.techtimes.com/articles/317076/20260524/anthropic-moves-closer-public-claude-mythos-release-10000-critical-bugs-found-first.htm

## `/diff` Detail View Keyboard Navigation — 2026-05-22
- **What**: Claude Code's `/diff` detail pane can now be scrolled with keyboard shortcuts (arrows, `j`/`k`, `PgUp`/`PgDn`, `Space`, `Home`/`End`), replacing mouse-only navigation
- **Situations**: reviewing large multi-file diffs without leaving the keyboard, navigating diff output during terminal-only or remote sessions, power users keeping hands off the mouse during code review
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## GFM Task List Rendering in Claude Code — 2026-05-22
- **What**: Claude Code markdown output now renders GitHub Flavored Markdown task list checkboxes (`- [ ] todo` / `- [x] done`) as visual checkboxes instead of raw bullet points
- **Situations**: reading AI-generated action plans or checklists in Claude Code output, tracking multi-step todos from a Claude response at a glance, reviewing structured task breakdowns without mentally parsing `[ ]` markers
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## `/usage` Per-Category Breakdown — 2026-05-22
- **What**: `/usage` now shows a per-category breakdown of what's driving your limits usage — skills, subagents, plugins, and per-MCP-server cost
- **Situations**: identifying which plugins or subagents are consuming the most Claude Code quota, auditing per-MCP-server cost in complex tool stacks, debugging unexpected usage limit hits mid-session
- **Tags**: [dev, analytics]
- **Source**: https://code.claude.com/docs/en/changelog

## `allowAllClaudeAiMcps` Enterprise MCP Setting — 2026-05-22
- **What**: New `allowAllClaudeAiMcps` managed setting that lets enterprise Claude Code deployments load claude.ai cloud MCP connectors alongside their `managed-mcp.json` config
- **Situations**: enterprise teams combining cloud and locally-managed MCP connectors in a single Claude Code deployment, enabling claude.ai MCP servers for users under managed IT policies, expanding available MCP tools without modifying `managed-mcp.json`
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Anthropic Acquires Stainless — 2026-05-18
- **What**: Anthropic acquired Stainless (~$300M), the SDK-automation startup that auto-generates TypeScript, Python, Go, Java, and other SDKs from API specs — the same tooling used to build Anthropic's own official SDKs; Stainless is winding down its hosted SDK generator product
- **Situations**: teams relying on Stainless-hosted SDK generation planning migration before shutdown, developers tracking Anthropic's SDK quality and toolchain ownership, enterprises evaluating Anthropic's long-term developer ecosystem investment
- **Tags**: [dev, product]
- **Source**: https://www.anthropic.com/news/anthropic-acquires-stainless

## Cache Diagnostics (Public Beta) — 2026-05-13
- **What**: New public beta (`cache-diagnosis-2026-04-07` header): pass `diagnostics.previous_message_id` on a Messages request and the API returns a `cache_miss_reason` explaining where the prompt cache prefix diverged from the previous turn
- **Situations**: debugging unexpected cache misses in multi-turn production pipelines, optimizing prompt caching configuration for high-volume applications, identifying why cache isn't hitting between conversation turns
- **Tags**: [dev, analytics]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## `/code-review` Command with Effort Level — 2026-05-21
- **What**: `/simplify` renamed to `/code-review`; now accepts an optional effort level (e.g. `/code-review high`) for coarse-to-fine review thoroughness
- **Situations**: running a quick sanity check vs. a deep review in the same session, using the clearer command name in team runbooks, pairing a code review with a specific effort tier without changing global effort
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## MCP Tunnels Research Preview — 2026-05-19
- **What**: New Research Preview feature that creates a secure tunnel to connect Claude to MCP servers running inside your private network
- **Situations**: using internal company tools as MCP servers without public endpoints, accessing on-prem databases or APIs from Claude without a VPN client requirement, evaluating private-network MCP connectivity before full rollout
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Self-hosted Sandboxes for Managed Agents — 2026-05-19
- **What**: New option to run Managed Agent tool execution on your own infrastructure instead of Anthropic's sandbox
- **Situations**: enterprise teams with data-residency requirements needing tool execution on-prem, regulated industries that can't send code execution to a third-party cloud, customizing the agent sandbox beyond Anthropic's default environment
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Live MCP Config Updates for Active Managed Agent Sessions — 2026-05-19
- **What**: Managed Agent sessions can now have their MCP server and tool configurations updated while the session is still running, without a restart
- **Situations**: adding a new tool to a running agent without interruption, rotating MCP credentials mid-session, dynamically adjusting which tools are available during a long-running agentic task
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Managed Agent Large Output Auto-Spill to File — 2026-05-19
- **What**: `agent_toolset` and MCP tool outputs exceeding 100K tokens in Managed Agent sandboxes are automatically written to a sandbox file; the model gets a truncated preview with the file path and reads full content on demand
- **Situations**: agents receiving large tool responses (database dumps, long API results) without hitting context-window limits, iterating on large datasets inside Managed Agent sessions, preventing truncated tool output from breaking long agentic workflows
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## `claude agents --json` Session Listing — 2026-05-19
- **What**: New `--json` flag on `claude agents` outputs all live Claude Code sessions as structured JSON for scripting, status bars, and custom session pickers
- **Situations**: building a tmux status bar or dashboard showing active Claude sessions, scripting session management workflows with `jq`, integrating Claude session state into a custom launcher or monitoring tool
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `/plugin` Pre-Installation Details — 2026-05-19
- **What**: The `/plugin` Discover and Browse screens now show a plugin's commands, agents, skills, hooks, and MCP/LSP servers before installation
- **Situations**: evaluating exactly what a plugin adds before committing to installation, comparing two similar plugins on feature breadth, checking whether a plugin exposes MCP servers before adding it to a shared team setup
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Per-Session `/model` with `d` Default Shortcut — 2026-05-19
- **What**: `/model` now scopes the change to the current session only; pressing `d` in the model picker sets the default model for all new sessions going forward
- **Situations**: temporarily switching to a different model mid-session without affecting other open sessions, setting a preferred default model once from the picker, keeping a standard default while experimenting with a faster model in a side session
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Plugin Last-Updated Date in Marketplace — 2026-05-19
- **What**: The `/plugin` browse and discover panes now display when each plugin was last updated
- **Situations**: checking whether a plugin is actively maintained before installing it, comparing freshness of competing plugins in the marketplace, auditing for stale plugins across a team Claude Code setup
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## `/resume` Background Session Support — 2026-05-19
- **What**: Background sessions started via `claude --bg` or agent view now appear in the `/resume` picker (marked `bg`); elapsed duration is shown in background subagent completion notifications
- **Situations**: resuming a named background agent session without hunting through session history, seeing how long a background task ran before it completed, navigating between foreground and background sessions from one place
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Web Search Tool SEC Filing Data — 2026-05-18
- **What**: The web search tool now returns richer SEC filing data, grounding financial research agents, earnings analysis, and due-diligence workflows in primary sources with citations
- **Situations**: grounding a financial research agent in primary SEC filings, earnings analysis requiring cited primary sources, running API-based due-diligence workflows on public companies
- **Tags**: [dev, analytics, research]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## PowerShell Tool Default-On for Bedrock/Vertex/Foundry Windows — 2026-05-15
- **What**: PowerShell tool is now enabled by default on Windows for Bedrock, Vertex, and Foundry Claude Code users (previously opt-in), and now passes `-ExecutionPolicy Bypass` automatically (opt out with `CLAUDE_CODE_POWERSHELL_RESPECT_EXECUTION_POLICY=1`)
- **Situations**: enterprise Windows teams on Bedrock, Vertex, or Foundry gaining PowerShell support without manual opt-in, scripts that previously failed due to execution policy restrictions, standardizing PowerShell-first shell automation across cloud-provider Claude Code deployments
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Background Session `/bg` Config Flag Persistence — 2026-05-15
- **What**: `/bg` and `←`-detach now carry `--mcp-config`, `--settings`, `--add-dir`, `--plugin-dir`, `--strict-mcp-config`, `--fallback-model`, and `--allow-dangerously-skip-permissions` into background sessions; background sessions also keep their model and effort level after waking from idle
- **Situations**: detaching a session started with a custom MCP config and having the background agent keep using it, resuming a backgrounded session after sleep without losing the selected model, backgrounding tasks that need a specific fallback model or plugin directory
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Agent SDK Credits — 2026-05-14
- **What**: New separate monthly "Agent SDK credits" pool for programmatic and third-party Claude usage ($20 for Pro, $100 for Max 5x, $400 for Max 20x), effective June 15; restores access to third-party agent harnesses (OpenClaw, T3 Code, Conductor, Zed, Jean) banned from subscriptions in April
- **Situations**: developers running `claude -p` or Claude Code GitHub Actions who need to budget programmatic usage separately from chat, teams using OpenClaw or similar third-party Claude agents resuming subscription-backed usage under the new credit caps, understanding effective cost before the June 15 billing changeover
- **Tags**: [dev, automation, product]
- **Source**: https://venturebeat.com/technology/anthropic-reinstates-openclaw-and-third-party-agent-usage-on-claude-subscriptions-with-a-catch

## PwC–Anthropic Expanded Alliance — 2026-05-14
- **What**: PwC expands strategic alliance to train 30,000 staff on Claude, deploy Claude Code and Cowork firm-wide, and launch a new Office of the CFO business group built on Claude as the first standalone PwC unit anchored in Anthropic technology
- **Situations**: enterprise consulting teams evaluating Claude for large-scale deployment and certification programs, finance/CFO-office workflows seeking Claude-native tooling via PwC, organizations benchmarking Anthropic's Big Four footprint before adopting
- **Tags**: [product, analytics]
- **Source**: https://www.anthropic.com/news/pwc-expanded-partnership

## Plugin Dependency Enforcement & Cost Estimates — 2026-05-15
- **What**: `claude plugin disable` now refuses when another enabled plugin depends on the target (showing a copy-pasteable disable-chain hint); `claude plugin enable` force-enables transitive dependencies; `/plugin` marketplace browse pane now shows projected context cost (per-turn and per-invocation token estimates) per plugin
- **Situations**: safely disabling a plugin without accidentally breaking dependent plugins, understanding token/cost impact before enabling a new plugin, managing interconnected plugin dependency graphs in Claude Code
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `worktree.bgIsolation: "none"` Setting — 2026-05-15
- **What**: New Claude Code setting allowing background sessions to edit the working copy directly without creating or entering a git worktree, for repos where worktrees are impractical
- **Situations**: repos with complex build systems or CI configs that break when run inside a worktree, large monorepos where worktree creation is prohibitively slow, standardizing on direct-edit background agents across a team
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Anthropic–Gates Foundation Partnership — 2026-05-14
- **What**: Anthropic and the Gates Foundation announced a $200M commitment (grant funding, Claude usage credits, and technical support) for AI in global health, life sciences, education, and economic mobility over four years
- **Situations**: global health researchers needing Claude access for disease eradication or diagnostics work, education-equity programs building AI tooling for underserved communities, life sciences teams working on agriculture or public health applications
- **Tags**: [research, product]
- **Source**: https://www.anthropic.com/news/gates-foundation-partnership

## `claude agents` Dispatched Session Flags — 2026-05-14
- **What**: `claude agents` now accepts `--add-dir`, `--settings`, `--mcp-config`, `--plugin-dir`, `--permission-mode`, `--model`, `--effort`, and `--dangerously-skip-permissions` flags to configure each dispatched background session independently
- **Situations**: launching a background agent with a different model or effort level than the foreground session, pointing a dispatched agent at a custom MCP config or plugin directory, setting a specific permission mode per background task
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Fast Mode Now Defaults to Claude Opus 4.7 — 2026-05-12
- **What**: Fast mode (`speed: "fast"`) now supports Opus 4.7 on the API (via the `fast-mode-2026-02-01` beta header); Claude Code also updated fast mode to use Opus 4.7 by default (override with `CLAUDE_CODE_OPUS_4_6_FAST_MODE_OVERRIDE=1`)
- **Situations**: getting significantly faster Opus 4.7 output for interactive or real-time agentic workflows, upgrading from Opus 4.6 fast mode without changing integration code, combining frontier intelligence with up-to-2.5× speed at premium pricing
- **Tags**: [dev]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Claude for Small Business — 2026-05-13
- **What**: New Claude plan with pre-built connectors and ready-to-run automation workflows for QuickBooks, PayPal, HubSpot, Canva, DocuSign, Google Workspace, and Microsoft 365 covering payroll, invoicing, sales, marketing, and month-end close
- **Situations**: automating invoicing or payroll runs against QuickBooks without building a custom integration, running month-end close workflows directly from Claude, launching HubSpot or Canva-based marketing automations out of the box
- **Tags**: [product, automation, campaigns]
- **Source**: https://siliconangle.com/2026/05/13/anthropic-launches-claude-small-business-new-automation-workflows/

## Hook Desktop Notifications via `terminalSequence` — 2026-05-13
- **What**: Hooks can now emit desktop notifications, window title updates, and terminal bells by including a `terminalSequence` field in hook JSON output, even without a controlling terminal
- **Situations**: getting a desktop pop-up when a long agentic coding task completes, updating the terminal window title to show Claude's current task, triggering a bell when a file-edit or deploy hook fires
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## "Summarize up to here" in Rewind Menu — 2026-05-13
- **What**: New Rewind menu option that compresses context up to the selected point while preserving recent turns, giving finer-grained control than full session compaction
- **Situations**: freeing context window space mid-session without discarding the most recent work, archiving the early exploratory phase of a long debugging session, reducing token spend on a multi-hour task while keeping the latest tool results intact
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Background Agent Permission Mode Preservation — 2026-05-13
- **What**: Background agents launched via `/bg` or `←←` now inherit and preserve the current session's permission mode instead of reverting to the default
- **Situations**: spawning a background agent that should share the same auto-approved permissions as the foreground session, avoiding unexpected permission prompts when backgrounding tasks mid-session, maintaining consistent allow/deny rules across parallel agents
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `ANTHROPIC_WORKSPACE_ID` Env Var — 2026-05-13
- **What**: New Claude Code env var to scope a workload-identity-federation minted token to a specific workspace when the federation rule covers more than one workspace
- **Situations**: multi-workspace enterprise deployments where each team's Claude Code instance should use its own workspace budget, CI/CD pipelines using workload identity federation that need to target a specific workspace, preventing token reuse across workspace boundaries
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Platform on AWS — 2026-05-11
- **What**: Full Claude Platform (Messages API, Files API, Message Batches API, Managed Agents, Agent Skills, code execution, tool use) now available on Anthropic-managed AWS infrastructure with AWS billing and IAM authentication
- **Situations**: AWS-native teams accessing the full Managed Agents stack with IAM auth and AWS cost reporting, organizations retiring AWS commitments against Claude usage, deploying Claude code execution and web tools through native AWS endpoints without a separate Anthropic account
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

---

## `/model` Picker Gateway Support — 2026-05-01
- **What**: The `/model` picker now populates from your gateway's `/v1/models` endpoint when `ANTHROPIC_BASE_URL` points at an Anthropic-compatible gateway
- **Situations**: switching between models on a self-hosted LiteLLM or other proxy gateway, enterprise Claude Code deployments routing through an internal API gateway, browsing available gateway models without leaving Claude Code
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Code Terminal OAuth for WSL2/SSH/Containers — 2026-05-01
- **What**: `claude auth login` now accepts the OAuth code pasted directly into the terminal when the browser callback can't reach localhost (WSL2, SSH tunnels, devcontainers)
- **Situations**: authenticating Claude Code inside a remote SSH session without a localhost redirect, logging in from WSL2 or a devcontainer, setting up Claude Code in CI/CD environments that lack browser access
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## `claude project purge` Command — 2026-05-01
- **What**: New `claude project purge [path]` command deletes all Claude Code state for a project (transcripts, tasks, file history, config entry); supports `--dry-run`, `-y/--yes`, `-i/--interactive`, and `--all` flags
- **Situations**: cleaning up stale Claude Code state after migrating or archiving a repo, bulk-removing old projects from Claude Code's registry with `--all`, dry-running a purge to preview what will be deleted before committing
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## 1M Context Window Beta Retired for Sonnet 4 / Sonnet 4.5 — 2026-04-30
- **What**: The `context-1m-2025-08-07` beta header no longer extends context for Claude Sonnet 4.5 and Sonnet 4; requests over 200k tokens now return an error unless migrated to Sonnet 4.6 or Opus 4.6 (where 1M context is GA)
- **Situations**: auditing integrations still using the beta header on Sonnet 4 or Sonnet 4.5 before requests start erroring, migrating large-document pipelines to Sonnet 4.6 or Opus 4.6, planning cutover timing for long-context workflows
- **Tags**: [dev]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## PR URL in `/resume` Search — 2026-04-28
- **What**: Pasting a PR URL into the `/resume` search box finds the Claude Code session that originally created that PR (supports GitHub, GitHub Enterprise, GitLab, and Bitbucket)
- **Situations**: resuming a coding session from a PR link shared in Slack or a code review, reconnecting to the session behind a PR without scrolling through session history, quickly picking up paused PR work from any team member's link
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## `ANTHROPIC_BEDROCK_SERVICE_TIER` Env Var — 2026-04-28
- **What**: New Claude Code env var to select an AWS Bedrock service tier (`default`, `flex`, or `priority`), sent as the `X-Amzn-Bedrock-Service-Tier` header on every request
- **Situations**: directing high-priority production workloads to Bedrock reserved capacity, running non-critical batch jobs on the lower-cost flex tier, fine-tuning cost/performance trade-offs across separate Bedrock deployments
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Rate Limits API — 2026-04-24
- **What**: New API endpoints let administrators programmatically query the rate limits configured for their organization and individual workspaces
- **Situations**: building dashboards to monitor API capacity headroom before large batch runs, auto-scaling pipelines that check workspace limits before dispatching jobs, auditing rate limit configurations across multiple workspaces
- **Tags**: [dev, analytics]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Memory for Claude Managed Agents (Public Beta) — 2026-04-23
- **What**: Persistent memory layer for Managed Agents now in public beta; agents learn from every session with an intelligence-optimized memory store that developers can inspect, manage, and export via the API
- **Situations**: building agents that remember user preferences across sessions, enterprise agents that accumulate domain knowledge over time, production agents that improve through repeated use
- **Tags**: [dev, automation]
- **Source**: https://claude.com/blog/claude-managed-agents-memory

## Claude Code MCP Tool Hooks (`type: "mcp_tool"`) — 2026-04-23
- **What**: Hooks can now directly invoke MCP tools by setting `type: "mcp_tool"` instead of a shell command, eliminating shell-glue wrappers for MCP-backed automation
- **Situations**: sending Slack notifications via an MCP server on PostToolUse events, chaining MCP actions into Claude Code hook pipelines without shell wrappers, triggering multi-tool workflows from Claude Code events
- **Tags**: [dev, automation]
- **Source**: https://github.com/anthropics/claude-code/releases

## Claude Code Vim Visual Mode & Custom Themes — 2026-04-23
- **What**: Vim visual mode (`v`) and visual-line mode (`V`) added to the editor; new `/theme` command for creating and managing custom color themes in Claude Code (v2.1.118)
- **Situations**: Vim-workflow developers needing character/line selection in Claude Code's editor, customizing Claude Code's appearance for personal or team preferences, creating branded terminal environments for demos
- **Tags**: [dev]
- **Source**: https://github.com/anthropics/claude-code/releases

## Claude Code `--from-pr` Multi-Platform Support — 2026-04-23
- **What**: `--from-pr` flag now accepts GitLab merge-request, Bitbucket pull-request, and GitHub Enterprise PR URLs in addition to GitHub.com (v2.1.119)
- **Situations**: GitLab teams reviewing MRs directly in Claude Code, Bitbucket-based projects using Claude Code's PR analysis workflow, enterprises on GitHub Enterprise Server accessing `--from-pr` for the first time
- **Tags**: [dev]
- **Source**: https://github.com/anthropics/claude-code/releases

## Claude Design — 2026-04-17
- **What**: Research preview powered by Opus 4.7 that reads your codebase and design files to generate a reusable design system (colors, typography, components) applied consistently across future projects
- **Situations**: maintaining visual brand consistency across a growing product, auto-generating UI components from existing design tokens, bootstrapping a design system from a legacy codebase
- **Tags**: [product, dev]
- **Source**: https://9to5mac.com/2026/04/17/anthropic-launches-claude-design-for-mac-following-opus-4-7-model-upgrade/

## Claude Code Permission Security Hardening — 2026-04-17
- **What**: Bash deny rules now match commands wrapped in `env`/`sudo`/`watch`/`ionice`/`setsid`; `Bash(find:*)` allowlists no longer auto-approve `find -exec`/`-delete`; macOS `/private/{etc,var,tmp,home}` paths flagged as dangerous removal targets
- **Situations**: preventing exec-wrapper tricks from bypassing Claude Code deny rules, securing find-based allowlists that previously allowed destructive `-exec` flags, hardening shared or automated Claude Code deployments
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Code `sandbox.network.deniedDomains` — 2026-04-17
- **What**: New Claude Code setting to explicitly block specific domains even when a broader `allowedDomains` wildcard would otherwise permit them
- **Situations**: blocking high-risk endpoints while keeping broad internet access in sandboxed sessions, enterprise deployments with outbound domain restrictions, fine-grained per-project network control
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Code `/ultrareview` Command — 2026-04-16
- **What**: Cloud-based parallel multi-agent code review; run `/ultrareview` on the current branch or `/ultrareview <PR#>` to fetch and review any GitHub PR
- **Situations**: getting comprehensive pre-merge review without switching to an external tool, reviewing a GitHub PR from directly inside Claude Code, surfacing security or logic issues across large changesets
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Code `xhigh` Effort Level & Interactive `/effort` Slider — 2026-04-16
- **What**: New `xhigh` effort tier for Opus 4.7 sitting between `high` and `max`; `/effort` with no arguments now opens an interactive arrow-key slider to set the level
- **Situations**: dialing Opus 4.7 intelligence vs. speed without paying full `max` compute, quickly adjusting effort mid-session via keyboard, performance-tuning long agentic runs
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Code PowerShell Tool — 2026-04-16
- **What**: Native PowerShell tool now rolling out on Windows (opt in/out via `CLAUDE_CODE_USE_POWERSHELL_TOOL`); also available on Linux/macOS with `pwsh` on PATH
- **Situations**: running PowerShell scripts natively in Claude Code on Windows, Windows-native shell automation without WSL, cross-platform PowerShell workflows
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude in Amazon Bedrock — Generally Available — 2026-04-16
- **What**: Claude via the Messages API (`/anthropic/v1/messages`) is now open to all Amazon Bedrock customers; Opus 4.7 and Haiku 4.5 available self-serve via the Bedrock console across 27 AWS regions
- **Situations**: AWS teams adopting Claude without special account approval, deploying Opus 4.7 or Haiku 4.5 directly from the Bedrock console, enterprise workloads requiring regional AWS endpoints
- **Tags**: [dev, product]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Claude Opus 4.7 — 2026-04-16
- **What**: Most capable generally available Claude model for complex reasoning and agentic coding at the same $5/$25 per MTok pricing as Opus 4.6; includes updated tokenizer and API breaking changes vs 4.6
- **Situations**: long-horizon agentic coding requiring the highest available intelligence, production workloads needing frontier reasoning at Opus 4.6 price, migrating from Opus 4.6 (review breaking changes before upgrading)
- **Tags**: [dev, product]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## Claude Code Routines — 2026-04-14
- **What**: Cloud-based scheduled automations (cron or event-triggered) that run on Claude Code's web infrastructure even when your local machine is offline
- **Situations**: scheduling nightly dependency audits or test runs, triggering repo-wide tasks on a schedule without a laptop staying awake, packaging and reusing automations across repos via connectors
- **Tags**: [automation, dev]
- **Source**: https://code.claude.com/docs/en/routines

## Claude Code Parallel Sessions & Desktop Redesign — 2026-04-14
- **What**: Run multiple Claude Code sessions side-by-side from one window with a new sidebar manager, plus an integrated terminal, file editor, HTML/PDF preview, and drag-and-drop layout
- **Situations**: managing separate agent tasks on parallel feature branches simultaneously, monitoring a deploy in one pane while editing code in another, comparing two Claude conversations side by side
- **Tags**: [dev, automation]
- **Source**: https://siliconangle.com/2026/04/14/anthropics-claude-code-gets-automated-routines-desktop-makeover/

## Claude Code Session Recap (`/recap`) — 2026-04-14
- **What**: Automatically generates an AI context summary when returning to a session after being away; manually invocable with `/recap`, configurable in `/config`
- **Situations**: resuming a complex debugging session the next morning, handing off context to a colleague, re-orienting after a long interruption mid-task
- **Tags**: [dev]
- **Source**: https://code.claude.com/docs/en/changelog

## `ENABLE_PROMPT_CACHING_1H` Env Var — 2026-04-14
- **What**: New Claude Code env var to opt into the 1-hour prompt cache TTL (replacing the 5-minute default) across API key, Bedrock, Vertex, and Foundry; `FORCE_PROMPT_CACHING_5M` forces 5-minute TTL
- **Situations**: long agent sessions where re-reads of the same large system prompt should hit cache for an hour, Bedrock/Vertex setups that previously required separate config for extended TTL, cutting costs on repeated calls within a work session
- **Tags**: [dev, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Sonnet 4 & Opus 4 Deprecation — 2026-04-14
- **What**: `claude-sonnet-4-20250514` and `claude-opus-4-20250514` are deprecated with retirement on the Claude API scheduled for June 15, 2026; recommended migration targets are Sonnet 4.6 and Opus 4.6
- **Situations**: auditing codebases for hardcoded deprecated model IDs before the June deadline, planning staged rollouts to 4.6 models, updating CI/CD pipelines that pin model strings
- **Tags**: [dev]
- **Source**: https://platform.claude.com/docs/en/release-notes/overview

## PreCompact Hook — 2026-04-13
- **What**: New Claude Code hook that fires before context compaction; hooks can block compaction by exiting with code 2 or returning `{"decision":"block"}`
- **Situations**: preserving full conversation context during critical long-running agent tasks, implementing custom compaction logic instead of the default, preventing mid-task summarisation that could drop important tool results
- **Tags**: [automation, dev]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude for Word Beta — 2026-04-10
- **What**: Native sidebar add-in for Microsoft Word with AI-assisted editing, clickable citations, and Track Changes integration
- **Situations**: reviewing legal contracts in-document, drafting financial memos with inline AI edits, accepting/rejecting AI revisions one-by-one
- **Tags**: [product, automation]
- **Source**: https://www.thurrott.com/a-i/334834/anthropic-launches-claude-for-word-in-beta

## Claude Code /team-onboarding Command — 2026-04-10
- **What**: New `/team-onboarding` slash command that auto-generates a teammate ramp-up guide from your local Claude Code usage patterns
- **Situations**: onboarding new engineers to an unfamiliar codebase, capturing team conventions for new hires, documenting Claude Code workflows
- **Tags**: [dev, product]
- **Source**: https://code.claude.com/docs/en/changelog

## Advisor Tool (API public beta) — 2026-04-09
- **What**: Pairs a fast executor model (Sonnet 4.6 / Haiku 4.5) with Opus 4.6 as a high-intelligence mid-generation advisor for strategic guidance
- **Situations**: running complex long-horizon agents at executor cost, getting near-Opus quality without full Opus token spend, agentic pipelines where most steps are routine but some require deep reasoning
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/agents-and-tools/tool-use/advisor-tool

## Claude Code Monitor Tool — 2026-04-09
- **What**: New Monitor tool in Claude Code for streaming real-time events from background scripts
- **Situations**: watching a background build or test run, monitoring deploys without blocking Claude's session, streaming events from long-running scripts
- **Tags**: [dev, analytics, automation]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Managed Agents (API public beta) — 2026-04-08
- **What**: Fully managed agent harness: runs Claude autonomously with secure sandboxing, built-in tools, checkpointing, credential management, and SSE streaming
- **Situations**: deploying autonomous agents without building infrastructure, running long-horizon agentic workflows with scoped permissions and tracing, production agents with secure code execution
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/managed-agents/overview

## ant CLI — 2026-04-08
- **What**: Official command-line client for the Claude API with native Claude Code integration and YAML-based API resource versioning
- **Situations**: scripting Claude API calls from the terminal, versioning prompts and API configs in YAML, integrating Claude into CI/CD pipelines
- **Tags**: [dev, automation]
- **Source**: https://platform.claude.com/docs/en/api/sdks/cli

## Claude Code Focus View — 2026-04-08
- **What**: Focus view toggle (`Ctrl+O`) in NO_FLICKER mode that shows only prompt, one-line tool summary with diffstats, and Claude's final response
- **Situations**: reducing terminal noise during long agentic runs, presenting Claude's work without raw tool output, working in narrow or shared terminals
- **Tags**: [dev, product]
- **Source**: https://code.claude.com/docs/en/changelog

## Claude Mythos Preview — 2026-04-07
- **What**: Specialized Claude model with strong general capabilities and particular depth in computer security tasks, available as invitation-only gated research preview via Project Glasswing
- **Situations**: defensive cybersecurity analysis, identifying vulnerabilities in critical software, security research requiring advanced reasoning
- **Tags**: [research, dev]
- **Source**: https://anthropic.com/glasswing

## Messages API on Amazon Bedrock (research preview) — 2026-04-07
- **What**: First-party Claude API endpoint (`/anthropic/v1/messages`) on AWS-managed infrastructure in us-east-1, same request shape as the direct Claude API with zero operator access
- **Situations**: AWS-native Claude deployments with the same SDK/API shape, regulated industries requiring data residency on AWS, migrating from first-party API to Bedrock without code changes
- **Tags**: [dev, product]
- **Source**: https://platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock-research-preview

## Claude Code Default Effort Changed to High — 2026-04-07
- **What**: Default effort level raised from medium to high for API-key, Bedrock/Vertex/Foundry, Team, and Enterprise Claude Code users (adjustable with `/effort`)
- **Situations**: getting more thorough responses by default, agentic tasks requiring deeper reasoning without manually setting effort, users who previously relied on the medium default
- **Tags**: [dev, product]
- **Source**: https://code.claude.com/docs/en/changelog
